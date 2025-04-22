# Cardano Mendix Plugin

### **Overview**

Welcome to the official documentation for the **Cardano Mendix Plugin** — a powerful integration that connects the Mendix low-code platform to the Cardano blockchain. This plugin is developed as part of the Landano initiative and is designed to make blockchain capabilities easily accessible to Mendix developers and enterprises building Web3 solutions.

***

#### **What is the Cardano Mendix Plugin?**

The Cardano Mendix Plugin bridges Mendix and the Cardano blockchain, enabling developers to seamlessly integrate decentralized functionality into their Mendix applications.

Whether you're working on digital identity, payments, land registration, or NFTs — this plugin provides the foundational building blocks to connect your app to the Cardano ecosystem.

***

#### **Key Features**

* **Wallet Management**\
  Create, restore, and manage Cardano wallets securely within your Mendix app.
* **ADA Transactions**\
  Send ADA between wallets with simple transaction flows.
* **Multi-signature Support**\
  Create and execute multi-sig transactions using native scripts.
* **NFT Creation**\
  Mint native assets and NFTs with policy control.
* **Transaction Metadata**\
  Attach custom metadata to transactions for use cases like document certification or provenance.
* **Smart Contract Integration**\
  Interact with Plutus smart contracts (Aiken-ready architecture).

***

#### **Architecture Overview**

The plugin is composed of:

* A set of Mendix modules (Java actions, microflows)
* A Java-based integration layer powered by the [Cardano Client Lib](https://github.com/bloxbean/cardano-client-lib)
* Optional native frontend components (in the case of mobile wallets or CIP-30 support)
* Designed for both **custodial** and **non-custodial** wallet patterns

You can integrate it into both **Mendix Web** and **Mendix Native Mobile** applications.

***

#### **Who is it for?**

* **Mendix Developers** looking to add blockchain features with low-code tools
* **Enterprises** exploring decentralized infrastructure
* **Catalyst-funded projects** building dApps or digital registries
* **Government & NGO systems** for digital land administration and certification

***

#### 📦 **Requirements**

* Mendix 10.x
* Java 11+ (for custom runtime actions)
* GitBook knowledge base (this site!)
* Cardano Node or Blockfrost (depending on setup)

***

#### 🔗 **Related Resources**

* [Cardano Client Lib](https://github.com/bloxbean/cardano-client-lib)
* [Landano Website](https://landano.io/)
* [Mendix Platform](https://mendix.com/)

***

#### ⏭️ **What’s Next?**

Check out the [Getting Started Guide](getting-started.md) to set up the plugin in your Mendix app, or explore [User Guides](user-guides.md) for transaction and wallet flows.

