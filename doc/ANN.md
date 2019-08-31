Sugarchain
==========
one-CPU-one-vote, the world's fastest PoW blockchain


KICK OFF
--------
- 2019/08/24 15:00 UTC
- [Saturday, 24 August 2019, 15:00:00 (UTC time)](https://www.timeanddate.com/countdown/launch?iso=20190824T15&p0=1440&msg=%5BANN%5D+Sugarchain+%5BCPU%5D+Launching+2019%2F08%2F24+15%3A00+UTC&font=sanserif)


Specifications
--------------
- Block time: `5 seconds`
- Difficulty: **SugarShield-N510** (based on Zcash's modification of Digishield)
- Block reward: `42.94967296 SUGAR`
- Halving interval: `12,500,000 Blocks` (approx. 2 years)
- Total supply: `1,073,741,824 SUGAR`
- PoW algorithm: **YespowerSugar** (based on Yespower 1.0.1)
- Port: 34230 (RPC 34229)
- Premine: **None** (NO ICO, NO Presale)


The world's fastest PoW blockchain
----------------------------------
- 5 seconds transaction speed
 - 120x faster than Bitcoin
 - 30x faster than Litecoin
 - 12x faster than Dogecoin
- Stable transaction time:
 - Even if the hash power suddenly increases, the block time keeps 5 seconds. It is against hash attacks.
- Don't worry about orphan blocks: 
 - The average orphaned rate is under 3% and no problem occurs.


A better block reward halving
-----------------------------
- Halving is everything: 
 - Bitcoin is valuable because its total supply has been strictly limited, unlike traditional currencies. This total supply is controlled only by that halving. There is nothing else. We made this halving better.
- Block reward: 
 - The block reward should be a power of two. So that it halves correctly. ie) `2^32/100000000 = 42.94967296 SUGAR`
- Halving schedule: 
 - Interval `12500000 blocks (5^8*32)` is about 2 years (exactly 1.9818619989852864... years). The total number of halvings is `33 times`, and it is expected to take about `66 years`.
- Total supply: 
 - `1073741824 SUGAR` in theory and `1073741823.875 SUGAR` in actual. The difference is `0.125 SUGAR`. One Satoshi (0.00000001) limitation makes this difference. In addition, this number is meaningful. `1 GB = 1073741824 Byte (2^30)`.
- ![Halving Chart](https://github.com/sugarchain-project/yumekawa-utils/blob/master/max_money/max_money.png)
- ![Halving Table](https://github.com/sugarchain-project/yumekawa-utils/blob/master/max_money/excel.png)


one-CPU-one-vote
----------------
Satoshi Nakamoto said about the importance of decentralized mining in his whitepaper. We want to create a blockchain that anyone can do mining easily without any entry barriers.

> "31/Oct/2008 Proof-of-work is essentially one-CPU-one-vote"

- CPU mining only
 - YespowerSugar (based on Yespower 1.0.1) is only for Sugarchain, not compatible with other Yespower coins.
 - The minimum difficulty (powlimit) is set low enough for two reasons. The first is to handle fast block time. The second is to allow mining on slow CPUs.
- Mining efficiency: 
 - According to the test results, the most efficient at 8 threads on a single CPU.
 - YespowerSugar is more suitable for older CPUs, because it is essentially a multi-threading resistor. Suitable for smartphones and raspberrypi.
- NO GPU: GPU mining is not possible.
- NO ASIC: ASIC mining is not possible.


Other advantages
----------------
- Native segwit (Bech32) address as default: It starts with `sugar1q...`
- Fast blockchain synchronization: Using sha256d in header indexing, the initial synchronization speed is as fast as Litecoin.


FAQ
---
- Disk space requirements: 
 - Blockchain size growth is around `10 MB per 1 day` and 3.65 GB per 1 year.
- Network rules: 
 - To prevent fraud and timestamp attacks, nodes should be within `70 seconds` of accurate internet time. Or it will be banned.
- Selfish mining & time warp attack: 
 - Fraud techniques for manipulating timestamps are already known. We use a future time limit (FTL) to prevent this. Blocks that differ `60 seconds` or more from the current head will be banned. (credit: zawy12)
- Exchange listing: 
 - We do not have a listing plan at this moment. However it can be discuss it on our community and it will be possible in the future. Please suggest.


Appendix
--------
- Block time vs difficulty at first launching on testnet
 - To keep the block time 5 seconds, SugarShield-N510 adjusts the difficulty level. Unlike the Zcash's modification version, we use a moving average of `510 blocks` (about 42.5 minutes). It counts from block 1, an adjustment is made at block 511, and the actual control begins at block 512. [(log: time-diff)](https://github.com/cryptozeny/difficulty/blob/master/examples-ANN/main.Sugarchain(t5)-YP-DS(n510)-13536.log)
 - ![Blocktime vs Difficulty](https://github.com/cryptozeny/difficulty/blob/master/examples/test.Sugarchain(t5)-YP-DS(n510).png)

- Nonce distribution at first launching on testnet 
 - The nonce is randomly well distributed. Difficulty changes but no bias. [(log: nonce-diff)](https://github.com/cryptozeny/difficulty/blob/master/examples-ANN/NONCE-main.Sugarchain(t5)-YP-DS(n510)-13548.log)
 - ![Nonce vs Difficulty](https://github.com/cryptozeny/difficulty/blob/master/examples/NONCE-test.Sugarchain(t5)-YP-DS(n510).png)


Wallet
------
- Win64: https://github.com/sugarchain-project/sugarchain/releases/tag/release-0.16.3.21rc1
- Win32: comming soon 
- Linux64: https://github.com/sugarchain-project/sugarchain/releases/tag/release-0.16.3.21rc1
- Linux32: comming soon
- OSX: https://github.com/sugarchain-project/sugarchain/releases/tag/release-0.16.3.21rc1
- ARM64: comming soon
- ARM32: comming soon
- Source: comming soon


Cpuminer
--------
Bech32 address is default and recommended. `-t1` uses 1 thread. if you want more hash, increase this number.
- Solo mining: Make a file [u]sugarchain.conf[/u], restart your wallet and run cpuminer-opt-sugarchain (RPC=34229, testnet RPC=44229)
```
server=1
rpcuser=username
rpcpassword=password
```
```
./cpuminer -a yespower -o http://localhost:34229 -u username -p password --coinbase-addr=sugar1q... -t1
```
- Pool mining:
```./cpuminer -a yespower -o stratum+tcp://POOL_ADDRESS:PORT -u sugar1q... -t1```

- **cpuminer-opt-sugarchain**: https://github.com/cryptozeny/cpuminer-opt-sugarchain/releases/tag/v3.8.8.1.7rc1


Pools
-----
Please contact us if you have a new mining pool.
- 1pool@tokyo https://1pool.sugarchain.org/
- 2pool@tokyo https://2pool.sugarchain.org/
- 52hash@china http://sugar.52hash.com/
- rplant@moscow https://pool.rplant.xyz/
- happysensor@korea http://pool.happysensor.xyz/


Explorer
--------
- 1explorer: https://1explorer.sugarchain.org/
- 2explorer: comming soon
- trezor blockbook: https://sugarchain-blockbook.ilmango.work/


Exchanges
---------
- ex4ange (by DobroFenix): https://ex4ange.org/?SUGAR-DOGE


If you are interested in the Sugarchain project, come to [Discord](https://discord.gg/rm7HHv6) and please follow us on [Twitter](https://twitter.com/sugarchain_dev).