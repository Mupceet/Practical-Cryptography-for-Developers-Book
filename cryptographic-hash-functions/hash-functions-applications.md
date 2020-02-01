# 哈希函数：应用场景

**Cryptographic hash functions** \(like SHA-256 and SHA3-256\) are used in many scenarios. Let's review their most common applications.

**加密哈希函数**（如 SHA-256 和 SHA-256）在许多场景中都有使用。让我们来回顾一下它们最常见的应用。

## 文件完整性

Verifying the **integrity** of files / documents / messages. E.g. a **SHA256 checksum** may confirm that certain file is original \(not modified after its checksum was calculated\).

验证文件/文档/信息的**完整性**。例如，**SHA256 校验和**可以确认某个文件是原始文件（在校验和计算后再没有修改）。

![](../.gitbook/assets/checksum-download-openssl.png)

The above screenshot demonstrates how the **SHA256 checksums** ensure the **integrity** of the OpenSSL files at the official Web site of OpenSSL.

上面的截图展示了 **SHA256 校验和**如何确保 OpenSSL 官方网站上 OpenSSL 文件的**完整性**。

## 存储密码

Storing **passwords** and verification of passwords. Instead of keeping a plain-text password in the database, developers usually keep **password hashes** or more complex values derived from the password \(e.g. **Scrypt**-derived value\).

存储**密码**及密码验证。开发人员通常不在数据库中的保留纯文本密码，而保留**密码的哈希**或从密码派生的更复杂的值（例如，**Scrypt** 派生的值）。

![](../.gitbook/assets/linux-shadow-encrypted-passwords.png)

The above example comes from the `/etc/shadow` file in a modern Linux system. The above passwords are stored as multiple-round SHA-512 hashes with salt.

上面的示例来自现代 Linux 系统中的 `/etc/shadow` 文件。上面的密码存储为带盐的多轮 SHA-512 哈希值。

## 生成唯一 ID

Generate an \(**almost**\) **unique ID** of certain document / message. Cryptographic hash functions almost uniquely identify documents based on their content. In theory **collisions are possible** with any cryptographic hash function, but are very unlikely to happen, so most systems \(like **Git**\) assume that the hash function they use is **collistion free**.

生成某个文档 / 信息的（**几乎**）**惟一的 ID**。加密哈希函数根据文档的内容几乎惟一地来标识文档。理论上，任何加密哈希函数都**可能发生碰撞**，但这种可能性很小，所以大多数系统（比如 **Git**）都假设它们使用的哈希函数是**无碰撞**的。

Usually a document is **hashed** and the **document ID** \(hash value\) is used later to prove the existence of the document, or to retrieve the document from a storage system. Example of hash-based unique IDs are the commit hashes in **Git** and **GitHub**, based on the content of the commit \(e.g. `3c3be25bc1757ca99aba55d4157596a8ea217698`\) and the **Bitcoin** addresses \(e.g. `1BvBMSEYstWetqTFn5Au4m4GFg7xJaNVN2`\).

通常对文档进行**哈希处理**，然后使用**文档 ID**（哈希值）来证明文档的存在，或者从存储系统中检索文档。基于哈希的唯一 ID 的例子有 **Git** 和 **GitHub** 中的提交哈希——它是基于提交的内容（例如 `3c3be25bc1757ca99aba55d4157596a8ea217698`），和**比特币**地址（例如 `1BvBMSEYstWetqTFn5Au4m4GFg7xJaNVN2`）。

![](../.gitbook/assets/git-commit-logs.png)

In the above example the SHA-1 unique ID identifies a certain commit in GitHub.

在上面的示例中，SHA-1 唯一 ID 标识了 GitHub 中的某个提交。

## 伪随机数生成

**Pseudorandom generation** and key derivation. Hash values can serve as random numbers. A simple way to generate a random sequence is like this: start from a **random seed** \(entropy collected from random events, such like keyboard clicks or mouse moves\). Append "**1**" and calculate the hash to obtain the first random number, then append "**2**" and calculate the hash to obtain the second random number, etc. We shall give a Python example, implementing the described idea.

**伪随机生成**和密钥派生。哈希值可以作为随机数。生成随机序列的一种简单方法是这样的：从**随机种子**开始(从随机事件收集的熵，如键盘点击或鼠标移动)。添加“**1**”并计算哈希得到第一个随机数，然后添加“**2**”并计算哈希得到第二个随机数，等等。后续我们将给出一个 Python 示例来实现所描述的这个思想。

## 工作量证明算法

**Proof-of-work** \(PoW\) algorithms. Most proof-of-work algorithms calculate a hash value which is bigger than certain value \(known as mining difficulty\). To find this hash value, miners calculate billions of different hashes and take the biggest of them, because hash numbers are unpredictable. For example, the proof of work problem might be defined as follows: find a number `p`, such that `hash(x + p)` holds 10 zero bits at its beginning.

**工作量证明** （Proof-of-work, PoW）算法。大多数工作量证明算法要计算出一个哈希值大于某个值（称为挖掘难度）。为了找到这个哈希值，因为哈希数是不可预测的，矿工们计算了数十亿个不同的哈希值，然后取其中最大的一个。举个例子，可以定义一个工作量证明问题为：查找一个数字 `p`，使 `hash(x + p)` 从前往后包含 10 个零位。

## 加密哈希是现代编程的一部分

**Cryptographic hash functions** are so widely used, that they are often implemented as **build-in functions** in the standard libraries for the modern programming languages and platforms.

**加密哈希函数**的使用如此广泛，以至于它们通常在现代编程语言和平台的标准库中作为**内置函数**提供。
