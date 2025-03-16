+++
title = "Blockchain Architecture First Principles #2 — 𝗔 𝗕𝗹𝗼𝗰𝗸𝗰𝗵𝗮𝗶𝗻 𝗜𝘀 𝗧𝗵𝗲 𝗪𝗼𝗿𝘀𝘁 𝗣𝗹𝗮𝗰𝗲 𝗧𝗼 𝗦𝘁𝗼𝗿𝗲 𝗗𝗮𝘁𝗮"
date = 2025-03-16
draft = false
+++

![swamp](swamp.jpg)

### 💭 Explanation
A blockchain is more than a database. It’s a **consensus engine**.  
That doesn’t necessarily make it better — it comes with a burden. It’s slower, more expensive, replicated, and permanent by design.  
**We should avoid putting data on-chain unless all other options are exhausted.**

On-chain data is broadcast, stored forever, and visible to anyone with access.  
It’s like tattooing your application state and sending copies to every node in the world.

You might think: “Just encrypt it or hash it.” But that’s a common fallacy:
- **A hash is worthless once its pre-image leaks.**
- **Encryption fails the moment its key is exposed.**  
These aren’t shields. They’re veils. Privacy doesn’t live in one-to-one projections. It lives in what cannot be reconstructed.

Even cryptography ages. **#Quantum computing** may break today’s assumptions sooner than expected.

All the more reason to minimize what you expose — and assume anything stored forever may one day become readable.  
Don’t get enthusiastic about what can be stored. Be wary of which burden and responsibility you’re willing to carry. Nothing is impossible — but **think well if it’s worth deviating from the river to pass through the swamp.**

### 🥷 How to Apply

- **Default to off-chain, unless on-chain is essential for logic.**  
- **If the data is required for smart contract execution and not sensitive, storing it on-chain is practical** — especially when the chain is purpose-built, like in a limited consortium (e.g., Hyperledger Fabric), where replication and access are controlled.  
- **If it’s sensitive, never expose a direct mapping of the data — not even a hash.** Use commitments, signatures, or zero-knowledge proofs instead.  
- **Zero-Knowledge Proofs (ZKPs) offer elegant solutions** — enabling you to prove facts without revealing the underlying data. But they’re also complex and unforgiving in their implementation. A small misstep can compromise the very privacy they’re meant to protect.  
- **Design for privacy by default.** Assume anything published forever could one day become readable.  


---

_Every Sunday, I’ll propose a blockchain first principle for architects. Not fixed rules, but emerging truths — meant to be ruthlessly challenged, like a scientific hypothesis. If a principle can’t stand up to questioning, I’ll refine or toss it._


🌐 **Also shared on [LinkedIn](https://www.linkedin.com/posts/shanedeconinck_quantum-blockchain-trust-activity-7307029996793921536-Tas1?utm_source=share&utm_medium=member_desktop&rcm=ACoAAAjP1-wB57TFLEnLFVsyAeHsFKYt-Xs0KyQ)**


**Photo by [R. Skrypnyk](https://www.pexels.com/@r-skrypnyk) — Pexels**