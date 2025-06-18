
# Cysic Verifier Node Setup Guide (GCP Friendly)

This guide helps you set up a Cysic Verifier Node on a Google Cloud Platform (GCP) VM. Based on the [official Cysic documentation](https://timemeansalots-organization.gitbook.io/docs.cysic.xyz/tutorial-docs/how-to-run-a-verifier-node).

---

## 📦 Requirements

### ✅ Recommended GCP VM Specs
- OS: Ubuntu 22.04 LTS
- RAM: 4 GB minimum (8 GB preferred)
- vCPUs: 1+
- Disk: 10GB Standard Persistent Disk

---

## 🔓 GCP Firewall Rules

Open the following ports in your GCP VM:

### Add via GCP Console:
1. Go to **VPC Network > Firewall Rules**
2. Click **Create Firewall Rule**
3. Name: `cysic-node-ports`
4. Targets: **All instances in the network**
5. Source IP Ranges: `0.0.0.0/0`
6. Protocols & ports:
   - Check **Specified protocols and ports**
   - TCP: `8545,30303`
   - UDP: `30303`
7. Save

---

## ⚙️ Installation Steps

### 1. Update and install dependencies
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install curl git unzip screen -y
```

### 2. Clone Cysic verifier repo and add your evm address at end YOUR_EVM_ADDRESS
```bash
# replace 0x-Fill-in-your-reward-address-here with your reward address below
curl -L https://github.com/cysic-labs/cysic-phase3/releases/download/v1.0.0/setup_linux.sh > ~/setup_linux.sh && bash ~/setup_linux.sh YOUR_EVM_ADDRESS
```

### 3. Run inside a screen session
```bash
screen -S cysicnode
```

### 4. Run the Verifier Node
```bash
cd ~/cysic-verifier/ && bash start.sh
```
![image](https://github.com/user-attachments/assets/ffe5ef8f-4a5f-4036-9be1-5eb43333cb79)

---

## 🧠 Useful Commands

| Command | Description |
|--------|-------------|
| `screen -r cysicnode` | Reattach to the running node |
| `screen -ls` | List all screen sessions |
| `CTRL + A + D` | Detach screen without stopping node |

---

## 🔗 Official Links

- Official Guide: [GitBook](https://timemeansalots-organization.gitbook.io/docs.cysic.xyz/tutorial-docs/how-to-run-a-verifier-node)
- Cysic Twitter: [@cysic_xyz](https://twitter.com/cysic_xyz)
- Discord: [Cysic Discord](https://discord.gg/cysic)

---
