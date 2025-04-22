# Developer Guide

This section provides a technical breakdown of the core flows, components, and logic implemented in the Cardano Mendix Plugin and example project.

Use this guide if you're planning to:

* Modify or extend the blockchain functionality
* Reuse flows in your own Mendix app
* Understand the architecture and security patterns

***

#### Architecture Overview

The plugin is modularized as follows:

| Module          | Purpose                                                     |
| --------------- | ----------------------------------------------------------- |
| `CardanoWallet` | Core functionality: wallet creation, ADA transfers, NFTs    |
| `Blockfrost`    | API abstraction layer for querying Cardano blockchain state |
| `PinataIPFS`    | IPFS media upload and NFT metadata pinning (optional)       |

Each module provides isolated Java actions, helper flows, and configuration entities.

***

#### Wallet Creation

| Layer        | Element                        |
| ------------ | ------------------------------ |
| Microflow    | `ACT_Wallet_Create`            |
| Submicroflow | `CWS_Wallets_CreateRestore`    |
| Java Action  | `JA_Account_GenerateMnemonics` |
| Java Action  | `JA_EncryptMnemonic`           |

The mnemonic is stored encrypted using a combination of a user-provided passphrase and a configured key. All wallets are persisted in the `Wallet` entity.

***

#### Wallet Restoration

| Layer        | Element                         |
| ------------ | ------------------------------- |
| Microflow    | `ACT_Wallet_Restore`            |
| Submicroflow | `ACT_Wallet_CreateRestore_Save` |
| Java Action  | `JA_DecryptMnemonic`            |
| Java Action  | `JA_Account_CreateFromMnemonic` |

Mnemonic decryption is required to regenerate the wallet object and corresponding payment address.

***

#### Browser Wallet Connection (CIP-30)

| Layer             | Element                              |
| ----------------- | ------------------------------------ |
| JavaScript Action | `JS_Wallet_Connect`                  |
| JavaScript Action | `JS_GetUsedCardanoWalletAddresses`   |
| JavaScript Action | `JS_GetCardanoWalletRewardAddresses` |

This is used in web apps to interact with browser wallets like Nami or Eternl. Returned addresses are stored temporarily and tied to the user session.

***

#### ADA Transaction (Simple)

| Layer       | Element                 |
| ----------- | ----------------------- |
| Microflow   | `ACT_Wallet_Confirm`    |
| Java Action | `JA_DecryptMnemonic`    |
| Java Action | `JA_CardanoTransaction` |

The flow takes user input (receiver address, amount), constructs and signs a transaction, and submits it via Blockfrost.

***

#### ADA Transaction with Metadata

| Layer       | Element                                 |
| ----------- | --------------------------------------- |
| Java Action | `JA_CardanoTransaction` (with metadata) |
| Entity      | `TransactionMetaData`                   |

The `TransactionMetaData` is passed as a parameter to the transaction builder.

***

#### Multi-sig Transaction

| Layer       | Element                                 |
| ----------- | --------------------------------------- |
| Microflow   | `ACT_Transaction_MultiSig_OpenStep1`    |
| Subflow     | `SUB_Transaction_PrepareWitnessSigning` |
| Java Action | `JA_MultiSig_Transaction_Build`         |
| Java Action | `JA_MultiSig_Transaction_Sign`          |
| Java Action | `JA_MultiSig_Transaction_Submit`        |

The transaction is constructed using a native script policy, signed in multiple steps, and submitted once complete.

***

#### NFT Minting

| Layer       | Element                       |
| ----------- | ----------------------------- |
| Microflow   | `ACT_NFT_NewEdit`             |
| Microflow   | `ACT_NFT_Mint`                |
| Java Action | `JA_Mint_NFT` / `JA_NFT_Mint` |
| Java Action | `JA_GenerateAssetUnitId`      |
| Java Action | `JA_PolicyScript_Create`      |

If using IPFS, upload via `PinataIPFS` and include the returned CID in the NFT metadata.

***

#### NFT Burn

| Layer       | Element        |
| ----------- | -------------- |
| Microflow   | `ACT_NFT_Burn` |
| Java Action | `JA_NFT_Burn`  |

Requires the original minting policy to burn the token correctly.

***

#### Smart Contract Lock / Unlock

| Layer       | Element                   |
| ----------- | ------------------------- |
| Java Action | `JA_SmartContract_Lock`   |
| Java Action | `JA_SmartContract_Unlock` |

Locking requires defining a valid Plutus script with redeemer and datum values. Unlocking consumes the locked UTxO by proving correct script execution.

***

#### Security & Storage

* **Encrypted mnemonics** are stored in a persistent entity (`EncryptedMnemonic`)
* **Passphrase-based encryption** uses a secret key defined in the plugin configuration
* **Never store plain mnemonics or private keys**

***

#### Extending the Plugin

To add new blockchain capabilities:

1. Create a new Java action in the `CardanoWallet` module
2. Wrap the logic using the Cardano Client Lib (already included)
3. Expose the action via a microflow or nanoflow
4. Secure access via roles in the module settings

