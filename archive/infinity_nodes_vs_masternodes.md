# A deep dive into Masternode security and how this has been greatly improved

# Introduction

SINOVATE is a cryptocurrency that recently had its first-year anniversary of the launch of its blockchain. They are focused on bringing new innovations to the space with a talented team of developers and strong community.

It uses both proof-of-work (PoW) consensus, focussed on being ASIC and FPGA resistant but also has another layer known as the Infinity Chain that interlinks and is run by the masternode network, known as Infinity Nodes. It currently uses a brand-new algorithm called X25X at the proof-of-work layer and is committed to constantly evolve in order to prevent ASICs being present on the network.

It has one of the fastest transaction speeds at around 533 transactions per second with the FlashSend feature utilizing the Infinity Node layer. It also brings other components and features such as governance voting, data storage (IDS) and transmission capabilities similar to IPFS and asset creation synonymous with the likes of Ravencoin, along with other features.

# Infinity Nodes vs. Masternodes

# **Inflation & Network Performance**

The concept of masternodes has been used in many other projects but they suffer from some serious unintended consequences. Inflation is one of the biggest issues that challenge investors. With a high rate of return often investors are attracted to a project, but these lead to inflation and there is no real incentive for the user to maintain their node over time, leading to degradation of the network.

# The game changing innovation for Masternodes: Infinity Nodes

Infinity Nodes operate in a different way, that reduces inflation and promote the smooth running of a healthy network. When a new node is created, the coins used to create it are burned, removing them from the supply using its unique Proof-of-Burn (POB) feature.

This uses a new transaction type called a BurnTx. This transaction is stored in the regular blockchain for easy verification of a node and start and end of its validity period.

Transaction fees for utilizing the features of Sinovate are also burnt and these can also be viewed at the “B[urn Address](http://explorer.sinovate.io/address/SinBurnAddress123456789SuqaXbx3AMC)”.

A node has a lifespan of around a year. However, over the lifetime of the node, the holder will instead be rewarded with their initial coins plus a guaranteed interest of 22%. This can be higher depending on the number of nodes locked up in the network at any one time.



![](assets/img/infinity_nodes_vs_masternodes/1.png)

This incentivizes users to maintain nodes over their lifetime, while controlling inflation and allowing for a smooth operating blockchain network.

Incentivising the network to lock up nodes for a long period of time, unlike other masternodes where node holders can choose to stop their node at any time, allows for other features such as IDS, the SINOVATE data storage solution.

# Masternode vs. Infinitynode Security



![](assets/img/infinity_nodes_vs_masternodes/2.png)

Readers may have heard of attacks that can affect proof-of-work coins like Bitcoin such as 51% or Genesis attacks. However, coins that use masternodes also have their own attack vectors that can be exploited.

Let’s dive into this….

# Sybil Attacks!

![](assets/img/infinity_nodes_vs_masternodes/3.png)

Sybil attacks are something that occur around the world daily. It is basically where a user will try to take over a peer-to-peer network by creating a vast amount of network identities or nodes to exert an unduly large influence.

An example today on social media are the large amount of fake accounts created to try to subvert debates in certain directions. A network’s ability to fight off these types of attacks are largely down to the cost to create or join the network with a new identity. While these attacks are an issue on social media, it could be devastating to a blockchain if it were to happen. An attacker’s chances of success and what they can do largely depends on how much they could dominate the network.

In Bitcoin and other proof-of-work coins, if an attacker were able to compromise the network with a Sybil attack, they would have far reaching powers over the network activity.

For example:

-   The attacker could only relay blocks they create, allowing double spend attacks.
-   They could refuse to relay blocks and transactions for everyone, effectively shutting down the network.

Proof-of-work makes this very difficult to do as the costs to join the network (by mining) are prohibitive and to create enough nodes to execute would be uneconomical.

**Masternodes have their own attack vectors though.**

To attack the system using a Sybil attack, an attacker must own enough masternodes to guarantee that they will form the selected group to process transactions. If they are able to do this, it would mean they would be able to execute a double spend transaction or other attacks as above.

On usual masternode networks , the attacker must only lock up the currency needed while they execute the attack. Afterwards they are freely able to unlock their nodes and sell the currency. This is not possible with SINOVATE.

The cost in acquiring enough SIN, bearing in mind liquidity, price and VPS requirements make this prohibitive in a similar way to proof-of-work.

# Transaction Locking Race Attack

In this type of attack, the attacker would send two competing blocks to the network at the same time, one to themselves and one to a third party. The network would be divided in consensus about which is valid.

The attacker must be able to maintain the node throughout this period and beyond or face losing their coins, unlike with other iterations where they are able to withdraw funds after the attack.

With SINOVATE, once all nodes in the group have returned their transactions, a non-consensus would be identified, and the transaction would resort to the proof-of-work chain.

# Finney Attack


![](assets/img/infinity_nodes_vs_masternodes/4.png)

A Finney attack is thus named as was first suggested by Hal Finney, the first known receiver of Bitcoin from Satoshi. In this attack, malicious actors also try to send a transaction to themselves by using the proof-of-work network to execute.

They mine blocks normally, waiting to find one in which they have sent a transaction to themselves. Instead of broadcasting, they then make a transaction on the masternode network for goods which must be completed before the next block is produced. Once the goods have been received, the mined block is broadcast which invalidates the masternode transaction.

The SIN protocol prevents this by being able to recognize the difference in transaction locks between proof-of-work and masternode consensus and when all members of the group have validated conflicting blocks rejected.

Again, the attacker must maintain Infinity Nodes for the complete lifetime or face losing these funds.


![](assets/img/infinity_nodes_vs_masternodes/5.png)

# Conclusion

The proof-of-burn mechanism used when locking up an Infinity Node brings a twofold innovation to the cryptocurrency space. With the coins being removed from supply and burnt forever, this leads to a firm control on inflation to benefit Infinity Node holders and incentivise the smooth running of the network.

Consequently, the costs for an attacker to try to subvert the SINOVATE network are greatly increased above previous masternode iterations, leading to a new standard in masternode, or rather, Infinity Node security.
