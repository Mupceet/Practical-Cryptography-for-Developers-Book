# 哈希函数

In computer programming **hash functions** map text \(or other data\) to integer numbers. Usually different inputs maps to different outputs, but sometimes a **collision** may happen \(different input with the same output\).

在计算机编程中，**哈希函数**将文本（或其他数据）映射为整数。通常情况下不同的输入将映射得到不同的输出，但有时也可能会发生**碰撞**（不同的输入具有相同的输出）。

**Cryptographic hash** functions transform text or binary data to fixed-length **hash value** and are known to be **collision-resistant** and **irreversible**. Example of cryptographic hash function is **SHA3-256**:

**加密哈希函数**用来将文本或二进制数据转换为固定长度的**哈希值**，并且它具有**抗碰撞性**和**不可逆性**。加密哈希函数的一个例子是 **SHA3-256**：

```text
SHA3-256("hello") = "3338be694f50c5f338814986cdf0686453a888b84f424d792af4b9202398f392"
```

The above SHA3-256 hash calculation can be coded in Python like this:

上述 SHA3-256 哈希计算可用 Python 编码如下：

```python
import hashlib, binascii
sha3_256hash = hashlib.sha3_256(b'hello').digest()
print("SHA3-256('hello') =", binascii.hexlify(sha3_256hash))
```

Run the above code example: [https://repl.it/@nakov/SHA3-256-hello-in-Python](https://repl.it/@nakov/SHA3-256-hello-in-Python).

可在此链接中运行该示例代码：[https://repl.it/@nakov/SHA3-256-hello-in-Python](https://repl.it/@nakov/SHA3-256-hello-in-Python)。

The same SHA3-256 hash calculation can be coded in JavaScript like this \(after `npm install js-sha3`\):

类似的，SHA3-256 哈希计算可以用 JavaScript 编码如下（需先执行 `npm install js-sha3`）：

```javascript
sha3 = require('js-sha3');
let sha3_256hash = sha3.sha3_256('hello').toString();
console.log("SHA3-256('hello') =", sha3_256hash);
```

Run the above code example: [https://repl.it/@nakov/SHA3-256-hello-in-JS](https://repl.it/@nakov/SHA3-256-hello-in-JS).

可在此链接中运行该示例代码：[https://repl.it/@nakov/SHA3-256-hello-in-JS](https://repl.it/@nakov/SHA3-256-hello-in-JS)。

## 软件工程中的哈希

The process of calculating the value of certain hash function is called "**hashing**".

计算某个哈希函数值的过程称为“**哈希**”。

![](../.gitbook/assets/hash-function.jpg)

In the above example the text `John Smith` is hashed to the hash value `02` and `Lisa Smith` is hashed to `01`. The input texts `John Smith` and `Sandra Dee` both are hashed to `02` and this is called "**collision**".

在上面的例子中，文本 `John Smith` 被哈希为哈希值 `02`，`Lisa Smith` 被哈希为 `01`。文本 `John Smith` 和 `Sandra Dee` 都被哈希为 `02`，这就是所谓的“**碰撞**”。

Hash functions are **irreversible by design**, which means that there is no fast algorithm to restore the input message from its hash value.

哈希函数**在设计上是不可逆的**，这意味着没有快速的算法来从其哈希值恢复输入信息。

In programming **hash functions** are used in the implementation of the data structure "**hash-table**" \(associative array\) which maps values of certain input type to values of another type, e.g. map product name \(text\) to product price \(decimal number\).

在编程中，**哈希函数**用于“**哈希表**”（关联数组）数据结构的实现，该结构将某种输入类型的值映射到另一种类型的值，例如，将产品名称（文本）映射到产品价格（小数）。

A **naive hash function** is just to sum the bytes of the input data / text. It causes a lot of collisions, e.g. `hello` and `ehllo` will have the same hash code. **Better hash functions** may use the [Merkle–Damgård construction](https://en.wikipedia.org/wiki/Merkle–Damgård_construction) scheme, which takes the first byte as **state**, then **transforms the state** \(e.g. multiplies it by a prime number like 31\), then **adds the next byte** to the state, then again transforms the state and adds the next byte, etc. This significantly reduces the rate of collisions and produces better distribution.

**简单的哈希函数**就是对输入数据或文本的字节求和。这会引起很多碰撞，例如 hello 和 ehllo 会有相同的哈希值。**更好的哈希函数**可以使用 [Merkle–Damgård 构造](https://en.wikipedia.org/wiki/Merkle–Damgård_construction)方案，它将第一个字节作为**状态**，然后**转换状态**(例如将其乘以一个质数，如 31)，然后**将下一个字节添加到状态中**，然后再次转换状态并添加下一个字节，依次重复。这将大大降低碰撞率并产生更好的分布。

## 加密哈希函数

In cryptography, **hash functions** transform **input data** of arbitrary size \(e.g. a text message\) to a **result** of fixed size \(e.g. 256 bits\), which is called **hash value** \(or hash code, message digest, or simply hash\). Hash functions \(hashing algorithms\) used in computer cryptography are known as "**cryptographic hash functions**". Examples of such functions are **SHA-256** and **SHA3-256**, which transform arbitrary input to 256-bit output.

在密码学中，**哈希函数**将任意大小的**输入数据**（如文本信息）转换为固定长度的**哈希值**（也可称为哈希码、信息摘要或简单哈希）**结果**（例如 256 位）。计算机密码学中使用的哈希函数（哈希算法）称为”**加密哈希函数**“。这类函数的例子有 **SHA-256** 和 **SHA-256**，它们将任意输入转换为 256 位的输出。

![](../.gitbook/assets/crypto-hash-function.jpg)

### 加密哈希函数——示例

As an **example**, we can take the cryptographic hash function `SHA-256` and calculate the hash value of certain text message `hello`:

以加密哈希函数 `SHA-256` 为例，计算文本信息 `hello` 的哈希值：

```text
SHA-256("hello") = "2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824"
```

The above SHA-256 calculation can be coded in Python like this:

上述 SHA-256 哈希计算可用 Python 编码如下：

```python
import hashlib, binascii

sha256hash = hashlib.sha256(b'hello').digest()
print("SHA-256('hello') = ", binascii.hexlify(sha256hash))
```

Run the above code example: [https://repl.it/@nakov/SHA-256-hello-in-Python](https://repl.it/@nakov/SHA-256-hello-in-Python).

可在此链接中运行该示例代码：[https://repl.it/@nakov/SHA-256-hello-in-Python](https://repl.it/@nakov/SHA-256-hello-in-Python)。

There is no efficient algorithm to find the input message \(in the above example `hello`\) from its hash value \(in the above example `2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824`\). It is well-known that cryptographic hash functions **cannot be reversed** back, so they are used widely to encode an input without revealing it \(e.g. encode a private key to a blockchain address without revealing the key\).

没有一种有效的算法可以从其哈希值（在上述示例中为 `2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824`）中找到输入信息（在上述示例中为 `hello`）。 众所周知，加密哈希函数**无法逆推**，因此它们被广泛地用于在不显示输入的情况下对输入进行编码（例如，在不显示密钥的情况下对一个区块链地址的私钥进行编码）。

As another **example**, we can take the cryptographic hash function `SHA3-512` and calculate the hash value of the same text message `hello`:

再举一个例子，我们可以采用加密哈希函数 `SHA3-512` 计算同一文本信息 `hello` 的哈希值：

```text
SHA3-512("hello") = "75d527c368f2efe848ecf6b073a36767800805e9eef2b1857d5f984f036eb6df891d75f72d9b154518c1cd58835286d1da9a38deba3de98b5a53e5ed78a84976"
```

### 加密哈希函数——在线演示

**Play** with most popular cryptographic hash functions **online**: [https://www.fileformat.info/tool/hash.htm](https://www.fileformat.info/tool/hash.htm).

可**在线使用**最流行的加密哈希函数：[https://www.fileformat.info/tool/hash.htm](https://www.fileformat.info/tool/hash.htm)

![](../.gitbook/assets/hash-functions-online.png)

**Cryptographic hash functions** are widely used in cryptography, in computer programming and in blockchain systems.

**加密哈希函数**广泛用于加密、计算机编程和区块链系统中。
