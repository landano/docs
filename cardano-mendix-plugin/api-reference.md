# API Reference

This section provides technical documentation for all Java and JavaScript actions included in the `CardanoWallet`, `Blockfrost`, and `PinataIPFS` modules. Each entry includes the purpose, input parameters, and expected return values.

***

#### Module: `CardanoWallet`

**`JA_Account_GenerateMnemonics`**

Generates a new 15-word mnemonic phrase.

* **Inputs**: none
* **Returns**: `Mnemonic (String)`

***

**`JA_EncryptMnemonic`**

Encrypts a mnemonic using a passphrase and system key.

* **Inputs**:
  * `Mnemonic (String)`
  * `Passphrase (String)`
* **Returns**: `EncryptedMnemonic (String)`

***

**`JA_DecryptMnemonic`**

Decrypts an encrypted mnemonic using the user's passphrase.

* **Inputs**:
  * `EncryptedMnemonic (String)`
  * `Passphrase (String)`
* **Returns**: `Mnemonic (String)`

***

**`JA_Account_CreateFromMnemonic`**

Restores a wallet object from a mnemonic.

* **Inputs**:
  * `Mnemonic (String)`
  * `Network (Enum)` – Mainnet / Testnet
* **Returns**: `Wallet (Object)` with address, keys, and fingerprint

***

**`JA_Account_GetBalances`**

Queries the balance of the wallet from the blockchain.

* **Inputs**:
  * `Wallet (Object)`
* **Returns**: `Lovelace (Long)` – Balance in lovelace

***

**`JA_CardanoTransaction`**

Builds, signs, and submits a transaction.

* **Inputs**:
  * `SenderWallet`
  * `ReceiverAddress (String)`
  * `Amount (Long)`
  * `Passphrase (String)`
  * `Optional: Metadata (JSON)`
* **Returns**: `Transaction Hash (String)`

***

**`JA_CardanoTransaction_UnSigned`**

Builds an unsigned transaction for multi-sig flows.

* **Inputs**: Same as above
* **Returns**: `UnsignedTx (Serialized)`

***

**`JA_Transaction_Submit`**

Submits a raw transaction (already signed or witnessed).

* **Inputs**:
  * `TransactionHex (String)`
* **Returns**: `Transaction Hash (String)`

***

**`JA_Simple_TransactionBuildSignSubmit`**

One-liner to handle simple transactions with signing and submission.

* **Inputs**: Similar to `JA_CardanoTransaction`
* **Returns**: `Transaction Hash (String)`

***

**`JA_MultiSig_Transaction_Build`**

Builds a transaction using a native multi-sig script.

* **Inputs**:
  * `Script (JSON)`
  * `ReceiverAddress`
  * `Amount`
* **Returns**: `UnsignedTx (String)`

***

**`JA_MultiSig_Transaction_Sign`**

Adds a witness signature to an existing transaction.

* **Inputs**:
  * `TransactionHex`
  * `SignerWallet`
* **Returns**: `PartiallySignedTx (String)`

***

**`JA_MultiSig_Transaction_Submit`**

Submits a multi-signed transaction.

* **Inputs**:
  * `FinalTxHex (String)`
* **Returns**: `Transaction Hash (String)`

***

**`JA_Mint_NFT` / `JA_NFT_Mint`**

Mints an NFT with metadata and optional IPFS media.

* **Inputs**:
  * `PolicyScript`
  * `Metadata JSON`
  * `SenderWallet`
  * `Passphrase`
* **Returns**: `AssetId (String)`

***

**`JA_NFT_Burn`**

Burns a previously minted NFT.

* **Inputs**:
  * `AssetId`
  * `Wallet`
  * `Passphrase`
* **Returns**: `Transaction Hash (String)`

***

**`JA_PolicyScript_Create`**

Generates a native policy script (time-locked, single or multi-sig).

* **Inputs**: Configuration object or JSON
* **Returns**: `PolicyScript (JSON)`

***

**`JA_GenerateAssetUnitId`**

Generates the unique unit ID for a native asset.

* **Inputs**:
  * `PolicyId`
  * `AssetName`
* **Returns**: `UnitId (String)`

***

**`JA_SmartContract_Lock`**

Locks funds using a Plutus smart contract script.

* **Inputs**:
  * `PlutusScript`
  * `Datum`
  * `Wallet`
  * `Passphrase`
* **Returns**: `Tx Hash`

***

**`JA_SmartContract_Unlock`**

Unlocks funds by executing the script with a redeemer.

* **Inputs**:
  * `PlutusScript`
  * `Datum`
  * `Redeemer`
  * `Wallet`
  * `Passphrase`
* **Returns**: `Tx Hash`

***

#### Module: `Blockfrost`

Most functionality here is abstracted behind the main `CardanoWallet` actions, but you may also expose additional raw calls via:

* `BlockfrostQueryHelper` (custom Java helper class)
* Optional: extend with new REST endpoints (e.g., get UTXOs, protocol params)

***

#### Module: `PinataIPFS`

**`JA_IPFS_UploadFile`**

Uploads a media file to IPFS via Pinata.

* **Inputs**:
  * `Binary file`
  * `API Key`
  * `API Secret`
* **Returns**: `CID (String)` – IPFS hash

**`JA_IPFS_UploadJSON`**

Pins JSON metadata to IPFS via Pinata.

* **Inputs**:
  * `JSON (String)`
  * `API Key`
  * `API Secret`
* **Returns**: `CID (String)`

***

#### JavaScript Actions (for Web / CIP-30 Support)

**`JS_Wallet_Connect`**

Requests connection to a browser wallet via CIP-30.

* **Returns**: Boolean (success)

**`JS_GetUsedCardanoWalletAddresses`**

Returns the payment address list from the connected wallet.

* **Returns**: `List of addresses`

**`JS_GetCardanoWalletRewardAddresses`**

Returns the reward (staking) address from the wallet.

* **Returns**: `Reward address (String)`
