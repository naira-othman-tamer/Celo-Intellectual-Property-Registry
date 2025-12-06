# 📜 Celo Intellectual Property Registry

A professional Intellectual Property Registry built on the Celo blockchain for timestamping and registering ideas with immutable proof.

## 🎯 Features

- **Immutable Registration**: Store IP records permanently on the Celo blockchain
- **Trusted Timestamps**: Every registration includes a verifiable blockchain timestamp
- **Global Verification**: Anyone can verify registration authenticity using the record ID
- **Professional UI**: Clean, legal-tech inspired design with white, gold, and slate color scheme
- **Celo Mainnet Support**: Fully compatible with Celo Mainnet & Celo Sepolia

## 🛠️ Tech Stack

- **Frontend**: HTML5, Tailwind CSS, JavaScript
- **Blockchain**: Ethers.js v5.7.2
- **Smart Contract**: Solidity ^0.8.0
- **Network**: Celo Mainnet (Primary) / Celo Sepolia (Testnet)

## 📁 Project Structure

## 🚀 Setup Instructions

### 1. Deploy the Smart Contract

1. Open [Remix IDE](https://remix.ethereum.org/)
2. Create a new file called `Registry.sol`
3. Copy the contents from `Registry.sol` in this project
4. Compile with Solidity compiler version ^0.8.0
5. Deploy to **Celo Mainnet**:
   - Connect MetaMask to Celo Mainnet (Chain ID: 42220)
   - Use Injected Provider in Remix
   - Deploy the contract
   - Copy the deployed contract address

### 2. Configure the Frontend

1. Open `index.html`
2. Find line `const contractAddress = "...";`
3. Replace the address with your deployed contract address
4. Save the file

### 3. Run the Application

Simply open `index.html` in a web browser or deploy via GitHub Pages.

## 🔧 Getting Celo Tokens

- **For Mainnet**: Ensure your wallet is funded with real CELO.
- **For Sepolia Testnet**: Visit [Celo Faucet](https://faucet.celo.org/sepolia) to get free testnet tokens.

## 📖 How to Use

### Register an Idea

1. Click "Get Started" on the landing page
2. Click "Connect Wallet" and approve MetaMask connection
3. The app will automatically switch to Celo Mainnet
4. Fill in the registration form:
   - **Title**: Name of your intellectual property
   - **Owner Name**: Your name or organization
   - **Description**: Detailed description or content hash (SHA-256)
5. Click "Register Idea on Blockchain"
6. Approve the transaction in MetaMask
7. Receive a certificate with your unique Registration ID

### Verify a Registration

1. Click "or verify an existing registration"
2. Enter the Registration ID
3. Click "Verify"
4. View the immutable record details

## 🌐 Network Configuration

**Celo Mainnet (Default)**
- Chain ID: 42220 (0xa4ec)
- RPC URL: https://forno.celo.org
- Explorer: https://celoscan.io/

**Celo Sepolia (Testnet)**
- Chain ID: 44787 (0xaa044c)
- RPC URL: https://alfajores-forno.celo-testnet.org
- Explorer: https://sepolia.celoscan.io/

## 🎨 Design Features

- **Typography-focused**: Clean Inter font family
- **Color Palette**: White backgrounds, slate text, gold accents (#D4AF37)
- **Responsive**: Mobile-friendly design with Tailwind CSS
- **Certificate-style**: Professional document presentation for registrations

## 🔒 Security Considerations

- All data is stored on-chain and immutable
- Owner address is automatically captured from connected wallet
- Timestamps are blockchain-verified

## 📄 License

MIT License - Feel free to use this project for your own purposes.

---

**Built with ❤️ on Celo**
