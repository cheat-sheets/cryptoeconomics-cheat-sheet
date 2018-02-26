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
- [Building Blocks](#building-blocks)
- [Concepts](#concepts)
- [Security Models](#security-models)
- [Examples of Cryptoeconomic Systems](#examples-of-cryptoeconomic-systems)
- [Resources](#resources)

---

### Building Blocks

**From cryptography**:

- Hashes
- Signatures
- ZKPs
- PoW
- Erasure Codes
- Timelock crypto / sequential PoW
- Homomorphic encryption / obfuscation

**From economy**:

Incentives: 

- rewards/penalties
- privileges

---

### Concepts

**Economic resource** - a resource possession of which gives agents the right to collectively perform state transitions 
in the cryptoeconomic system.
 - computing power
 - cryptocurrency / token

**Economic set** - all agents possessing economic resource.

**Cryptoeconomic Security Margin** - an amount of money X such that you can prove "either a given guarantee G is 
satisfied or those at fault for violating G are poorer than they otherwise would have been by at least X".
 - if expressed as a percentage or a ratio, represents the ratio of the economic set, e.g. security margin of 0.5
 means that it costs the attacker half of all computing power cost to violate the guarantee G.
 

**Cryptoeconomic proof** - a message signed by an actor that can be interpreted as "I certify that either P is true,
or I suffer an economic loss of size X".

---

### Security Models

Security models are different in the assumptions that they make about the real world. It's not clear what assumptions
are more realistic, nevertheless it's useful to perform analysis in different models to have the clearer picture about
the security of a system.

Different security models give different security margins.

**Honest Majority** - assumes that up to X (usually a number less that 1/2) of agents are controlled by an attacker, 
and the remaining agents honestly follow the protocol.
 - **Tranditional Fault Tolerance** - assumes almost all agents are honest (X is close to 0).
 - **Bysantine Fault Tolerance** - assumes up to 1/3 of agents are controlled by an attacker.

**Uncoordinated Majority** - assumes that up to X (often between 1/4 and 1/2) of agents are capable of coordinating 
their actions, all agents are rational in a game-theoretic sense.
 - additional parameter - level of coordination.

**Coordinated Majority** - assumes that all agents are controlled by the same actor, or are fully capable of coordinating 
on the economically optimal choice between themselves. We can talk about the cost to the coalition 
(or profit to the coalition) of achieving some undesirable outcome.

**Bribing Attacker** - takes the uncoordinated majority model, but instead of making the attacker be one of the participants, 
the attacker sits outside the protocol, and has the ability to bribe any participants to change their behavior. 
Attackers are modeled as having a budget, which is the maximum that they are willing to pay, and we can talk about 
their cost, the amount that they end up paying to disrupt the protocol equilibrium.
 - additional parameter - budget requirement.
 
---

**[Bitcoin with selfish mining fix](https://arxiv.org/abs/1311.0243)** analysis:

| Model | Security Margin |
| ---  | --- |
| Honest Majority | 0.5 (51% attack) | 
| Uncoordinated Majority | 0.25 (selfish mining attack)* |
| Coordinated Majority | 0 |
| Bribing Attacker | 13.2 * k budget, 0 cost |

<nowiki>*</nowiki> (1) Assuming more than 0.5 of the economic set are coordinated.
(2) Without the selfish mining fix the security margin in uncoordinated majority model is epsilon 
(slighter greater than 0).
 
**[Shelling coin](https://blog.ethereum.org/2015/01/28/p-epsilon-attack/)** analysis:

| Model | Security Margin |
| ---  | --- |
| Honest Majority | 0.5 (51% attack) | 
| Uncoordinated Majority | 0.25 ** |
| Coordinated Majority | 0 |
| Bribing Attacker | 0.5 budget, 0 cost |

** The attacker only needs to possess half of the coordinated part of the economic set. 
The other half has an incentive to vote with the attacker. 

---

### Examples of Cryptoeconomic Systems

 - Consensus algorithms
 - Outsources computation and storage
 - Provable fair random number generation
 - Providing true information about the world (oracles)
 - Governance (DAOs)
 - Stable-value cryptocurrencies (stablecoin)
 - Bounties to solutions to math or CS problems
 - Telling the time

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

