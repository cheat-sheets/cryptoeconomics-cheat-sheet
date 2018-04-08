# Cryptoeconomics Cheat Sheet

**Cryptoeconomics**  - generalized field that deals with large class of systems that try to use both 
cryptographic tools and economic incentives defined in the system in order to achieve information security goals 
of that system. (Vitalik Buterin)
 - cryptography can prove properties about messages that happened in the past.
 - economic incentives can encourage desired properties to hold into the future.

**Cryptoeconomics** (alternative definition) - the application of incentive mechanism design to information 
 security problems (Vlad Zamfir).

### Table of Content

- [Related Fields](#related-fields)
  - [Cryptography](#cryptography)
  - [Economy](#economy)
  - [Game Theory / Mechanism Design](#game-theory--mechanism-design)
  - [Distributed Systems](#distributed-systems)
- [Concepts](#concepts)
- [Security Models](#security-models)
- [Cryptoeconomic Systems](#cryptoeconomic-systems)
  - Consensus algorithms
  - Outsources computation and storage
  - [Random number generation](#random-number-generation)
  - Providing true information about the world (oracles)
  - Governance (DAOs)
  - Stable-value cryptocurrencies
  - Bounties to solutions to math or CS problems
  - Telling the time
- [Resources](#resources)

---

### Related Fields

#### Cryptography

- Hashes
- Signatures
- ZKPs
- PoW
- Erasure Codes
- Timelock crypto / sequential PoW
- Homomorphic encryption / obfuscation

#### Economy

Incentives: 

- rewards/penalties
- privileges

#### Game Theory / Mechanism Design

- [VCG](#https://github.com/medvedev1088/game-theory-cheat-sheet#vcg)
  - susceptible to collusion, hard to apply in cryptoeconomics
- [Coalitional Games](https://github.com/medvedev1088/game-theory-cheat-sheet#coalitional-games)

#### Distributed Systems

- Byzantine Fault Tolerance (BFT)

---

### Concepts

**Cryptoeconomic resource** - a resource, possession of which gives agents the right to collectively perform state transitions 
in the cryptoeconomic system. E.g. hashing power, stake, tokens.

**Cryptoeconomic set** - all agents possessing the cryptoeconomic resource.

**Cryptoeconomic Security Margin** - a fraction of cryptoeconomic resource X such that you can prove "either a given 
guarantee G is satisfied or those at fault for violating G are poorer than they otherwise would have been by at least X 
fraction of the cryptoeconomic resource". E.g. security margin of 0.5 means that it costs the attacker half of all 
hashing power to violate the guarantee G.

**Cryptoeconomic proof** - a message signed by an actor that can be interpreted as "I certify that either P is true,
or I suffer an economic loss of size X".

---

### Security Models

Security models are different in the assumptions that they make about the real world. It's not clear what assumptions
are more realistic, nevertheless it's useful to perform analysis in different models to have the clearer picture about
the security of a system.

Different security models give different security margins.

- **Honest Majority** - assumes that up to X (usually a number less that 1/2) of agents are controlled by an attacker, 
and the remaining agents honestly follow the protocol.
  - **Tranditional Fault Tolerance** - assumes almost all agents are honest (X is close to 0).
  - **Bysantine Fault Tolerance** - assumes up to 1/3 of agents are controlled by an attacker.

- **Uncoordinated Majority** - assumes that up to X (often between 1/4 and 1/2) of agents are capable of coordinating 
their actions, all agents are rational in a game-theoretic sense.
  - model parameter - level of coordination X.

- **Coordinated Majority** - assumes that all agents are controlled by the same actor, or are fully capable of coordinating 
on the economically optimal choice between themselves. We can talk about the cost to the coalition 
(or profit to the coalition) of achieving some undesirable outcome.
  - model parameter - level of coordination X (close to 1).

- **Bribing Attacker** - takes the uncoordinated majority model, but instead of making the attacker be one of the participants, 
the attacker sits outside the protocol, and has the ability to bribe any participants to change their behavior. 
Attackers are modeled as having a budget, which is the maximum that they are willing to pay, and we can talk about 
their cost, the amount that they end up paying to disrupt the protocol equilibrium.
  - model parameter - attacker's budget B.
 
---

**[Bitcoin with selfish mining fix](https://arxiv.org/abs/1311.0243)** analysis:

| Model | Parameters | Security Margin |
| ---  | --- | --- |
| Honest Majority |  | ~0.5 (51% attack) | 
| Uncoordinated Majority | Level of coordination ~0.5 | ~0.25 (selfish mining attack)* |
| Coordinated Majority | Level of coordination ~1 | 0 |
| Bribing Attacker | Budget > 13.2 * number_of_blocks | ~0 |

<nowiki>*</nowiki> Without the selfish mining fix the security margin in uncoordinated majority model is epsilon 
(slightly greater than 0).
 
**[Shelling coin](https://blog.ethereum.org/2015/01/28/p-epsilon-attack/)** analysis:

| Model | Parameters | Security Margin |
| ---  | --- | --- |
| Honest Majority |  | 0.5 (51% attack) | 
| Uncoordinated Majority | Level of coordination ~0.5 | ~0.25 ** |
| Coordinated Majority | Level of coordination ~1 | 0 |
| Bribing Attacker | Budget > 0.5 | ~0 |

** The attacker only needs to possess half of the coordinated part of the economic set. 
The other half has an incentive to vote with the attacker. 

---

### Cryptoeconomic Systems

#### Random Number Generation

A number of protocols, including consensus protocols, blockchain-based lotteries, scalable sampling schemes, etc, 
require some kind of random number generation in the protocol. There are a number of alternatives with their 
pros and cons:

- PoW - use block hash
- N-of-N commit-reveal ([RANDAO](https://github.com/randao/randao))
- Oracles
- Timelock crypto
 


---

### Resources

- Videos
  - Introduction to Cryptoeconomics - Vitalik Buterin https://www.youtube.com/watch?v=pKqdjaH1dRo
  - Hard problems in Cryptoeconomics - Vitalik Buterin https://www.youtube.com/watch?v=p5qwbOkCZSc
  - Cryptoeconomic Protocols In the Context of Wider Society - Vitalik Buterin https://www.youtube.com/watch?v=S47iWiKKvLA
  - Programmable Incentives: Intro to Cryptoeconomics - Karl Floersch https://www.youtube.com/watch?v=-alrVUv6E24
  - The Current State of Cryptoeconomics - Vlad Zamfir https://www.youtube.com/watch?v=u6VSPD5TrP4
- Security Models Explained in Sharding FAQ https://github.com/ethereum/wiki/wiki/Sharding-FAQ#what-are-the-security-models-that-we-are-operating-under
- Hard Problems of Cryptoeconomics https://github.com/ethereum/wiki/wiki/Problems
- Hard Problems of Cryptocurrency 2015 https://github.com/ethereum/wiki/wiki/HPOC_2015
- A Crash Course in Mechanism Design for Cryptoeconomic Applications https://medium.com/blockchannel/a-crash-course-in-mechanism-design-for-cryptoeconomic-applications-a9f06ab6a976
- Cryptoeconomics gitbook https://dapp-studies.gitbooks.io/cryptoeconomics/content/
- Game Theory Cheat Sheet https://github.com/medvedev1088/game-theory-cheat-sheet
- What is Cryptoeconomics? The Ultimate Beginners Guide https://blockgeeks.com/guides/what-is-cryptoeconomics/
- Making Sense of Cryptoeconomics, Josh Stark https://medium.com/l4-media/making-sense-of-cryptoeconomics-c6455776669
- Cryptoeconomics https://blockchainhub.net/cryptoeconomics/

