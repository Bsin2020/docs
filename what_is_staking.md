 
# Understanding Staking

## **1.  Prerequisites**

We recommend you to read carefully the following articles to understand the Proof-of-Stake (PoS) consensus and the different in-depth technical overviews made by Giaki3003, SINOVATE Blockchain lead:

**Introduction**: https://academy.binance.com/en/articles/proof-of-stake-explained
**In-Depth Technical Overview**: https://giaki3003.tech/proof-of-stake-by-giaki3003-part-1

We will resume here the essential information to guide you in the SINOVATE Proof-of-Stake solution called 4th generation of Proof-of-Stake (PoS4). 

## **2.  What is Proof-of-Stake?**

A PoS algorithm is mainly a peer-to-peer solution based on the “stake” of peers to reach a consensus for validating blocks. A “stake” is simply the fact of having a native wallet with native coins of the blockchain that are allocated to validate the blocks of transactions. In this way, a SIN hodler wins a reward if its stake successfully confirms a new block. 
PoS shows a considerable energy efficiency compared to Proof-of-Work solutions and its implementation in the SINOVATE blockchain guarantees a green decentralized data storage. (https://cointelegraph.com/news/tezos-blockchain-notes-power-savings-after-pos-switch-pwc-report)
Compared to Byzantine Fault Tolerance (BFT) solutions, this consensus mechanism allows the blockchain a fair scalability with a real decentralization and security by trusting the holders of the SINOVATE coins. Anyone can participate in this consensus as a self-governed peer and do not need to trust a third-party service. Of course, third-party services can ease the process for individuals and businesses that cannot respect the specific constraints of PoS4 based on UTXOs and permanent Internet connection.

## **3.  What is an UTXO?**

You have probably seen this abbreviation in different discussions about staking. You can read the article in the following: 
https://www.investopedia.com/terms/u/utxo.asp#:~:text=A%20UTXO%20is%20the%20amount,and%20end%20of%20each%20transaction

Basically, UTXO means then an unspent transaction output (UTXO). When a user A sends 500 coins to a user B to an address B1, then it creates a UTXO in the address B1 with an amount of 500 SIN coins. Hence, if user A does again a transaction to user B to the address B1 of 300 SIN coins. Then, the address B1 finally has 2 UTXOs: One of 500 SIN coins and one of 300 SIN coins.

## **4.  What is the Fourth-Generation of Proof-of-Stake (Pos4)?** 

The PoS4 development is a complex integration requiring different steps of development. The first step released in April 2022 was to have a stable association between the PoW mechanism with the X25X algorithm and to implement a novel feature called LockStake. The principle uses the UTXO of addresses of all the wallets that participate in the network consensus. 
Additionally, two safety guards have been added to the PoS4. The first is that the UTXO maturity must be at least 14,400 blocks (around 10 days) to be eligible as a staking validator. This reduces considerably the attack surface of an already complex vector. The second is the coinbase validation from a PoS block which is 1,440 blocks (around 1 day). This means all the validators (PoS validator + InfinityNodes) must wait 1 day to have a mature reward. If an attack occurs, the spend of this attack in the marketplace would have to wait 1 day.

## **5.  What are the benefits?**

The major benefit of PoS4 compared to all the other staking solutions is the reward distribution does not contribute to whales directly. Indeed, as the UTXO is locked for 10 days, it makes it unreliable to have coins centralized on one UTXO. Hence, a whale would have to split its stake into UTXO staking chunks that allows a fair reward accumulation. For instance, a theoretical supply of 720,000,000 SIN coins and 14,400 blocks at the best rate would guarantee that a UTXO staking chunk of 50,000 SIN coins would earn a reward every 14,400 blocks round. A wallet with only one chunk of 50,000 SIN coins has then the same luck to produce a block.
The second major benefit is the increase of transactions per second (TPS) by 20 from the previous version. Hence, the blockchain can support 2,000 TPS and 4,000 TPS with SegWit that is originally implemented with the Bitcoin core. This is possible by reducing the block time interval from 2 minutes to 1 minute and increasing the block size from 2 to 32 MB (64MB in SegWit). The block reward with PoS4 is 50 SIN coins.
This scalability will guarantee to manage the transactions relative to the data storage and payments with SIN coins. It brings a different decentralization from GPU miners and a security alongside the Proof-of-Burn and LockReward solutions.

## **6.  What are the next development phases?**

The first development step of PoS4 brings basic bricks of staking security, decentralization, and scalability. SINOVATE blockchain developers believe PoS’ should integrate the last features provided by Casper and Slasher approaches. Of course, the already-integrated PoB will make these implementations quite straightforward and efficient.


