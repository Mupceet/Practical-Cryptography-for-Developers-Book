# 加密哈希和碰撞

**Different input** messages are expected to produce **different output** hash values \(message digest\).

预期中**不同的输入**消息会产生**不同的输出**哈希值（消息摘要）。

![](../.gitbook/assets/crypto-hash-function-examples.jpg)

## 哈希碰撞

A **collision** means the same hash value for two different inputs. For simple hash functions it is easy to reach a collision. For example, assume a hash function `h(text)` sums of all character codes in a text. It will produce the same hash value \(collision\) for texts holding the same letters in different order, i.e. `h('abc') == h('cab') == h('bca')`. To avoid collisions, cryptographers have designed **collision-resistant** hash functions.

**碰撞**表示不同的两个输入具有相同的哈希值。对于简单的哈希函数，很容易产生冲突。例如，假设一个哈希函数 `h(text)` 是文本中所有字符编码的和。在文本为相同的字母的不同的顺序组合时，它将产生相同的哈希值(碰撞)，即 `h('abc') == h('cab') == h('bca')`。为了避免碰撞，密码学家设计了**抗碰撞**哈希函数。

## 加密哈希函数：无冲突

**Collisions** in the cryptographic hash functions are **extremely unlikely** to be found, so crypto **hashes** are considered to almost uniquely identify their corresponding input. Moreover, it is extremely hard to find an input message that hashes to given value.

加密哈希函数的**冲突极难出现**，因此加密**哈希**被认为几乎惟一地标识了它们对应的输入。此外，很难找出一个给定哈希值的输入。

Cryptographic hash functions are **one-way hash functions**, which are **infeasible to invert**. The chance to find a collision \(by brute force\) for a strong cryptographic hash function \(like SHA-256\) is extremely little. Let's define this in more details:

加密哈希函数是**单向哈希函数**，**不可逆转**。为强加密哈希函数（如 SHA-256）找出碰撞（通过蛮力）的机会非常小。下面来让我们更详细地定义它：

* Let's have hash value `h`=`hash(p)` for certain strong cryptographic hash function `hash`.
* 我们用 `h`=`hash(p)` 来表示某个强加密哈希函数得到的哈希值。
* It is expected to be **extremely hard** to find an input `p'`, such that `hash(p')`=`h`.
* 预期中很难找到输入 `p'` 使得 `hash(p')=h`。
* For most modern strong cryptographic hash functions there are **no known collisions**.
* 对于大多数现代强加密哈希函数，不存在**已知的碰撞**。

The **ideal cryptographic hash function** should have the following properties:

**理想的加密哈希函数**应具有以下属性：

* **Deterministic**: the same input message should always result in the same hash value.
* **确定性**：相同的输入消息应始终产生相同的哈希值。
* **Quick**: it should be fast to compute the hash value for any given message.
* **快速**：计算任何给定消息的哈希值应该很快。
* **Hard to analyze**: a small change to the input message should totally change the output hash value.
* **难于分析**：对输入消息的微小更改将完全改变输出的哈希值。
* **Irreversible**: generating a valid input message from its hash value should be **infeasible**. This means that there should be no significantly better way than brute force \(try all possible input messages\).
* **不可逆**：从其哈希值生成有效的输入消息应该是不可行的。这意味着没有比暴力破解更好的方法（尝试所有可能的输入消息）。
* **No collisions**: it should be extremely hard \(or practically impossible\) to find two different messages with the same hash.
* **没有冲突**：找到具有相同哈希值的两个不同消息应该非常困难（或几乎不可能）。

Modern cryptographic hash functions \(like SHA2 and SHA3\) match the above properties and are used widely in cryptography.

现代加密哈希函数（如 SHA2 和 SHA3）符合上述性质，在密码学中得到了广泛的应用。
