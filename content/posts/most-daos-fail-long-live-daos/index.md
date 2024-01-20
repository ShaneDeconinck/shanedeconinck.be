+++
title = 'Most DAOs fail. Long live DAOs!'
date = 2024-01-20T21:44:00+01:00
draft = false
+++
![Image alt](main.png)

## Smart Contracts

The idea of smart contracts was conceived in the late '90s by Nick Szabo, a computer scientist, legal scholar, and cryptographer. In  1996  he published the article  [Smart Contracts: Building Blocks for Digital Free Markets](https://www.semanticscholar.org/paper/Smart-Contracts%3A-Building-Blocks-for-Digital-Szabo/9b6cd3fe0bf5455dd44ea31422d015b003b5568f)  [1] and in  1997  the article  [The Idea of Smart Contracts](https://web.archive.org/web/20140406003401/szabo.best.vwh.net/idea.html)  [2].

Szabo explored the potential of using  cryptographic  techniques  to bring about  self-executing contracts  and  decentralized mechanisms  for enforcing contractual clauses. His vision was to embed contractual agreements into the programming of digital systems, thereby reducing the need for traditional legal enforcement mechanisms and intermediaries. However, the technology wasn't yet available to implement the idea.

## Bitcoin, the first decentralized network

More than a decade later, in  2008,  [Bitcoin's whitepaper](https://bitcoin.org/bitcoin.pdf)  emerged. Providing the architecture for the first truly decentralized digital network. However, even that wasn't enough yet to allow smart contracts to be crafted, as Bitcoin only allows for very limited Scripting.

## Ethereum, the first Turing-complete smart contracts

Vitalik Buterin, who was deeply involved in the Bitcoin ecosystem as a teenager, envisioned a new kind of blockchain network that could support more complex applications than Bitcoin, including smart contracts. This vision led to the creation of Ethereum.

In late  2013, Buterin published the Ethereum White Paper, which outlined the concept of a blockchain platform that would go beyond the financial use cases of Bitcoin. The Ethereum White Paper introduced the idea of a blockchain with a built-in Turing-complete programming language, enabling users to create any kind of application they could imagine, including smart contracts.

Following the White Paper, the technical details of Ethereum's implementation were further elaborated in the Ethereum Yellow Paper, authored by Gavin Wood in  2014. This paper provided the technical foundation and specifications for the Ethereum Virtual Machine (EVM), which is the runtime environment for smart contracts on the Ethereum network.

## The birth of DAOs

Right from the early stages of his blockchain endeavors, Vitalik Buterin had already coined the term  'Decentralized Autonomous Organization' (DAO), anticipating its significance in the realm of Ethereum and blockchain technology.

> I invented the term in 2013, and Daniel Larimer came up with DACs (s/organization/corporation) a few months before. Of course the concept of decentralized automatons is older; my DAO ideas were in part inspired by Daniel Suarez's Daemon. ---  [Vitalik Buterin](https://medium.com/@VitalikButerin/i-invented-the-term-in-2013-and-daniel-larimer-came-up-with-dacs-s-organization-corporation-a-ef86db1524d5)

In April 2016, the first prominent DAO, known simply as "The DAO," was launched, marking a significant moment in the evolution of decentralized autonomous organizations. This project, built on the Ethereum blockchain, aimed to operate as a pioneering venture capital fund for the decentralized space, driven by smart contracts and collective decision-making of its stakeholders.

The DAO rapidly gained notoriety, not only for its innovative approach to decentralized governance but also for the subsequent security breach that led to major losses and sparked widespread discussions about the security and viability of DAOs. This shows that the self-executing and decentralized nature of DAOs holds inherent risks, particularly in terms of security vulnerabilities and the potential for unintended consequences.

The DAO incident highlighted how flaws in smart contract code can be exploited, leading to significant financial losses and undermining trust in decentralized systems.

## After the TheDAO disaster, a lot of lessons were learned

Following the 2016 DAO incident, there has been a significant evolution in the world of Decentralized Autonomous Organizations. Recognizing the vulnerability exposed by the security breach, the blockchain community has ramped up its focus on ensuring robust security protocols for DAOs. This has involved implementing more stringent security audits, establishing bug bounty programs, and conducting in-depth code reviews, all aimed at safeguarding smart contracts against vulnerabilities.

Simultaneously, the legal landscape for DAOs has been in flux. The incident underscored the need for clear legal frameworks to govern these novel entities. As a result, there's been a push to integrate DAOs within existing legal structures, with some jurisdictions even considering recognizing DAOs as formal legal entities. This shift is significant as it influences how DAOs operate in terms of liability, governance, and regulatory compliance.

## Successful examples

-   [UniSwap (UNI)](https://uniswap.org/governance) : Uniswap stands out as one of the most successful DAOs, particularly in the decentralized finance (DeFi) space. It is not only a leading decentralized exchange (DEX) but also notable for its substantial treasury and active community participation. Uniswap DAO allows its members to vote on significant decisions using $UNI tokens, influencing the platform's governance, fees, and token listings.
-   [Friends With Benefits Pro (FWB)](https://wiki.fwb.help/GovernanceManual) : This exclusive DAO focuses on creating a social network for top Web 3.0 influencers. It emphasizes content creation and idea sharing, with membership requiring ownership of a certain amount of $FWB tokens. This DAO is also known for organizing high-profile events and offering educational resources in Web 3.0 and NFT spaces.
-   [Decentraland (MANA)](https://decentraland.org/governance/) : As a prominent player in the metaverse sector, Decentraland's DAO allows token holders to govern various aspects of this virtual world, including land auctions and content controls. The DAO's structure is complex, with different branches focusing on community voting, executive decisions, and security.
-   [ConstitutionDAO (PEOPLE)](https://www.constitutiondao.com/) : Although it was a short-lived project, ConstitutionDAO made a significant impact with its mission to purchase one of the surviving copies of the US Constitution. It demonstrated the power of collective fundraising and community-driven initiatives, even though it did not win the auction.
-   [MakerDAO](https://makerdao.com/en/governance) : Governing the DAI stablecoin, MakerDAO is a key player in the DeFi space. It allows MKR token holders to manage DAI's supply and liquidity and make crucial decisions regarding collateral and interest rates.
-   Howest's Decentralized Autonomous Hackathon : 
Since 2022, we at Howest have been pioneering the integration of blockchain technology into education with our annual Decentralized Autonomous Hackathon (DAH).
This event is a practical showcase of decentralized systems and blockchain technology, structured around ERC1155 standards and Role-Based Access Control. The hackathon presents a unique opportunity for participants to engage in a real-world application of DAO principles.Intrigued about the roles, phases, and the intricate workings of our DAH based on ERC1155? Stay tuned for a detailed post where I’ll delve into the specifics of its smart contract.

## Components of a DAO

A DAO can have wide ranging functionalities, and can be implemented in many different ways. Here are some common characteristics:

-   **Token-Based Membership**:  In a DAO, membership is often associated with holding specific tokens. These tokens can represent voting power, equity, or a stake in the DAO. The more tokens a member has, the more influence they might wield in the DAO's decision-making process.
-   **Proposal and Voting System, and Consensus Mechanism**:  DAOs operate on a system of proposals and voting to make decisions. Members can propose changes or actions, which are then voted on by the community. The consensus mechanism, which can vary from simple majority to more complex systems, is used to determine whether a proposal is accepted or rejected.
-   **Roles**:  Within a DAO, there can be various roles, including founders, developers, investors, and regular members. Each role may have different responsibilities and levels of involvement in the DAO's operations.
-   **Off-Chain Communication Channels**:  DAOs often use off-chain platforms like Discord, Telegram, or forums for communication and discussion among members. These channels facilitate discussions on proposals, strategies, and general community engagement.
-   **Treasury**:  A DAO's treasury is where its funds are stored and managed, often through smart contracts. The use of these funds is typically decided through the DAO's governance process, with members voting on how to allocate resources for projects, investments, or operational expenses.
-   **Legal Structure**:  Some DAOs choose to establish a formal legal structure to interface with traditional legal and financial systems. This can help in defining the DAO's legal standing, handling liabilities, and facilitating interactions outside the blockchain ecosystem.

## Best practices

-   **Start Small**:  Begin with manageable goals to facilitate learning and adaptation.
-   **Stand on the Shoulders of Giants**:  Learn from existing DAOs to build on successful strategies.
-   **Clear and Simple Governance**:  Implement straightforward governance to encourage participation.
-   **Robust Security Measures**:  Prioritize security with regular audits and updates.
-   **Effective Communication Channels**:  Use platforms like Discord for member engagement and transparency.
-   **Legal Compliance and Structure**:  Navigate the regulatory landscape with legal advice.
-   **Encourage Active Participation**:  Incentivize meaningful contributions from members.
-   **Iterative Development**:  Gradually introduce changes based on member feedback.
-   **Diversify and Decentralize**:  Aim for a diverse member base to enhance resilience.
-   **Regular Audits and Reviews**:  Continuously evaluate the DAO's operations and governance.

## User Experience (UX) as a Barrier

While the concept of DAOs holds immense promise, one significant barrier to their widespread adoption is the user experience (UX). Interacting with decentralized systems can be complex and daunting for the average user. The need to manage private keys, navigate blockchain interfaces, and understand the intricacies of smart contracts can be overwhelming.

However, it's important to note that the Web3 community recognizes this challenge and is actively working on solutions. Innovations like account abstraction are on the horizon, aiming to make UX more user-friendly. Account abstraction abstracts away many of the complexities of interacting with the blockchain, making it easier for users to engage with DAOs and other decentralized applications.

## Reflection

Reflecting on the nature of Decentralized Autonomous Organizations (DAOs), it's evident that establishing and managing a DAO is indeed more challenging than running a centralized organization. This complexity stems from the decentralized nature of DAOs, which requires a careful balancing of security, legal compliance, effective governance, and active community engagement.

Yet, at the same time, DAOs are groundbreaking. They represent a significant shift in how organizations can be structured and governed, moving away from traditional hierarchical models to a more democratic, participatory framework. This shift opens up new possibilities for collaboration, innovation, and collective decision-making.

However, the path to successfully implementing and managing a DAO is not straightforward. It requires time, patience, and a willingness to experiment and learn. Pioneering a DAO involves navigating uncharted waters, dealing with technological complexities, and often facing skepticism and regulatory challenges.

In this context, the phrase "those who say it can't be done shouldn't interrupt the people doing it" becomes particularly relevant. It speaks to the courage and determination required to venture into the relatively new and untested realm of DAOs. Those involved in DAOs are often at the forefront of exploring how decentralized technologies like blockchain can reshape organizational structures and governance models.

The journey of developing and sustaining a DAO is a testament to innovation and resilience in the face of challenges. It calls for bravery and a pioneering spirit, as the creators and members of DAOs are not just building organizations; they are, in many ways, shaping the future of how collective endeavors might be organized and managed in an increasingly digital and interconnected world.

> That said, I don't think calling "the DAO" a "slap in the face" is remotely appropriate despite its faults; it's much easier to conceptualize something and armchair-criticize others than it is to implement it yourself. ---  [Vitalik Buterin](https://medium.com/@VitalikButerin/i-invented-the-term-in-2013-and-daniel-larimer-came-up-with-dacs-s-organization-corporation-a-ef86db1524d5)