## Update Guide for Mandatory Network Upgrade


- Login to VPS as node user
- The node directory is assumed to be `/home/$NODEUSER/.sin`

```
sudo apt update && sudo apt install unzip
```

```
wget -q --show-progress --no-check-certificate https://github.com/SINOVATEblockchain/sinovate/releases/latest/download/download_bootstrap.sh -O download_bootstrap.sh
```
```
chmod +x download_bootstrap.sh
```
```
sudo systemctl stop sinovate.service
```
```
wget -q --show-progress --no-check-certificate https://github.com/SINOVATEblockchain/sinovate/releases/latest/download/daemon.tar.gz -O daemon.tar.gz
```
```
tar -xzf daemon.tar.gz -C /home/$(whoami)
```
```
./download_bootstrap.sh
```
- At this stage, the script will download and apply the bootstrap file for you. Once all is well, you can restart the node with the following command.

```
sudo systemctl start sinovate.service
```
:warning: Then you must send at least 50 more SINs to the VPS SIN address. :warning:
