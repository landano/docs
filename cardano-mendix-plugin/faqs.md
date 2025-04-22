# FAQs

### Frequently Asked Questions (FAQ)

#### Can I use this plugin with my own Cardano node?

> No. The current version of the plugin **only supports Blockfrost** for querying and submitting transactions to the Cardano blockchain. Support for direct node interaction may be added in the future.

***

#### Can I use this plugin with browser wallets like Lace or Eternl?

> Yes, browser wallet support is provided via **CIP-30** using JavaScript actions like `JS_Wallet_Connect`. This allows you to connect, read addresses, and sign transactions directly in the browser context.

***

#### Where are the mnemonics stored?

> Mnemonics are **encrypted with a user passphrase** and stored in the Mendix database. You must provide the correct passphrase to decrypt the mnemonic before signing transactions.

***

#### Is this plugin compatible with Mendix Native Mobile?

> Yes, although some JavaScript actions (like browser wallet connection) are web-specific. For native apps, you can use the full wallet stack by storing and managing mnemonics securely on-device or integrating a mobile-friendly signing layer.

***

#### Can I test on the Cardano testnet?

> Yes. The plugin supports the **Preprod** and **Preview** testnets. When using Blockfrost, make sure your API key is linked to the correct network, and fund your wallet using the [Cardano Testnet Faucet](https://testnets.cardano.org/en/testnets/cardano/tools/faucet/).

***

#### Is NFT minting supported?

> Yes. You can mint native assets (NFTs) using the `JA_Mint_NFT` or `JA_NFT_Mint` actions. You can also use the optional `PinataIPFS` module to host metadata and media content.

***

#### How is metadata attached to a transaction?

> Transaction metadata can be passed as a **JSON string** to the `TransactionMetaData` parameter in actions like `JA_CardanoTransaction`. This supports custom certification, tagging, or indexing use cases.

***

#### Can I perform multi-signature transactions?

> Yes. The plugin supports native script-based **multi-sig flows**, allowing you to build, sign (by multiple parties), and submit transactions. These flows are exposed via `JA_MultiSig_Transaction_Build`, `Sign`, and `Submit`.

***

#### How do I add new blockchain features?

> You can extend the plugin by creating new Java actions using the **Cardano Client Lib** (already embedded in the plugin). Wrap these in microflows and expose them in your Mendix UI as needed.

***

#### What should I do if a transaction fails?

> Check the following:

* Is the Blockfrost API key correct and active?
* Is your wallet funded?
* Is the passphrase correct and able to decrypt the mnemonic?
* Are all required fields (receiver address, amount, metadata) filled in?

You can also inspect the logs in Mendix Studio Pro and/or enable debug logging for the `CardanoWallet` module.
