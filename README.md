# Privasea-AI-Node-Run-Full-Guide

## Need Some Software Requirements for PC Users

1. For Windows Install WSL - https://learn.microsoft.com/en-us/windows/wsl/install#install-wsl-command

2. For Windows Install Ubuntu after Installing WSL - https://apps.microsoft.com/detail/9PDXGNCFSCZV?hl=en-us&gl=IN&ocid=pdpshare

3. For macOS If you have Installed Homebrew (https://brew.sh/) to manage packages on OS X,
run this command to install Git.
```
brew install git
```
4. Install Docker - https://www.docker.com/products/docker-desktop/

   🍀For VPS (Additional Only for VPS Users to Download Docker)
```
sudo apt update -y
```
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
```
```
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
```
sudo apt update -y
```
```
apt-cache policy docker-ce
```
```
sudo apt install docker-ce -y
```
```
sudo usermod -aG docker ${USER}
su - ${USER}
groups
```

## Need Some Hardware Requirements [Check Out](system-requirements.md)

1️⃣ Pull Docker Image
```
docker pull privasea/acceleration-node-beta:latest
```

2️⃣ Create the program running directory and navigate to it
```
mkdir -p  /privasea/config && cd  /privasea
```

3️⃣ Get the keystore file
```
docker run --rm -it -v "$HOME/privasea/config:/app/config" privasea/acceleration-node-beta:latest ./node-calc new_keystore
```

Note: The program will prompt you to enter a password, please remember this password for future use. The generated keystore file will have a corresponding node address, Please keep it properly to avoid losing it, it will be used in the dashboard configuration.
![image (1)](https://github.com/user-attachments/assets/439e3fc2-15a3-4618-a85c-d68a4dcc47ea)

4️⃣ Move the keystone file to a new file for backup
```
mv $HOME/privasea/config/UTC--* $HOME/privasea/config/wallet_keystore
```

5️⃣ Link node address and reward address

Alchemy Faucet — https://www.alchemy.com/faucets/arbitrum-sepolia

QuickNode Faucet — https://faucet.quicknode.com/arbitrum

1. Go to Privasea Dashboard - https://deepsea-beta.privasea.ai/privanetixNode

2. Set-up your Privanetix Node

6️⃣ Start the Node
```
KEYSTORE_PASSWORD=ENTER_YOUR_KEYSTORE_PASSWORD && docker run -d --name privanetix-node -v "$HOME/privasea/config:/app/config" -e KEYSTORE_PASSWORD=$KEYSTORE_PASSWORD privasea/acceleration-node-beta:latest
```

Note: Replace your ENTER_YOUR_KEYSTORE_PASSWORD with your Keystore Password, you already provided in 3rd steps

7️⃣ Check your dashboard to Showing Online

8️⃣ To get the reward you have to stake some TPRAI on your node

1. Just Click on the “Privasea DeepSea Beta Faucet” to get TPRAI faucet
2. Then Click on ‘My Staking’ > After that, your node details will be displayed > Just click on ‘Details
3. Then Click on the ‘Stake’ button > Put the amount & Staked it

## 🔶For Next Day Run This Command

#1 Open docker 1st 

#2 Now Open WSL and Put this Command 
```
sudo mkdir -p  /privasea/config && cd  /privasea
```
```
KEYSTORE_PASSWORD=ENTER_YOUR_KEYSTORE_PASSWORD && docker run -d --name privanetix-node -v "$HOME/privasea/config:/app/config" -e KEYSTORE_PASSWORD=$KEYSTORE_PASSWORD privasea/acceleration-node-beta:latest
```

Note: Replace your ENTER_YOUR_KEYSTORE_PASSWORD with your Keystore Password, you already provided in 3rd steps
