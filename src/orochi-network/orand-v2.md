# Orand V2

Orand project was built based on Elliptic Curve Verifiable Random Function (ECVRF). It is deterministic, verifiable and secured based on assumptions from elliptic curves. Administrators of Orochi Network are unable to manipulate the results.

To optimize operation costs and improve security we provided following features:

- **Verifiable:** An Orand's epoch can be verified independently outside our system or can be verified by smart contracts.
- **Self and Delegated Submission:** Orand project have flexibility in proof submission, we just generate valid ECVRF proof and you can decide how to submit them:
  - **Self Submission:** You can request from your back-end to Orand service and submit the randomness to your smart contract.
  - **Delegation Submission:** You can delegate the submission process to Orochi Network by transfer token to our operator, so the feeding process will be performed automatically.
- **Batching:** We allow you to set the batching limit for one epoch, e.g., we can batch `100` randomness for one single epoch which makes the cost be reduced significantly.

## Self Submission

User will request the verifiable randomness from Orand service, they can submit the randomness themselves and control gas consumption. You must submit epoch by sequence and starting epoch or genesis must be epoch `0`.

```mermaid
%%{init: {'theme':'base'}}%%
sequenceDiagram
    Game Backend->>+Orand: Request randomness
    Orand->>-Game Backend: VRF Epoch
    Game Backend->>+Orand Contract: Publish VRF Epoch
    Orand Contract->>-Game Backend: Transaction Receipt
```

## Delegated Submission

User will delegate the submission process to Orochi Network, first they need to deposit native token to operator address that provided by Orochi Network.

```mermaid
%%{init: {'theme':'base'}}%%
sequenceDiagram
    Game Backend->>+Orand: Request randomness
    Orand->>+Orand Contract: Publish VRF Epoch
    Orand Contract->>-Orand: Transaction Receipt
    Orand->>-Game Backend: VRF Epoch + Tx Receipt
```

## Request Submission

dApp will request to a application contract for the randomness, Orand service will fulfill this request and submit the randomness to Orand provider contract.

```mermaid
%%{init: {'theme':'base'}}%%
sequenceDiagram
    Game Frontend->>+Application Contract: Request randomness
    Orand->>+Orand: Repeating Polling Request
    Orand->>-Orand Contract: Fulfil Request
    Orand Contract->>Game Frontend: Tx Receipt
```

## Deployed Platform

Orand V2 was deployed on following smart contract platform.

### Testnet

| Network Name          | Address                                                                                                                             |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Ancient8 Testnet      | [0xfB40e49d74b6f00Aad3b055D16b36912051D27EF](https://scanv2-testnet.ancient8.gg/address/0xfB40e49d74b6f00Aad3b055D16b36912051D27EF) |
| Unicorn Ultra Nebulas | [0xf33B79F915fC4A870ED1b26356C9f6EB60638DB8](https://testnet.u2uscan.xyz/address/0xf33B79F915fC4A870ED1b26356C9f6EB60638DB8)        |

## Orand V3

Orand V3 will focus on utilizing Multi Party Computation (MPC) to secure the randomness generation, allowing the whole system to act as one random oracle. It makes the process more dispersed. In this stage, we boot up **Chaos Theory Alliance** to preventing predictability. Everything is built up toward to the vision of **Decentralized Random Number Generator**. If you believe in the vision of **Decentralized Random Number Generator**, please send drop us an email to ([contact@orochi.network](contact@orochi.network)) in order to participate in **Chaos Theory Alliance**.