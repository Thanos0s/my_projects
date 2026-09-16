# Avalanche Consensus Basics

## What Is Consensus in Blockchain?

**Consensus** is the process by which all computers, or **nodes**, in a blockchain network agree on:

- Which transactions are valid
- What the current state of the blockchain should be
- Which block should be added next
- Whether someone is attempting to spend the same funds twice

### A Simple Analogy

Imagine that many people have copies of the same notebook. Before adding a new page, everyone needs a way to agree that the information on that page is correct.

Blockchain consensus mechanisms provide this method of agreement without relying on a central authority.

## Why Is Consensus Needed?

Blockchain networks are decentralized. This means there is no single authority, such as a bank, deciding:

- Which transactions are valid
- Who owns which assets
- Which block should be added next
- Whether a transaction attempts to spend the same funds twice

Consensus allows the network to make these decisions collectively.

## Common Consensus Mechanisms

| Consensus mechanism | How it works | Example |
| --- | --- | --- |
| **Proof of Work (PoW)** | Computers solve computational puzzles. | Bitcoin |
| **Proof of Stake (PoS)** | Validators stake cryptocurrency to participate in the network. | Ethereum |
| **Delegated Proof of Stake (DPoS)** | Users delegate their stake to selected validators. | Some PoS networks |
| **Proof of Authority (PoA)** | Approved validators create and validate blocks. | Private or permissioned blockchains |

## Example: Proof of Stake

Suppose 100 validators are participating in a network:

1. A user sends 10 ETH to another user.
2. The transaction is broadcast to the network.
3. A validator proposes a block containing the transaction.
4. Other validators check the block.
5. If the required consensus is reached, the block becomes part of the blockchain.
6. The blockchain state is updated across the network.

> **In one sentence:** Consensus is the method a decentralized blockchain uses to make its participants agree on the valid state of the network.

### Consensus vs. Encryption

Consensus is not the same as encryption:

- **Encryption** protects information by making it unreadable to unauthorized parties.
- **Consensus** helps the network agree on what is true and valid.

---

## Blockchain Highway Analogy

### Question

Following the highway analogy, what would one want in a highway or blockchain?

### Options

- **A.** Few lanes, meaning there will be no bottlenecks between cars or transactions going to the same place, resulting in high throughput. The highway should also be as long as possible.
- **B.** Many lanes, meaning cars or transactions can go faster, resulting in high throughput. The highway should also be as short as possible so cars or transactions reach their destination quickly.
- **C.** Many lanes, meaning multiple cars or transactions can move at the same time, resulting in high throughput. The highway should also be as short as possible so cars or transactions reach their destination quickly.
- **D.** Many lanes, meaning cars or transactions can go faster, resulting in low throughput. The highway should also be as short as possible.

### Correct Answer

**C.** Many lanes and a short route.

- We build **Layer 1 blockchains (L1s)**, which function like different lanes, to achieve high throughput.
- We use a fast consensus protocol, which functions like a short route, to achieve low time to finality.

---

## Avalanche Consensus Questions

### When Does a Validator in Avalanche Finalize Its Decision?

A validator finalizes its decision **after its preference has been confirmed by an α-majority for β consecutive rounds**.

Here:

- **α (alpha)** is the decision threshold or required majority.
- **β (beta)** is the number of consecutive successful rounds required for confidence.

Finalization does not happen after only one round. It does not happen immediately when a conflict appears, and it does not require responses from every validator in the network.

### What Is the Role of Validators When Transactions Conflict?

When two transactions conflict, validators collectively decide which transaction will be accepted by the network. This decision determines the next state of the blockchain.

Validators do **not**:

- Automatically accept both conflicting transactions
- Reject every conflicting transaction
- Create new transactions to resolve the conflict

### What Happens During One Round of Querying in Avalanche Consensus?

During each round of Avalanche Consensus, a validator:

1. Randomly selects a small subset, or sample, of other validators.
2. Asks them about their current preference.
3. Uses their responses to update or confirm its own preference.

This approach is more efficient than broadcasting a query to the entire network.
