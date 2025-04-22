# User Guides

This section explains the user-facing flows available in the reference application bundled with the Cardano Mendix Plugin. These guides walk you through the typical actions a user can perform, such as creating a wallet, sending ADA, or minting an NFT. Each guide reflects the UI and logic demonstrated in the example project.

#### Create a Wallet

**Flow:**

1. Navigate to the “Wallets” page.
2. Click **Create Wallet**.
3. Enter a secure passphrase.
4. The app generates a 15-word mnemonic and securely stores it encrypted with your passphrase.
5. The wallet is added to the list with a unique name and address.

**Result:** A new wallet is created and stored securely, ready to be used for transactions.

***

#### Restore a Wallet

**Flow:**

1. Navigate to the “Wallets” page.
2. Click **Restore Wallet**.
3. Enter your 15-word mnemonic and a passphrase.
4. The app recreates the wallet and displays it in the list.

**Result:** Access to a previously created wallet is restored.

***

#### Connect Browser Wallet (CIP-30)

**Flow:**

1. Navigate to the “Connect Wallet” page.
2. Choose a browser wallet (e.g., Nami, Eternl).
3. Authorize the app in the browser extension.
4. Your wallet address and balance are now linked to the app session.

**Result:** The app can now interact with your connected browser wallet.

***

#### Send ADA

**Flow:**

1. Select a wallet from the overview.
2. Click **Send ADA**.
3. Enter the receiver address and the amount of ADA.
4. Confirm with your passphrase.
5. The transaction is submitted and confirmed on-chain.

**Result:** ADA is sent from your wallet to another address.

***

#### Send ADA with Metadata

**Flow:**

1. Navigate to the **Metadata Transaction** page.
2. Enter the transaction data, including the key-value metadata pairs.
3. Submit the transaction.

**Result:** A standard transaction is broadcasted with additional metadata attached.

***

#### Multi-signature Transaction

**Flow:**

1. Navigate to the **Multi-sig** tab.
2. Create a multi-sig policy script (with multiple wallet addresses).
3. Build a transaction that requires multiple signatures.
4. Each participant signs the transaction individually.
5. Once all signatures are collected, submit the transaction.

**Result:** A multi-sig transaction is successfully executed following native script rules.

***

#### Mint an NFT

**Flow:**

1. Navigate to the **NFTs** tab.
2. Click **Create NFT**.
3. Fill in the asset name, description, and optionally upload media (stored via IPFS).
4. Click **Mint NFT** and confirm with your passphrase.

**Result:** A new native asset is created and stored on-chain as an NFT.

***

#### Burn an NFT

**Flow:**

1. Open the NFT details.
2. Click **Burn** and confirm with your passphrase.

**Result:** The asset is removed from circulation.

***

#### Smart Contract – Lock & Unlock

**Flow:**

1. Navigate to the **Smart Contract** section.
2. Select whether to **Lock** or **Unlock** funds.
3. Enter the required script parameters (e.g. address, datum).
4. Confirm and submit.

**Result:** Funds are locked or unlocked according to the smart contract rules.
