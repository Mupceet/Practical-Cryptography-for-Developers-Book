# 安全哈希算法

In the past, many **cryptographic hash algorithms** were proposed and used by software developers. Some of them was **broken** \(like **MD5** and **SHA1**\), some are still considered secure \(like **SHA-2**, **SHA-3** and **BLAKE2**\). Let's review the most widely used cryptographic hash functions \(algorithms\).

过去，软件开发人员提出并使用了许多**加密哈希算法**。其中有些已**被认为不安全**（例如 **MD5** 和 **SHA1**），有些仍被认为是安全的（例如 **SHA-2**，**SHA-3** 和 **BLAKE2**）。让我们回顾一下使用最广泛的加密哈希函数（算法）。

## 安全哈希函数

**Modern cryptographic hash algorithms** \(like **SHA-3** and **BLAKE2**\) are considered **secure** enough for most applications.

**现代加密哈希算法**（如 **SHA-3** 和 **BLAKE2**）对于大多数应用程序来说足够**安全**。

### SHA-2, SHA-256, SHA-512

[**SHA-2**](https://en.wikipedia.org/wiki/SHA-2) is a family of strong cryptographic hash functions: **SHA-256** \(256 bits hash\), **SHA-384** \(384 bits hash\), **SHA-512** \(512 bits hash\), etc. It is based on the cryptographic concept "[**Merkle–Damgård construction**](https://en.wikipedia.org/wiki/Merkle–Damgård_construction)" and is considered **highly secure**. SHA-2 is published as official crypto standard in the United States.

[**SHA-2**](https://en.wikipedia.org/wiki/SHA-2) 是一个强加密哈希函数家族：**SHA-256**（256 位哈希）、**SHA-384**（384 位哈希）、**SHA-512**（512 位哈希）等，它基于密码学概念“[**Merkle–Damgård 结构**](https://en.wikipedia.org/wiki/Merkle–Damgård_construction)”，被认为是**高度安全**的。SHA-2 在美国作为官方密码标准发布。

**SHA-2** is widely used by developers and in cryptography and is considered cryptographically strong enough for modern commercial applications.

**SHA-2** 被开发人员和密码学领域广泛使用，被认为在密码学上有足够的强度，适合现代商业应用。

**SHA-256** is widely used in the **Bitcoin** blockchain, e.g. for identifying the transaction hashes and for the proof-of-work mining performed by the miners.

**SHA-256** 在**比特币**区块链中被广泛使用，例如用于识别交易的哈希以及用于由矿工进行的工作量证明挖掘。

Examples of SHA2 hashes:

SHA2 哈希的示例：

```text
SHA-256('hello') = 2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824
SHA-384('hello') = 59e1748777448c69de6b800d7a33bbfb9ff1b463e44354c3553bcdb9c666fa90125a3c79f90397bdf5f6a13de828684f
SHA-512('hello') = 9b71d224bd62f3785d96d46ad3ea3d73319bfbc2890caadae2dff72519673ca72323c3d99ba5c11d7c7acc6e14b8c5da0c4663475c2e5c3adef46f73bcdec043
```

### 更多的哈希位 = 更高的抗碰撞性

By design, **more bits at the hash output** are expected to achieve **stronger security** and higher collision resistance \(with some exceptions\). As general rule, 128-bit hash functions are weaker than 256-bit hash functions, which are weaker than 512-bit hash functions.

根据设计，在**哈希输出中使用更多的位**可以获得**更强的安全性**和更高的抗碰撞性（除了某些例外）。一般来说，128 位的哈希函数要比 256 位的哈希函数弱，256 位的哈希函数要比 512 位的哈希函数弱。

Thus, SHA-512 is stronger than SHA-256, so we can expect that for SHA-512 it is more unlikely to practically find a collision than for SHA-256.

因此，SHA-512 比 SHA-256 更强，所以我们可以预期，实际上 SHA-512 比 SHA-256 更不可能找到碰撞。

### SHA-3, SHA3-256, SHA3-512, Keccak-256

[**SHA-3**](https://en.wikipedia.org/wiki/SHA-3) \(and its variants SHA3-224, SHA3-256, SHA3-384, SHA3-512\), is considered **more secure than SHA-2** \(SHA-224, SHA-256, SHA-384, SHA-512\) for the same hash length. For example, SHA3-256 provides **more cryptographic strength than SHA-256** for the same hash length \(256 bits\).

对于相同的哈希长度，[**SHA-3**](https://en.wikipedia.org/wiki/SHA-3)（及其变体 SHA3-224、SHA3-256、SHA3-384、SHA3-512）被认为比 SHA-2 （SHA-224、SHA-256、SHA-384、SHA-512）**更安全**。例如，对于相同的哈希长度（256 位），SHA3-256 比 SHA-256 提供了更大的加密强度。

The **SHA-3** family of functions are representatives of the "**Keccak**" hashes family, which are based on the cryptographic concept "[**sponge construction**](https://en.wikipedia.org/wiki/Sponge_function)". Keccak is the winner of the [SHA-3 NIST competition](https://en.wikipedia.org/wiki/NIST_hash_function_competition#Finalists).

SHA-3 函数族是基于密码概念“[**海绵构造**](https://en.wikipedia.org/wiki/Sponge_function)”的“**Keccak**”哈希家族的代表。Keccak 是 [SHA-3 NIST 竞赛](https://en.wikipedia.org/wiki/NIST_hash_function_competition#Finalists)的获胜者。

Unlike **SHA-2**, the **SHA-3** family of cryptographic hash functions are not vulnerable to the "[**length extension attack**](https://en.wikipedia.org/wiki/Length_extension_attack)".

与 **SHA-2** 不同，**SHA-3** 系列加密哈希函数不容易受到“[**长度扩展攻击**](https://en.wikipedia.org/wiki/Length_extension_attack)”的影响。

**SHA-3** is considered **highly secure** and is published as official recommended crypto standard in the United States.

**SHA-3** 被认为是**高度安全**的，并在美国作为官方推荐的加密标准发布。

The hash function **Keccak-256**, which is used in the **Ethereum** blockchain, is a variant of SHA3-256 with some constants changed in the code.

**以太坊**区块链中使用的哈希函数 **Keccak-256** 是 SHA3-256 的变体，代码中一些常量发生了更改。

The hash functions **SHAKE128\(msg, length\)** and **SHAKE256\(msg, length\)** are variants of the **SHA3-256** and **SHA3-512** algorithms, where the output message length can vary.

哈希函数 **SHAKE128\(msg, length\)** 和 **SHAKE256\(msg, length\)** 是 **SHA3-256** 和 **SHA3-512** 算法的变体，其中输出消息的长度可以变化。

Examples of SHA3 hashes:

SHA3 哈希的示例：

```text
SHA3-256('hello') = 3338be694f50c5f338814986cdf0686453a888b84f424d792af4b9202398f392
Keccak-256('hello') = 1c8aff950685c2ed4bc3174f3472287b56d9517b9c948127319a09a7a36deac8
SHA3-512('hello') = 75d527c368f2efe848ecf6b073a36767800805e9eef2b1857d5f984f036eb6df891d75f72d9b154518c1cd58835286d1da9a38deba3de98b5a53e5ed78a84976
SHAKE-128('hello', 256) = 4a361de3a0e980a55388df742e9b314bd69d918260d9247768d0221df5262380
SHAKE-256('hello', 160) = 1234075ae4a1e77316cf2d8000974581a343b9eb
```

### BLAKE2 / BLAKE2s / BLAKE2b

[**BLAKE**](https://en.wikipedia.org/wiki/BLAKE_%28hash_function) / **BLAKE2** / **BLAKE2s** / **BLAKE2b** is a family of fast, highly secure cryptographic hash functions, providing calculation of 160-bit, 224-bit, 256-bit, 384-bit and 512-bit digest sizes, widely used in modern cryptography. BLAKE is one of the finalists at the [SHA-3 NIST competition](https://en.wikipedia.org/wiki/NIST_hash_function_competition#Finalists).

[**BLAKE**](https://en.wikipedia.org/wiki/BLAKE_%28hash_function) / **BLAKE2** / **BLAKE2s** / **BLAKE2b** 是一组快速、高度安全的加密散列函数，提供 160 位、224 位、256 位、384 位和512 位摘要大小的计算，在现代密码学中广泛使用。BLAKE 是 [SHA-3 NIST 竞赛](https://en.wikipedia.org/wiki/NIST_hash_function_competition#Finalists)的决赛选手之一。

The **BLAKE2** function is an improved version of **BLAKE**.

**BLAKE2** 函数是 **BLAKE** 的改进版本。

**BLAKE2s** \(typically **256-bit**\) is BLAKE2 implementation, performance-optimized for 32-bit microprocessors.

**BLAKE2s**（通常为 256 位）是 BLAKE2 的实现，针对 32 位微处理器进行了性能优化。

**BLAKE2b** \(typically **512-bit**\) is BLAKE2 implementation, performance-optimized for 64-bit microprocessors.

**BLAKE2b**（通常为 512 位）是 BLAKE2 的实现，针对 64 位微处理器进行了性能优化。

The **BLAKE2** hash function has similar security strength like SHA-3, but is less used by developers than SHA2 and SHA3.

**BLAKE2** 哈希函数具有与 SHA-3 类似的安全强度，但开发人员使用的频率低于 SHA2 和 SHA3。

Examples of BLAKE hashes:

BLACK 哈希的示例：

```text
BLAKE2s('hello') = 19213bacc58dee6dbde3ceb9a47cbb330b3d86f8cca8997eb00be456f140ca25
BLAKE2b('hello') = e4cfa39a3d37be31c59609e807970799caa68a19bfaa15135f165085e01d41a65ba1e1b146aeb6bd0092b49eac214c103ccfa3a365954bbbe52f74a2b3620c94
```

### RIPEMD-160

[**RIPEMD-160**](https://en.wikipedia.org/wiki/RIPEMD) is a secure hash function, widely used in cryptography, e.g. in PGP and Bitcoin.

[**RIPEMD-160**](https://en.wikipedia.org/wiki/RIPEMD) 是一种安全的哈希函数，广泛用于密码学中，例如在 PGP 和比特币中。

The **160-bit** variant of **RIPEMD** is widely used in practice, while the other variations like RIPEMD-128, RIPEMD-256 and RIPEMD-320 are not popular and have disputable security strengths.

**RIPEMD** 的 **160 位**版本在实践中得到了广泛的应用，而其他变体如 RIPEMD-128、RIPEMD-256 和 RIPEMD-320 则不受欢迎，而且安全性也存在争议。

As recommendation, **prefer using SHA-2 and SHA-3** instead of RIPEMD, because they are more stronger than RIPEMD, due to higher bit length and less chance for collisions.

**推荐使用 SHA-2 和 SHA-3** 而不是 RIPEMD，因为它们比 RIPEMD 强度更高，因为它们的位长更高，碰撞的机会更少。

Examples of RIPEMD hashes:

RIPEMD 哈希的示例：

```text
RIPEMD-160('hello') = 108f07b8382412612c048d07d13f814118445acd
RIPEMD-320('hello') = eb0cf45114c56a8421fbcb33430fa22e0cd607560a88bbe14ce70bdf59bf55b11a3906987c487992
```

All of the above popular secure hash functions \(SHA-2, SHA-3, BLAKE2, RIPEMD\) are not restricted by commercial patents and are **free for public use**.

上述所有流行的安全哈希函数（SHA-2、SHA-3、BLAKE2、RIPEMD）都不受商业专利的限制，可以**免费供公众使用**。

## 不安全的哈希函数

**Old hash algorithms** like [**MD5**](https://en.wikipedia.org/wiki/MD5), [**SHA-0**](https://en.wikipedia.org/wiki/SHA-1#SHA-0) and [**SHA-1**](https://en.wikipedia.org/wiki/SHA-1) are considered **insecure** and were withdrawn due to **cryptographic weaknesses** \(collisions found\). **Don't use MD5**, **SHA-0** and **SHA-1**! All these hash functions are proven to be cryptographically **insecure**.

诸如 [**MD5**](https://en.wikipedia.org/wiki/MD5)，[**SHA-0**](https://en.wikipedia.org/wiki/SHA-1#SHA-0) 和 [**SHA-1**](https://en.wikipedia.org/wiki/SHA-1) 之类的**旧哈希算法**被认为是**不安全**的，并由于存在**加密漏洞**（发现冲突）而被撤回。 **不要使用 MD5，SHA-0 和 SHA-1**！ 事实证明，所有这些哈希函数在加密中都是**不安全**的。

You can find in Internet that **SHA1 collisions** can be practically generated and this results in algorithms for creating **fake digital signatures**, demonstrated by two different signed PDF documents which hold different content, but have the same hash value and the same digital signature. See [https://shattered.io](https://shattered.io).

你可以在互联网上找到，**SHA1 碰撞**可以实际生成，导致存在创建**假数字签名**的算法，例如两个不同的PDF文档，它们包含不同的内容，但具有相同的哈希值和相同的数字签名。参见https://shattered.io。

Avoid using of the following hash algorithms, which are considered **insecure** or have disputable security: [**MD2**](https://en.wikipedia.org/wiki/MD2_%28hash_function), [**MD4**](https://en.wikipedia.org/wiki/MD4), [**MD5**](https://en.wikipedia.org/wiki/MD5), [**SHA-0**](https://en.wikipedia.org/wiki/SHA-1#SHA-0), [**SHA-1**](https://en.wikipedia.org/wiki/SHA-1), [**Panama**](https://en.wikipedia.org/wiki/Panama_%28cryptography), [**HAVAL**](https://en.wikipedia.org/wiki/HAVAL) \(disputable security, collisions found for HAVAL-128\), [**Tiger**](https://en.wikipedia.org/wiki/Tiger_%28hash_function) \(disputable, weaknesses found\), [**SipHash**](https://en.wikipedia.org/wiki/SipHash) \(it is not a cryptographic hash function\).

避免使用下列哈希算法，它们被认为是不安全的或具有可争议的安全性:[**MD2**](https://en.wikipedia.org/wiki/MD2_%28hash_function)、[**MD4**](https://en.wikipedia.org/wiki/MD4)、[**MD5**](https://en.wikipedia.org/wiki/MD5)、[**SHA-0**](https://en.wikipedia.org/wiki/SHA-1#SHA-0)、[**SHA-1**](https://en.wikipedia.org/wiki/SHA-1)、[**Panama**](https://en.wikipedia.org/wiki/Panama_%28cryptography)、[**HAVAL**](https://en.wikipedia.org/wiki/HAVAL)（具有争议的安全性，HAVAL-128 找到了冲突）、[**Tiger**](https://en.wikipedia.org/wiki/Tiger_%28hash_function)（具有争议，找到了弱点）、[**SipHash**](https://en.wikipedia.org/wiki/SipHash)（它不是一个加密哈希函数）。

### 其他安全哈希函数

The below functions are popular strong cryptographic hash functions, alternatives to SHA-2, SHA-3 and BLAKE2:

以下函数是流行的强加密哈希函数，可替代 SHA-2，SHA-3 和 BLAKE2：

* [**Whirlpool**](https://en.wikipedia.org/wiki/Whirlpool_%28hash_function) is secure cryptographic hash function, which produces 512-bit hashes.
* [**Whirlpool**](https://en.wikipedia.org/wiki/Whirlpool_%28hash_function) 是安全的加密哈希函数，可产生 512 位哈希值。
* [**SM3**](https://tools.ietf.org/id/draft-oscca-cfrg-sm3-01.html) is the crypto hash function, officialy standartized by the **Chinese government**. It is similar to SHA-256 \(based on the Merkle–Damgård construction\) and produces 256-bit hashes.
* [**SM3**](https://tools.ietf.org/id/draft-oscca-cfrg-sm3-01.html) 是加密哈希函数，由**中国政府**正式制定。它类似于 SHA-256（基于 Merkle-Damgård 结构）并产生 256 位哈希。
* [**GOST**](https://en.wikipedia.org/wiki/GOST_%28hash_function) \(GOST R 34.11-94\) is secure cryptographic hash function, the Russian national standard, described in [RFC 4357](https://tools.ietf.org/html/rfc4357). It produces 256-bit hashes.
* [**GOST**](https://en.wikipedia.org/wiki/GOST_%28hash_function) 是俄罗斯国家标准的安全加密哈希函数，在 [RFC 4357](https://tools.ietf.org/html/rfc4357) 中有描述。它产生 256 位的哈希值。

The below functions are less popular alternatives to SHA-2, SHA-3 and BLAKE, finalists at the [SHA-3 NIST competition](https://en.wikipedia.org/wiki/NIST_hash_function_competition#Finalists):

以下函数是 SHA-2、SHA-3 和 BLAKE 的不太受欢迎的替代品，它们是 [SHA-3 NIST 竞赛](https://en.wikipedia.org/wiki/NIST_hash_function_competition#Finalists)的决赛选手:

* [**Skein**](https://en.wikipedia.org/wiki/Skein_%28hash_function) is secure cryptographic hash function, capable to derive 128, 160, 224, 256, 384, 512 and 1024-bit hashes.
* [**Skein**](https://en.wikipedia.org/wiki/Skein_%28hash_function) 是一个安全的加密哈希函数，可以生成 128、160、224、256、384、512 和 1024 位的哈希值。
* [**Grøstl**](https://en.wikipedia.org/wiki/Grøstl) is secure cryptographic hash function, capable to derive 224, 256, 384 and 512-bit hashes.
* [**Grøstl**](https://en.wikipedia.org/wiki/Grøstl) 是一个安全的加密哈希函数，可以生成 224、256、384 和 512 位的哈希值。
* [**JH**](https://en.wikipedia.org/wiki/JH_%28hash_function) is secure cryptographic hash function, capable to derive 224, 256, 384 and 512-bit hashes.
* [**JH**](https://en.wikipedia.org/wiki/JH_%28hash_function) 是一个安全的加密哈希函数，可以生成 224、256、384 和 512 位的哈希值。

### SHA-256，SHA3-256，BLAKE2 和 RIPEMD-160 没有已知的碰撞

As of Oct 2018, **no collisions are known** for: **SHA256**, **SHA3-256**, **Keccak-256**, **BLAKE2s**, **RIPEMD160** and few others.

截至 2018 年 10 月，尚无已知的碰撞发生：**SHA256**、**SHA3-256**、**Keccak-256**、**BLAKE2s**、**RIPEMD160**等。

**Brute forcing** to find hash function collision as general costs: 2128 for SHA256 / SHA3-256 and 280 for RIPEMD160.

**穷举**查找哈希函数碰撞的一般开销：SHA256 / SHA3-256 需要 2<sup>128</sup>, RIPEMD160 是 2<sup>160</sup>。

Respectively, on a powerful enough **quantum computer**, it will cost less time: 2256/3 and 2160/3 respectively. Still \(as of September 2018\) so powerful quantum computers are not known to exist.

另外，在一台足够强大的量子计算机上，它将花费更少的时间：分别为2<sup>256</sup>/3和2<sup>160</sup>/3。尽管如此（截至 2018 年 9 月），如此强大的量子计算机尚不存在。

Learn more about cryptographic hash functions, their strength and **attack resistance** at: [https://z.cash/technology/history-of-hash-function-attacks.html](https://z.cash/technology/history-of-hash-function-attacks.html)

要了解有关加密哈希函数及其强度和**抗攻击性**的更多信息，请访问：[https://z.cash/technology/history-of-hash-function-attacks.html](https://z.cash/technology/history-of-hash-function-attacks.html)
