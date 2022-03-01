If you want to have two masternodes on single VPS, you can follow the next steps. **A Floating IP is needed.** Login at your VPS, then:
```
# create a new user
sudo adduser node-02
sudo usermod -aG sudo node-02

# login as new user (and change shell color)
sudo su node-02
cd
echo 'PS1="\[\033[38;5;208m\]\u\[$(tput sgr0)\]\[\033[38;5;15m\]@\[$(tput sgr0)\]\[\033[38;5;10m\]\h\[$(tput sgr0)\]\[\033[38;5;15m\]:\[$(tput sgr0)\]\[\033[38;5;6m\][\w]:\[$(tput sgr0)\]\[\033[38;5;15m\] \[$(tput sgr0)\]"' >> .bashrc

# CTRL+D and "sudo su node-02" again to see the applied colors

# download latest SIN daemon
wget -O daemon.tar.gz https://github.com/SINOVATEblockchain/SIN-core/releases/latest/download/daemon.tar.gz
tar -xzvf daemon.tar.gz && rm daemon.tar.gz

# create config file
mkdir ~/.sin && nano ~/.sin/sin.conf
```

```
# COPY/PASTE
# PAY ATTENTION TO MODIFY WHERE INDICATE WITH "EDIT"
debug=0
rpcuser=EDIT
rpcpassword=EDIT
rpcallowip=127.0.0.1
listen=1
server=1
daemon=1
port=20970
rpcport=20972
logintimestamps=1
maxconnections=256
bind=EDIT_WITH_FLOATING_IP
masternode=1
externalip=EDIT_WITH_FLOATING_IP:20970
masternodeprivkey=EDIT
addnode=46.101.152.7:20970
addnode=104.248.17.3:20970
addnode=139.59.139.105:20970
addnode=209.97.153.68:20970
addnode=192.99.19.160:20970
addnode=147.135.15.167:20970
addnode=159.89.194.138:20970
addnode=47.88.175.216:20970
```

If using Hetzner VPS, create a floating IP and edit your VPS network:

```
# add floating ip
sudo nano /etc/network/interfaces.d/60-my-floating-ip.cfg

# add the following lines modifying your.Float.ing.IP
auto eth0:1
iface eth0:1 inet static
    address your.Float.ing.IP
    netmask 32
    
# restart networking
sudo service networking restart
```

If you want to boost up, use the bootstrap:
```
sudo apt update && sudo apt install unzip
wget -O ~/bootstrap.zip https://github.com/SINOVATEblockchain/SIN-core/releases/latest/download/bootstrap.zip
unzip ~/bootstrap.zip
mv -t ~/.sin ~/bootstrap/blocks ~/bootstrap/chainstate
rm -rf ~/{bootstrap,bootstrap.zip}
```

```
# create service to start sind on VPS boot
sudo nano /etc/systemd/system/sinovate02.service
```

```
[Unit]
Description=sinovate02 service
After=network.target
[Service]
User=node-02
Group=node-02

Type=forking

ExecStart=/home/node-02/sind -daemon -conf=/home/node-02/.sin/sin.conf -datadir=/home/node-02/.sin
ExecStop=-/home/node-02/sin-cli -conf=/home/node-02/.sin/sin.conf -datadir=/home/node-02/.sin stop

Restart=always
PrivateTmp=true
TimeoutStopSec=60s
TimeoutStartSec=10s
StartLimitInterval=120s
StartLimitBurst=5

[Install]
WantedBy=multi-user.target
```

```
# enable service
sudo systemctl daemon-reload
sudo systemctl enable sinovate02

# start service 
sudo service sinovate02 start

# control status
watch -n 2 '~/sin-cli getblockcount && ~/sin-cli masternode status && ~/sin-cli mnsync status && ~/sin-cli -getinfo'
```

as usual, when finished sync, and your local `infinitynode.conf` is correctly set, start alias form local wallet