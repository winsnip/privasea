# Privasea Privanetix Node

## Minimum System Requirements

| Component         | Requirement                |
|--------------------|----------------------------|
| **Operating System (OS)** | Ubuntu (Recommended)       |
| **CPU Architecture**      | amd64 (x86 architecture)   |
| **Storage**               | 100GB available storage   |
| **Memory (RAM)**          | 4GB RAM                  |
| **Processor**             | 6 cores                  |

![Ubuntu](https://img.shields.io/badge/Ubuntu-22.04-orange)  
![Docker](https://img.shields.io/badge/Tool-Docker-blue)  
![Node Status](https://img.shields.io/badge/Node%20Status-Active-brightgreen)

> You can buy VPS from [Contabo](https://contabo.com/en/vps/)) using cryptocurrency.

---

## Installation

### Step 1: Install Docker
First, install Docker in your system if it is not already installed by running the following command:
```bash
source <(wget -O - https://raw.githubusercontent.com/winsnip/privasea/refs/heads/main/docker.sh)
```
Add the current user to the Docker group:

```
sudo groupadd docker && sudo usermod -aG docker $(whoami) && newgrp docker
```

### Step 2: Pull Docker Image
Pull the Docker image using the following command:
```
docker pull privasea/acceleration-node-beta:latest
```
waiting 20 secound

### Step 3: Create a Directory

Create a directory for Privasea and navigate into it:
```
mkdir -p ~/privasea/config && cd ~/privasea
```

### Step 4: Generate a New Wallet Keystore
Run the following command to generate a new wallet keystore:
```
docker run --rm -it -v "$HOME/privasea/config:/app/config" privasea/acceleration-node-beta:latest
```
> Note: You need to input a password during this step. Save this password securely for future use. Also, note down the node address displayed during this process.

### Step 5: Move the Keystore File
Move the generated keystore file to a specific location:
```
mv $HOME/privasea/config/UTC--* $HOME/privasea/config/wallet_keystore
```

### Step 6: Configure Privanetix Node

Visit the [Privanetix Dashboard](https://deepsea-beta.privasea.ai/privanetixNode)) Dashboard to configure your node:

1. Connect a wallet to receive rewards.

2. Enter the node address you noted earlier.

3. Set up the node name and commission (e.g., 1%).

4. Click Set up my node.

#### Step 7: Start the Node
Run the following command to start your Privasea Privanetix Node. Replace ENTER_YOUR_KEYSTORE_PASSWORD with the password you used earlier:
```
KEYSTORE_PASSWORD=ENTER_YOUR_KEYSTORE_PASSWORD && docker run -d --name privanetix-node -v "$HOME/privasea/config:/app/config" privasea/acceleration-node-beta:latest
```
