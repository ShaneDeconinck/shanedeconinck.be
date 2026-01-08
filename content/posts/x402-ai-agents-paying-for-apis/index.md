+++
title = "When Agents Pay for APIs: Getting Hands-On with x402 and EIP-3009"
date = 2026-01-07
draft = false
+++

**HTTP 402 "Payment Required"** has existed since 1997. It was reserved for "future use" because there was no digital payment system that worked at the protocol level. Now we're starting to see practical implementations.

With AI agents talking to APIs and other agents, machine-to-machine payments are becoming essential. Agent-to-API is the most likely first use case for production deployment, and it's a big opportunity for companies—whether they're getting scraped or want to pass on capabilities without building AI products themselves.

Current API billing (signups, credit cards, invoice emails) wasn't built for autonomous agents. We need payment primitives that work without human intervention.

## Enter x402

[x402](https://www.x402.org/) is an open payment protocol that **Coinbase and Cloudflare** are standardizing through the [x402 Foundation](https://www.cloudflare.com/press/press-releases/2025/cloudflare-and-coinbase-will-launch-x402-foundation/). It finally puts HTTP 402 to work.

**What x402 solves:**
- **No accounts needed** - Pay per request, no signup
- **Machine-readable** - Agents parse payment instructions automatically
- **Instant settlement** - On-chain confirmation, no invoicing delays
- **Cryptographic proof** - On-chain transaction hash proves payment, no disputes

The protocol supports multiple networks and payment methods. It has already processed [over 100M payments](https://www.x402.org/writing/x402-v2-launch) across APIs and AI agents.

I wanted to understand how it works, so I built a demo.

## The Demo

{{< youtube wNHUrroN_Hk >}}

I built a proof of concept: a San Francisco real estate API with two pricing tiers.

| Tier | Endpoint | Price | What You Get |
|------|----------|-------|--------------|
| 1 | `/api/v1/listings` | $0.01 | Property listings by neighborhood |
| 2 | `/api/v1/valuation` | $0.10 | AI-powered property valuation |

An AI agent queries the API, gets a 402 response with payment instructions, signs an authorization, and the server settles it on-chain. No human in the loop.

## How x402 Works on EVM (with EIP-3009)

The implementation uses **EIP-3009 TransferWithAuthorization** - a standard supported by USDC that enables gasless payments. The agent signs an authorization, and the server settles it on-chain.

### Step 1: Agent requests data

```
GET /api/v1/listings?neighborhood=Mission
```

### Step 2: Server responds 402

```json
{
  "x402Version": 1,
  "accepts": [{
    "scheme": "exact",
    "network": "base-sepolia",
    "maxAmountRequired": "10000",
    "payTo": "0x9c71...7056",
    "asset": "0x036C...Cf7e"
  }]
}
```

The server tells the agent exactly what to pay, where, and on which network.

### Step 3: Agent signs authorization (GASLESS)

```python
# Agent signs EIP-712 TransferWithAuthorization (no gas!)
nonce = secrets.token_bytes(32)  # Random 32-byte nonce
message = {
    "from": agent_address,
    "to": recipient,
    "value": amount,
    "validAfter": now,
    "validBefore": now + 300,  # 5 min validity
    "nonce": nonce
}
signature = account.sign_message(encode_typed_data(message))
```

The agent doesn't send a transaction - it just signs. No ETH needed for gas.

### Step 4: Agent retries with X-PAYMENT header

```
GET /api/v1/listings?neighborhood=Mission
X-PAYMENT: <base64-encoded signature + authorization>
```

### Step 5: Server settles and responds

```python
# Server calls transferWithAuthorization (pays gas)
usdc.transferWithAuthorization(
    from_addr, to_addr, value,
    validAfter, validBefore, nonce,
    v, r, s  # signature components
)
```

The USDC contract verifies the signature, checks the nonce hasn't been used (replay protection), and transfers USDC. The server pays gas, agent pays nothing.

## The Architecture

```
┌─────────────────────┐
│   AI Agent          │
│   (Claude + Wallet) │
│   Signs EIP-712     │
│   (no gas needed!)  │
└──────────┬──────────┘
           │
           │ 1. GET /listings
           │ 2. ← 402 + payment instructions
           │ 3. Sign authorization (gasless)
           │ 4. GET /listings + X-PAYMENT
           ▼
┌─────────────────────┐
│   API Server        │
│   (FastAPI + x402)  │
├─────────────────────┤
│ 5. Verify signature │
│ 6. Call USDC        │
│    transferWith-    │
│    Authorization    │
│ 7. Return data      │
└─────────────────────┘
```

**Key insight:** The agent only needs to sign - no ETH required. The server handles settlement and pays gas. This removes a major friction point for agent deployments.

## The Economics

With EIP-3009, the server pays gas to settle payments. The agent only signs.

x402 is chain-agnostic and can work on non-EVM chains too—the standard is still evolving. Here are two EVM examples (at time of writing):

**Base L2 (this demo):**
| Query Price | Gas Cost (~$0.002) | Server Overhead | Agent Gas |
|-------------|-------------------|-----------------|-----------|
| $0.01 | $0.002 | 20% | $0 |
| $0.10 | $0.002 | 2% | $0 |
| $1.00 | $0.002 | 0.2% | $0 |

**Ethereum Mainnet:**
| Query Price | Gas Cost (~$15) | Server Overhead | Agent Gas |
|-------------|-----------------|-----------------|-----------|
| $0.01 | $15 | 150,000% | $0 |
| $0.10 | $15 | 15,000% | $0 |
| $1.00 | $15 | 1,500% | $0 |

On Base, micro-payments work well. On mainnet, you'd need much higher-value queries or batching to make the economics viable.

## What This Enables

### For Data Owners (Incumbents)

Real estate companies, financial data providers, healthcare systems—they have valuable data but don't want to become AI companies.

x402 lets them monetize data access without building AI products. Expose an API, set a price, collect USDC.

### For AI Companies

They need data but can't acquire everything. x402 gives agents a way to pay for data programmatically, at scale, without business development deals for every data source.

### For Users

Agents that can access more services, autonomously, without manual API key setup for each integration.

## Limitations

**Payment without delivery** - If payment settles but API fails, money is lost. Needs refund mechanisms or escrow patterns.

**Discovery** - How do agents find services? This demo hardcodes URLs. Production needs service registries (an active area of development).

**Custody** - Agent holds private keys. Key compromise = funds lost. (Though with EIP-3009, agent only needs signing key, no ETH.)

## Try It

**Code:** [GitHub](https://github.com/ShaneDeconinck/x402-agent-to-api-demo)

**Tech stack:**
- FastAPI (Python)
- Web3.py + USDC on Base Sepolia
- Anthropic SDK (Claude)
- Tailwind CSS frontend

## What I Learned Building This

Getting hands-on with x402 taught me more than reading the docs ever could:

- **Server-side settlement makes sense** - Shifts gas costs to the party that can price for it (the API provider).
- **Infrastructure is ready** - Base L2, USDC with EIP-3009, eth_account for signing—the pieces exist today.
- **The hard problems are elsewhere** - Discovery, custody, and delivery guarantees need more work than the payment flow itself.

If you're curious about agent-to-API payments, I'd recommend building something small yourself. The [x402 docs](https://docs.cdp.coinbase.com/x402/welcome) and [GitHub](https://github.com/coinbase/x402) are good starting points.

---

*I'm sharing as I'm learning. Let me know if I got anything wrong, and I hope this is valuable to you.*
