# 📜 Celo Intellectual Property Registry - MVP

A professional Intellectual Property Registry built on the Celo blockchain for timestamping and registering ideas with immutable proof.

## 🎯 Features

- **Immutable Registration**: Store IP records permanently on the Celo blockchain
- **Trusted Timestamps**: Every registration includes a verifiable blockchain timestamp
- **Global Verification**: Anyone can verify registration authenticity using the record ID
- **Professional UI**: Clean, legal-tech inspired design with white, gold, and slate color scheme
- **Celo Alfajores Testnet**: Built for Celo's testnet with automatic network switching

## 🛠️ Tech Stack

- **Frontend**: HTML5, Tailwind CSS, JavaScript
- **Blockchain**: Ethers.js v5.7.2
- **Smart Contract**: Solidity ^0.8.0
- **Network**: Celo Alfajores Testnet

## 📁 Project Structure

```
p3/
├── index.html       # Complete SPA with UI and blockchain integration
├── Registry.sol     # Smart contract for IP registration
└── README.md        # This file
```

## 🚀 Setup Instructions

### 1. Deploy the Smart Contract

1. Open [Remix IDE](https://remix.ethereum.org/)
2. Create a new file called `Registry.sol`
3. Copy the contents from `Registry.sol` in this project
4. Compile with Solidity compiler version ^0.8.0
5. Deploy to **Celo Alfajores Testnet**:
   - Connect MetaMask to Celo Alfajores (Chain ID: 44787)
   - Use Injected Provider in Remix
   - Deploy the contract
   - Copy the deployed contract address

### 2. Configure the Frontend

1. Open `index.html`
2. Find line ~267: `const contractAddress = "PUT_ADDRESS_HERE";`
3. Replace `"PUT_ADDRESS_HERE"` with your deployed contract address
4. Save the file

### 3. Run the Application

Simply open `index.html` in a web browser. No build process required!

## 🔧 Getting Celo Testnet Tokens

1. Visit [Celo Alfajores Faucet](https://faucet.celo.org/alfajores)
2. Enter your wallet address
3. Receive free testnet CELO tokens

## 📖 How to Use

### Register an Idea

1. Click "Get Started" on the landing page
2. Click "Connect Wallet" and approve MetaMask connection
3. The app will automatically switch to Celo Alfajores network
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

## 🔐 Smart Contract Functions

### `registerRecord(string _title, string _ownerName, string _data)`
Registers a new IP record on the blockchain.
- **Parameters**: Title, Owner Name, Description/Hash
- **Returns**: Unique Record ID
- **Emits**: `RecordRegistered` event

### `getRecord(uint256 _id)`
Retrieves a record by its ID.
- **Parameters**: Record ID
- **Returns**: Owner address, timestamp, title, owner name, data

### `getRecordsByOwner(address _owner)`
Gets all record IDs owned by a specific address.

### `getTotalRecords()`
Returns the total number of registered records.

## 🌐 Network Configuration

**Celo Alfajores Testnet**
- Chain ID: 44787 (0xaef3)
- RPC URL: https://alfajores-forno.celo-testnet.org
- Explorer: https://alfajores.celoscan.io/

## 🎨 Design Features

- **Typography-focused**: Clean Inter font family
- **Color Palette**: White backgrounds, slate text, gold accents (#D4AF37)
- **Responsive**: Mobile-friendly design with Tailwind CSS
- **Certificate-style**: Professional document presentation for registrations
- **Smooth Animations**: Fade-in effects and hover transitions

## 🔒 Security Considerations

- All data is stored on-chain and immutable
- Owner address is automatically captured from connected wallet
- Timestamps are blockchain-verified
- Input validation on both frontend and smart contract

## 📝 Notes

- This is an MVP (Minimum Viable Product) for demonstration purposes
- For production use, consider adding IPFS integration for large content storage
- The current implementation stores descriptions on-chain; for large documents, store only hashes
- Consider implementing access control for sensitive records

## 🐛 Troubleshooting

**Wallet won't connect**
- Ensure MetaMask is installed
- Check that you're on the correct network (Celo Alfajores)

**Transaction fails**
- Ensure you have enough CELO testnet tokens
- Check that the contract address is correctly configured

**Record not found when verifying**
- Ensure the Registration ID is correct
- Wait for transaction confirmation before verifying

## 📄 License

MIT License - Feel free to use this project for your own purposes.

---

**Built with ❤️ on Celo**