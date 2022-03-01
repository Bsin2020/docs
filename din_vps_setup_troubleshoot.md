# Self-hosted node troubleshooting guide.

  

1.  **Node doesn't receive rewards.**

  

1.2 Make sure wallet daemon is started (./sind), or it may be a daemon crash. Also, make sure there isn't low or peak-level RAM.

  

1.3 Make sure to be able to ping node IP from home PC.

  

1.3.1 Does node have the current blockchain block height? (./sin-cli getblockcount)

  

1.4 Turn off VPS firewall or IPtables, not the best option, but if you don't know how to config - turn it off, no coins or essential data is inside in case of a hack.

  

1.4.1. Node port must be exactly 20970, and you must check the connection to this port, for example, with telnet.

1.5 We have nodes count increasing every day, and reward can be "moved" in time, 1,5,12,24 hours. (for example, in the transaction history tab, you can see the reward received on 1 December at 3:00 pm and the following reward on 3 December but at 2:00 am, please pay attention.)

  

1.6 If you do not have a reward today in blockchain circumstances, someone else will not have it the next day or later to keep inflation low.

  

1.7 Make sure to send 3 SIN to the node address (address is generated with keys, ./sin-cli getbalance, must be at least 3 SIN.

  

1.7.1 Make sure you did import key (./sin-cli importprivkey )

  

1.8 **VPS hardware** - make sure VPS is very responsive. This means all resources must reply in ~100 milliseconds, ls - folder list for disk system, netstat - for the network system. Wallet daemon must not use a lot of swaps. VPS must reply to incoming connections in 100 milliseconds. Monthly VPS traffic around 100 Gb - if the provider limit VPS bandwidth is less than 100 Gb, this may be an issue.

  

1.9 We do not support and do not troubleshoot several nodes in 1 VPS. (because of 0.0.0.0 if you know what this means)

  

1.10 Nodes must have IPv4 and IPv6. Make sure you can ping google.com from both interfaces. (ping4 google.com and ping6 google.com) Some VPS providers do not activate IPv6 from the box.

  

2- **Can't start node (Not capable Infinitynode)**

  

2.1 Make sure you did "updatemeta" from GUI control wallet, WIN wallet, MAC wallet, Linux Wallet. (infinitynodeupdatemeta)

  

2.2 If you did updatemeta two times with the same node key, other IP, or owner address, it would not work. This is because the node key must be changed (generated) every updatemeta use. Wait for 55 confirmations for a updatemeta transaction.

  

2.3 If you did updatemeta with the wrong owner address, you would not have an error, but the node will not start.
