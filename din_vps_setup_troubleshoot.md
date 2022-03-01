# Self-hosted node troubleshooting guide.

  <br>

# 1.  Node doesn't have rewards.
    
  <br>  

1.2 Make sure wallet daemon started (./sind). Maybe daemon crashed? This can be in several options, low or peak level RAM, for example.

<br>

1.3 Make sure to be able to ping node IP from home PC.
  
  <br>
  
1.3.1 Does node have the current blockchain block height? (./sin-cli getblockcount)

<br>

1.4 Turn off VPS firewall or IPtables, not the best option but if you don't know how to config - turn it off, no coins or essential data inside in case of a hack.
  
<br>
1.4.1. Node port must be exactly 20970, and you must check the connection to this port, with telnet for example.

<br>

1.5 We have nodes count increasing every day, and reward can be "moved" in time, 1,5,12,24 hours. (for example in the transaction History tab you can see reward 1 December 3:00 pm and next reward 3 December but 2:00 am, please pay attention.)

<br>

1.6 If you do not have a reward today in blockchain circumstances, someone also will not have it the next day or later, to keep inflation low.

<br>

1.7 Make sure to send 3 sin to node address (address generated with keys, ./sin-cli getbalance, must be 3 or more, no reason to make it more than 3)

<br>

1.7.1 Make sure you did import key (./sin-cli importprivkey <generated key>)

<br>

1.8 VPS hardware - make sure VPS is very responsive. This means all resources must reply in ~100 milliseconds, ls - folder list for disk system, netstat - for the network system. Wallet daemon must not use a lot of swap. VPS must reply to incoming connections in 100 milliseconds. Monthly VPS trafic around 100 Gb - if provider limit VPS bandwidth before 100 Gb this maybe isuue. 

<br>

1.9 We do not support and do not troubleshoot several nodes in 1 VPS. (because 0.0.0.0 if you know what this means)

<br>

1.10 Nodes must have IPv4 and IPv6. Make sure you can ping google.com from both interfaces. (ping4 google.com and ping6 google.com) Some VPS providers do not activate IPv6 from the box.

<br>

# 2. Can't start node (Not capable Infinitynode)

<br>

2.1 Make sure you did updatemeta from GUI control wallet, WIN wallet, MAC wallet, Linux Wallet. (infinitynodeupdatemeta)

<br>

2.2 If you did updatemeta two times with the same node key, other IP or owner address it will not work. Node key must be changed (generated) every updatemeta use. Wait for 55 confirmations for updatemeta transaction.

<br>

2.3 If you did updatemeta with the wrong owner address, you would not have an error, but the node will not start.

<br>
