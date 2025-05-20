# 0gstorage-node-setup
Setup and configuration guide for 0gstorage node

## Step 1: Update dan Install Dependencies

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install curl wget git screen unzip jq -y
```
## Step 2: Download dan Jalankan Script

```bash
wget https://raw.githubusercontent.com/WillEnyong/0gstorage/main/run.sh
chmod +x run.sh
./run.sh
#Klik 1 auto fast
#Setelah itu Import Private Key
```
Step 3: Update Konfigurasi

```bash
systemctl stop zgs

sed -i 's/^flow_contract *= *.*/flow_contract = "0x5f1D96895e442FC0168FA2F9fb1EBeF93Cb5035e"/' $HOME/0g-storage-node/run/config.toml
sed -i 's/^mine_contract *= *.*/mine_contract = "0xB0F6c3E2E7Ada3b9a95a1582bF6562e24A62D334"/' $HOME/0g-storage-node/run/config.toml
sed -i 's/^reward_contract *= *.*/reward_contract = "0xdf758Bd14306482DeCbeF186eC6f18e4e79aaaE6"/' $HOME/0g-storage-node/run/config.toml

rm -rf $HOME/0g-storage-node/run/db
```
Step 4: Start Ulang Node

```bash
systemctl start zgs
```
Step 5: Cek Log Node
```bash
tail -f ~/0g-storage-node/run/log/zgs.log.$(TZ=UTC date +%Y-%m-%d)
