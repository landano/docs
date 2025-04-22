# Getting Started

This guide will help you integrate and begin using the Cardano Mendix Plugin in your Mendix applications. The plugin enables seamless interaction with the Cardano blockchain and comes bundled with a complete working example app.

***

#### Plugin Overview

The plugin is delivered through three primary Mendix modules:

* **CardanoWallet**: Core blockchain logic, wallet handling, and transaction flows.
* **Blockfrost**: Required integration for communicating with the Cardano blockchain via Blockfrost.io.
* **PinataIPFS**: Optional IPFS integration for storing NFT metadata and media files on Pinata.

A complete example project is included, showcasing real use cases such as wallet creation, simple transactions, metadata handling, NFT minting, and smart contract interaction. While video references are available for internal understanding, the primary way to explore functionality is via the included working app.

***

#### Prerequisites

To use the plugin, ensure you have:

* Mendix Studio Pro 10.x
* Java 11+ (required for custom runtime actions)
* A Blockfrost API key (testnet or mainnet)
* Optional: Pinata IPFS API keys (for NFT media)

***

#### Installation

You have two options for installation:

**Option 1: Use the Complete Example App**

We recommend starting with the provided full-featured demo app, which includes:

* Wallet flows (create, restore)
* ADA transactions
* NFT minting and metadata
* Multi-sig and smart contracts

**Option 2: Import Modules Manually**

1. In Mendix Studio Pro, go to `App Explorer → Import Module Package`
2. Import these modules in order:
   * `CardanoWallet`
   * `Blockfrost`
   * `PinataIPFS` _(optional)_

Configure constants or helper flows as needed (e.g. Blockfrost API key).

***

#### Blockchain Access: Blockfrost Only

Currently, the plugin exclusively supports [Blockfrost](https://blockfrost.io) as the backend for all Cardano interactions.

**Setup Steps:**

1. Register at Blockfrost.io and generate a project
2. Choose **Preprod** or **Mainnet**
3. Copy your API key
4. Insert it into your Mendix constants or secure configuration object
5. Ensure the correct network enum is passed to all Java actions

There is no support yet for running your own Cardano node.

***

#### Core Plugin Functions

| Function           | Java Action(s) or Flow(s)                              |
| ------------------ | ------------------------------------------------------ |
| **Create Wallet**  | `JA_Account_GenerateMnemonics` → `JA_EncryptMnemonic`  |
| **Restore Wallet** | `JA_DecryptMnemonic` → `JA_Account_CreateFromMnemonic` |
| **Connect Wallet** | `JS_Wallet_Connect` (via CIP-30 or native context)     |
| **Check Balance**  | `JA_Account_GetBalances`                               |

***

#### Transactions

| Function                        | Java Action(s)                                           |
| ------------------------------- | -------------------------------------------------------- |
| **Send ADA**                    | `JA_CardanoTransaction`                                  |
| **Send with Metadata**          | `JA_CardanoTransaction` with `TransactionMetaData` param |
| **Create Unsigned Transaction** | `JA_CardanoTransaction_UnSigned`                         |
| **Sign and Submit Transaction** | `JA_Simple_TransactionBuildSignSubmit`                   |

***

#### Multi-signature (Native Scripts)

| Step                            | Java Action(s)                   |
| ------------------------------- | -------------------------------- |
| **Build Multi-sig Transaction** | `JA_MultiSig_Transaction_Build`  |
| **Sign Transaction**            | `JA_MultiSig_Transaction_Sign`   |
| **Submit Multi-sig**            | `JA_MultiSig_Transaction_Submit` |

***

#### NFTs

| Function             | Java Action(s)                                      |
| -------------------- | --------------------------------------------------- |
| **Mint NFT**         | `JA_Mint_NFT` or `JA_NFT_Mint`                      |
| **Burn NFT**         | `JA_NFT_Burn`                                       |
| **Get Asset Name**   | `JA_GetAssetName`                                   |
| **Generate Unit ID** | `JA_GenerateAssetUnitId`                            |
| **Attach IPFS Data** | Use `PinataIPFS` upload + pass hash to NFT metadata |

***

#### Smart Contracts (Lock / Unlock)

| Function         | Java Action(s)            |
| ---------------- | ------------------------- |
| **Lock funds**   | `JA_SmartContract_Lock`   |
| **Unlock funds** | `JA_SmartContract_Unlock` |

***

#### Next Steps

* Explore the User Guides for detailed flow walkthroughs
* Use the API Reference to learn all Java actions
* Fork the example app to kickstart your own dApp use case
