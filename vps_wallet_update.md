# SINOVATE InfinityNode Update And Sync Guide

## If running Infinity Node, stop it.
``sudo systemctl stop sinovate.service``

## install unzip package
``sudo apt update && sudo apt install unzip``

## remove old files and folders (Write this entire code on one line.)
``rm -rf ~/.sin/{blocks,chainstate,debug.log,mnpayments.dat,mncache.dat,banlist.dat,peers.dat,netfulfilled.dat,governance.dat,fee_estimates.dat}``

## download latest bootstrap archive
``wget -O ~/bootstrap.zip https://service.sinovate.io/mainnet/latest/bootstrap.zip``

## unzip the bootstrap archive
``unzip ~/bootstrap.zip``

## move bootstrap files
``mv -t ~/.sin ~/bootstrap/blocks ~/bootstrap/chainstate``

## remove unnecessary files
``rm -rf ~/{bootstrap,bootstrap.zip}``

## Update Latest Wallet
``wget -O daemon.tar.gz https://github.com/SINOVATEblockchain/sinovate/releases/latest/download/daemon.tar.gz``
``tar -xzvf daemon.tar.gz``
## Check Version
``./sin-cli -version``
## reboot infinitynode
``sudo reboot``
