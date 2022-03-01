## Verify BestBlockHash
To verify your Infinity Node is correctly synced with the blockchain, login to the VPS where the Infinity Node is running and send the following command:
```bash
~/sin-cli getbestblockhash && curl -s "https://blockbook.sinovate.io/api/v2" | grep -Po '"bestBlockHash":.*?[^\\]",' | cut -c "18-" | cut -d \" -f 1
```
If you receive two lines exactly the same, your Infinity Node is correctly synced.

## Manual resync
In case the blockchain data of your Infinity Node get corrupted, you need to resync it from scratch with `-reindex` flag

Login to your VPS and send the following commands:
```bash
crontab -r
sudo systemctl stop sinovate.service
rm -rf ~/.sin/{blocks,chainstate,debug.log,mnpayments.dat,mncache.dat,banlist.dat,peers.dat,netfulfilled.dat,governance.dat,fee_estimates.dat}
~/sind -reindex
watch -n 5 '~/sin-cli getblockcount && ~/sin-cli masternode status && ~/sin-cli mnsync status'
```

Wait until you get the following message. (It may take up to 30 minutes. CTRL+C to exit monitoring)

```bash
"AssetName": "MASTERNODE_SYNC_FINISHED"
```

Your Infinity Node is now synced.
