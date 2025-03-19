# How-to-run-a-t3rn-V2-Node


Running a **t3rn V2 node** allows you to participate in the t3rn network, a multi-chain execution protocol designed for secure and interoperable smart contract execution. This guide will walk you through setting up your node, claiming testnet tokens, and configuring your environment. Let’s get started!  


## **What is t3rn?**  
t3rn is a blockchain protocol that enables secure and interoperable smart contract execution across multiple chains. By running a t3rn node, you contribute to the network’s decentralization and earn rewards in the form of **BRN tokens**.  


## **Step 1: Set Up a VPS**  
To run a t3rn node, you’ll need a Virtual Private Server (VPS). Here’s how to get started:  

1. **Choose a VPS Provider**:  
   We recommend using **CLOUP VPS 2 on Contabo** for its affordability and reliability.  
   [Get Contabo VPS Here]([https://www.tkqlhce.com/click-101114590-13484397](https://www.tkqlhce.com/5k117cy63y5LNMNPTTSSSLNRMOOPST?sid=medium)).  

2. **Select Ubuntu 22.04**:  
   During setup, choose **Ubuntu 22.04** as your operating system. This version is stable and widely supported.  


## **Step 2: Connect to Your VPS**  
Once your VPS is ready, connect to it using SSH:  

```bash  
ssh root@<IP_OF_YOUR_VPS>  
```  
Replace `<IP_OF_YOUR_VPS>` with your VPS’s actual IP address.  


## **Step 3: Claim Testnet Faucet Tokens**  
To interact with the t3rn testnet, you’ll need testnet tokens. Follow these steps:  

1. **Claim BRN Tokens**:  
   Visit the t3rn faucet and claim at least **0.1 BRN**:  
   [t3rn Faucet](https://b2n.hub.caldera.xyz/).  
   *Tip: Use a VPN to claim tokens on multiple addresses.*  

2. **Claim ETH on Testnets**:  
   You’ll also need ETH on the following testnets:  
   - **Arbitrum Sepolia**  
   - **Optimism Sepolia**  
   - **Base Sepolia**  

   Use these faucets to claim ETH:  
   - [QuickNode Faucet](https://faucet.quicknode.com/arbitrum/sepolia)  
   - [Chainlink Faucet](https://faucets.chain.link/arbitrum-sepolia)  
   - [Bware Labs Faucet](https://bwarelabs.com/faucets/arbitrum-sepolia)  
   - [Alchemy Faucet](https://www.alchemy.com/faucets/ethereum-sepolia)  
   - [MetaMask Faucet](https://docs.metamask.io/developer-tools/faucet/)  
   - [Google Cloud Faucet](https://cloud.google.com/application/web3/faucet/ethereum/sepolia)  

3. **Bridge ETH Between Testnets**:  
   Use these tools to move ETH between testnets:  
   - [Testnet Bridge](https://testnetbridge.com/sepolia)  
   - [SuperBridge](https://testnets.superbridge.app/base-sepolia)  


## **Step 4: Configure Your Node**  
Now that you’ve claimed your tokens, it’s time to set up your t3rn node.  

### **1. Update Your System**  
Start by updating your system:  
```bash  
sudo apt update && sudo apt upgrade -y  
```  

### **2. Install Screen**  
Screen allows you to run processes in the background. Install it with:  
```bash  
apt install screen  
```  

### **3. Download t3rn Binaries**  
Download the t3rn executor binaries:  
```bash  
wget https://github.com/t3rn/executor-release/releases/download/v0.53.1/executor-linux-v0.53.1.tar.gz  
```  

### **4. Extract the Binaries**  
Unzip the downloaded file:  
```bash  
tar -xvzf executor-linux-v0.53.1.tar.gz  
```  

### **5. Navigate to the Executor Directory**  
Move into the extracted directory:  
```bash  
cd executor  
```  

### **6. Create a Screen Session**  
Start a new Screen session to keep your node running in the background:  
```bash  
screen -S t3rn  
```  

### **7. Configure Environment Variables**  
Set up your node environment by exporting the following variables:  

```bash  
export ENVIRONMENT=testnet  
export LOG_LEVEL=debug  
export LOG_PRETTY=false  
export EXECUTOR_PROCESS_BIDS_ENABLED=true  
export EXECUTOR_PROCESS_ORDERS_ENABLED=true  
export EXECUTOR_PROCESS_CLAIMS_ENABLED=true  
export EXECUTOR_PROCESS_ORDERS=true  
export EXECUTOR_PROCESS_CLAIMS=true  
export EXECUTOR_MAX_L3_GAS_PRICE=100  
export PRIVATE_KEY_LOCAL=<YOUR_WALLET_PRIVATE_KEY>  
export ENABLED_NETWORKS='arbitrum-sepolia,base-sepolia,optimism-sepolia,l2rn'  
export RPC_ENDPOINTS='{  
    "l2rn": ["https://b2n.rpc.caldera.xyz/http"],  
    "arbt": ["https://arbitrum-sepolia.drpc.org", "https://sepolia-rollup.arbitrum.io/rpc"],  
    "bast": ["https://base-sepolia-rpc.publicnode.com", "https://base-sepolia.drpc.org"],  
    "opst": ["https://sepolia.optimism.io", "https://optimism-sepolia.drpc.org"],  
    "unit": ["https://unichain-sepolia.drpc.org", "https://sepolia.unichain.org"]  
}'  
export EXECUTOR_PROCESS_PENDING_ORDERS_FROM_API=false  
```  

Replace `<YOUR_WALLET_PRIVATE_KEY>` with your wallet’s private key.  

### **8. Start the Node**  
Navigate to the `bin` directory and start the node:  
```bash  
cd executor/bin  
./executor  
```  

### **9. Detach from the Screen Session**  
To leave the Screen session without stopping the node, press `CTRL+A+D`.  

---

## **Step 5: Monitor Your Node**  
Once your node is running, you can monitor its activity and rewards.  

### **1. Check BRN Rewards**  
Visit the t3rn rewards dashboard to check your BRN balance:  
[t3rn Rewards Dashboard](https://unlock3d.t3rn.io/rewards).  

### **2. View Logs**  
To check your node logs, reattach to the Screen session:  
```bash  
screen -r t3rn  
```  
Detach again with `CTRL+A+D` when done.  

---

## **Need Help?**  
If you encounter any issues or have questions, join the t3rn community:  
- **Discord**: [t3rn Discord](https://discord.gg/D5p9rmUexr).  
- **Twitter**: Follow [@allcryptoguides](https://x.com/allcryptoguides) for updates and support.  
- **Telegram**: Join [@leksidedrops](https://t.me/leksidedrops) for updates and support.  

---

## **Disclaimer**  
This guide is for educational purposes only and does not constitute financial advice. Always conduct your own research before participating in blockchain networks.  

---

**Thank you for reading!** By following this guide, you’re now ready to run your own t3rn V2 node and contribute to the future of multi-chain interoperability. Happy node running!  

---  
*Keywords: t3rn V2 node, t3rn testnet, how to run a t3rn node, t3rn rewards, BRN tokens, multi-chain execution, t3rn faucet, blockchain node setup.*
