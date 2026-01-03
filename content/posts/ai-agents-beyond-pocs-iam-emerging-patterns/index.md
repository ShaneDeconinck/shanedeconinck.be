+++
title = "AI Agents Beyond POCs: IAM Emerging Patterns Worth Watching"
date = 2026-01-03
draft = false
+++

---
title: "AI Agent Governance: The Enterprise Challenge Beyond Getting AI to Work"
date: 2026-01-03
draft: false
---

As software developers, we have a front-row seat to AI's transformative potential. [84% of developers now use or plan to use AI tools](https://www.index.dev/blog/developer-productivity-statistics-with-ai-tools), with tools like Claude Code already delivering ROI by reasoning through complex tasks autonomously. Getting them to work well is challenging enough. But scaling them across the enterprise with proper governance? That's a whole different level of complexity.

[Nearly 60% of AI leaders cite risk and compliance concerns](https://www.deloitte.com/us/en/what-we-do/capabilities/applied-artificial-intelligence/blogs/pulse-check-series-latest-ai-developments/ai-adoption-challenges-ai-trends.html) as their primary adoption barrier. The challenge? Traditional IAM wasn't built for systems that create intent rather than just forward it.

## The Governance Gap

When agents autonomously decide which APIs to call and spawn sub-agents to handle tasks, fundamental questions arise:

- Who is accountable when an agent makes a consequential decision?
- How do we audit chains of delegation across multiple agents?
- What prevents authority creep as agents scale?

Today's enterprise struggles are just the beginning. As agents become more autonomous and operate across organizational boundaries, these challenges compound.

## 3 Key Patterns Emerging

### 1. Agentic On-Behalf-Of (OBO)

Dual-identity tokens (RFC 8693) that identify both human and agent, making every decision traceable.

### 2. Proof of Continuity

Rather than asking "who holds this authority?" at each step, asking "can this authority validly continue?" This enables delegation chains without central trust anchors—critical for cross-organizational agent workflows.

### 3. Trust-Spanning Frameworks

Decentralized credentials (DIDs/VCs) for establishing identity across organizational boundaries. DIF and ToIP working groups are developing protocols specifically for AI agent delegation and trust chains.

## Resources I'm Finding Helpful

- [Christian Posta on why there may never be a single standard for AI agent auth](https://www.linkedin.com/posts/ceposta_there-is-no-standard-today-for-%F0%9D%90%80%F0%9D%90%88-%F0%9D%90%80-activity-7413006276974211072-Dd7i/)
- [Nicola Gallo on Proof of Continuity and why decentralized identity needs to solve authority](https://www.linkedin.com/posts/nicolagallo83_why-isnt-decentralized-identity-mainstream-activity-7412533797629599745-rwrw/)
- [Tobin South's OpenID Foundation whitepaper on identity management for agentic AI](https://openid.net/wp-content/uploads/2025/10/Identity-Management-for-Agentic-AI.pdf)
- [Andor Kesselman - Scaling the Agentic Web: New Challenges and Areas of Innovation](https://www.youtube.com/watch?v=SJ8rFKJ8NHw&t=2250s)

[Slidedeck generated bij NotebookLM](slidedeck.pdf)

---

*I'm sharing as I'm learning. Let me know if I got anything wrong, and I hope this is valuable to you.*