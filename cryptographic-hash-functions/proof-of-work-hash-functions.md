# 工作量证明（Proof-of-Work）哈希函数

Blockchain **proof-of-work mining** algorithms use a special class of hash functions which are **computational-intensive** and **memory-intensive**. These hash functions are designed to consume a lot of computational resources and a lot of memory and to be very hard to be implemented in a hardware devices \(such as [FPGA](https://en.wikipedia.org/wiki/Field-programmable_gate_array) integrated circuits or [ASIC](https://en.wikipedia.org/wiki/Application-specific_integrated_circuit) miners\). Such hash functions are known as "**ASIC-resistant**".

区块链**工作证明挖掘算法**使用了一类特殊的哈希函数，它是**计算密集型**和**内存密集型**的。这些哈希函数被设计成消耗大量计算资源和大量内存，并且很难在硬件设备（如 [FPGA](https://en.wikipedia.org/wiki/Field-programmable_gate_array) 集成电路或 [ASIC](https://en.wikipedia.org/wiki/Application-specific_integrated_circuit) 矿工）中实现。这种被称为“**抗 ASIC**”的哈希函数。

Many hash functions are designed for proof-of-work mining algorithms, e.g. **ETHash**, **Equihash**, **CryptoNight** and **Cookoo Cycle**. These hash functions are **slow to calculate**, and usually use **GPU** hardware \([rigs](https://en.bitcoin.it/wiki/Mining_rig) of graphics cards like NVIDIA GTX 1080\) or powerful **CPU** hardware \(like Intel Core i7-8700K\) and a lot of fast **RAM** memory \(like DDR4 chips\). The goal of these mining algorithms is to **minimize the centralization of mining** by stimulating the small miners \(home users and small mining farms\) and limit the power of big players in the mining industry \(who can afford to build giant mining facilities and data centers\). A big number of **small players means better decentralization** than a small number of big players.

许多哈希函数是为工作证明挖掘算法而设计的，例如 **ETHash**、**Equihash**、**CryptoNight** 和 **Cookoo Cycle**。这些哈希函数**计算速度很慢**，通常使用 **GPU** 硬件（如 NVIDIA GTX 1080 等 [rigs](https://en.bitcoin.it/wiki/Mining_rig) 显卡，）或强大的 **CPU** 硬件（如 Intel Core i7-8700K）和大量的快速 **RAM** 内存（如 DDR4 芯片）。这些挖掘算法的目标是通过刺激小型采矿者（家庭用户和小型采矿场）来**最小化挖掘的集中化**，并限制采矿行业中大型参与者的权力（他们有能力建造巨大的采矿设施和数据中心）。大数量的小参与者比小数量的大参与者**意味着更好的分权**。

The main weapon in the hands of the big mining corporations is considered the [ASIC miners](https://en.bitcoin.it/wiki/Mining_hardware_comparison), so the design of modern cryptocurrencies and usually includes proof-of-work mining using an **ASIC-resistant hashing algorithm** or **proof-of-stake** consensus protocol.

大型矿业公司手中的主要武器被认为是 [ASIC 矿工](https://en.bitcoin.it/wiki/Mining_hardware_comparison)，因此，现代加密货币的设计通常包括使用**抗 ASIC 的哈希算法**或**权益证明**（**proof-of-stake**）共识协议进行的工作量证明挖掘。

## ETHash

Let's explain in brief the idea behind the **ETHash** proof-of-work mining hash function used in the Ethereum blockchain.

让我们简要地解释一下以太坊区块链中使用的 **ETHash** 工作量证明挖掘哈希函数背后的思想。

* **ETHash** is the proof-of-work hash function in the Ethereum blockchain. It is **memory-intensive** hash-function \(requires a lot of RAM to be calculated fast\), so it is believed to be **ASIC-resistant**.
* **ETHash** 是以太坊区块链中的工作量证明哈希函数。它是**内存密集型**哈希函数（需要大量 RAM 才能快速计算），因此被认为具有 **ASIC 抵抗性**。

How does ETHash work?

**ETHash** 如何工作？

* A "**seed**" is computed for each block \(based on the entire chain until the current block\).
* 为每个块计算一个“**种子**”（基于直到当前块的整个链）。
* From the seed, a **16 MB pseudorandom cache** is computed.
* 根据种子，计算出 **16 MB 的伪随机缓存**。
* From the cache, a **1 GB dataset** is extracted to be used in mining.
* 从缓存中提取 **1 GB 的数据集**以用于挖掘。
* Mining involves hashing together random slices of the dataset.
* 挖掘涉及将数据集的随机切片哈希在一起。

Learn more about **ETHash** at: [https://github.com/ethereum/wiki/wiki/Ethash](https://github.com/ethereum/wiki/wiki/Ethash), [https://github.com/lukovkin/ethash](https://github.com/lukovkin/ethash).

要了解有关 **ETHash** 的更多信息，请访问：[https://github.com/ethereum/wiki/wiki/Ethash](https://github.com/ethereum/wiki/wiki/Ethash)，[https://github.com/lukovkin/ethash](https://github.com/lukovkin/ethash)

## Equihash

Let's explain in briefly the idea behind the **Equihash** proof-of-work mining hash function used in Zcash, Bitcoin Gold and a few other blockchains.

让我们简要地解释一下在 Zcash、Bitcoin Gold 和其他几个区块链中使用的 **Equihash** 工作证明挖掘哈希函数背后的思想。

* **Equihash** is the proof-of-work hash function in the Zcash and Bitcoin Gold blockchains. It is **memory-intensive** hash-function \(requires a lot of RAM for fast calculation\), so it is believed to be **ASIC-resistant**.
* **Equihash** 是 Zcash 和 Bitcoin Gold 区块链中的工作量证明哈希函数。它是**内存密集型**哈希函数（需要大量 RAM 才能快速计算），因此被认为具有 **ASIC 抵抗性**。

How does **Equihash** work?

**Equihash** 如何工作？

* Uses **BLAKE2b** to compute **50 MB hash dataset** from the previous blocks in the blockchain \(until the current block\).
* 使用 **BLAKE2b** 从区块链中以前的块（直到当前块）计算 **50 MB 哈希数据集**。
* Solves the "**Generalized Birthday Problem**" over the generated hash dataset \(pick 512 different strings from 2097152, such that the binary XOR of them is zero\). The best known solution \(Wagner's algorithm\) runs in exponential time, so it requires a lot of memory-intensive and computing-intensive calculations.
* 在生成的哈希数据集上解决“**通用生日问题**”（从 2097152中选择512个不同的字符串，使它们的二进制异或为零）。最著名的解决方案（ Wagner 算法）需要指数级时间，因此需要大量的内存密集型和计算密集型计算。
* **Double SHA256** the solution to compute the final hash.
* **双 SHA256** 解决方案计算最终哈希。

Learn more about **Equihash** at: [https://www.cryptolux.org/images/b/b9/Equihash.pdf](https://www.cryptolux.org/images/b/b9/Equihash.pdf), [https://github.com/tromp/equihash](https://github.com/tromp/equihash).

要了解有关 **Equihash** 的更多信息，请访问：[https://www.cryptolux.org/images/b/b9/Equihash.pdf](https://www.cryptolux.org/images/b/b9/Equihash.pdf)，[https://github.com/tromp/equihash](https://github.com/tromp/equihash)

## 有关抗 ASIC 的哈希函数的更多信息

Lear more about the **ASIC-resistant hash functions** at: [https://github.com/ifdefelse/ProgPOW](https://github.com/ifdefelse/ProgPOW).

要了解有关**抗 ASIC 的哈希函数**的更多信息，请访问：[https://github.com/ifdefelse/ProgPOW](https://github.com/ifdefelse/ProgPOW)。
