# 密码学——概述

## 现代密码学概述

**Cryptography** has evolved from its first attempts \(thousands years ago\), through the first successful cryptographic algorithms for developers \(like the now retired MD5 and DES\) to modern crypto algorithms \(like SHA-3, Argon2 and ChaCha20\).

**密码学**已经从其最初的尝试（数千年前）发展到了第一个成功的开发人员密码算法（例如现已退休的 MD5 和 DES），再到现代密码算法（例如 SHA-3，Argon2 和 ChaCha20）。

Let's first introduce very shortly the basic **cryptography concepts**, that developers should know, like cryptographic **hash functions** \(SHA-256, SHA3, RIPEMD and others\), **HMAC** \(hashed message authentication code\), password to **key derivation** functions \(like **Scrypt**\), the Diffie-Hellman key-exchange protocol, **symmetric key** encryption schemes \(like the **AES** cipher with CBC and CTR block modes\) and **asymmetric key** encryption schemes with public and private keys \(like the **RSA** cipher and elliptic curves-based cryptography / **ECC**, the secp256k1 curve and the Ed25519 cryptosystem\), **digital signatures** and **ECDSA**, as well as the concept of **entropy** and secure **random number** generation and **quantum-safe cryptography**.

让我们首先简要介绍一下开发人员应该知道的基本**密码学概念**，例如密码**哈希函数**（SHA-256，SHA3，RIPEMD 等），**HMAC**（hashed message authentication code, 哈希消息验证码），**密钥派生**函数的密码（例如 Scrypt）， Diffie-Hellman 密钥交换协议，**对称密钥**加密方案（例如具有 CBC 和 CTR 块模式的 AES 密码）和具有公钥和私钥的**非对称密钥**加密方案（例如基于椭圆曲线加密的 RSA 与基于 secp256k1 曲线和 Ed25519 密码系统的 ECC），**数字签名**和 **ECDSA**，以及**熵**和安全**随机数生成**以及**量子安全密码学**的概念。

### Encrypt / Decrypt Message - Live Demo

As a simple **example**, we shall demonstrate message **encryption** + **decryption** using the **AES** encryption algorithm. Play with this online tool: [https://aesencryption.net](https://aesencryption.net).

我们可以使用此在线工具：[https://aesencryption.net](https://aesencryption.net) 演示一个使用 **AES** 加密算法对消息进行**加密** + **解密**的简单示例。

![](.gitbook/assets/encrypt-decrypt-live-demo.jpg)

We shall learn later that behind this simple **AES encryption**, there are **many algorithms and settings** hidden inside, like password to key-derivation function and its parameters, block cipher mode, cipher initial vector, message authentication code and others.

稍后我们将了解到，在这种简单的 **AES 加密**背后，内部隐藏了**许多算法和设置**，例如密钥派生函数及其参数，分组密码模式，密码初始向量，消息验证码等。

## 密码学是什么？

**Cryptography** is the science of providing **security** and **protection** of information. It is used everywhere in our digital world: when you open a Web site, send an email or connect to the WiFi network. That's why developers should have **at least basic understanding of cryptography** and how to use crypto algorithms and crypto libraries, to understand hashing, symmetric and asymmetric ciphers and encryption schemes, as well as digital signatures and the cryptosystems and algorithms behind them.

**密码学**是一门提供**信息安全**和**信息保护**的科学。它在我们的数字世界中无处不在：浏览网页、发送电子邮件或连接 WiFi 网络时都有它有存在。这就是为什么开发人员**至少应该对密码学有基本的了解**，了解如何使用密码算法和密码库，了解哈希、对称和非对称密码和加密方案，以及了解数字签名及其背后的密码系统和算法。

### 加密和密钥

Cryptography deals with **storing and transmitting data in a secure way**, such that only those, for whom it is intended, can read and process it. This may involve **encrypting and decrypting data** using symmetric or asymmetric encryption schemes, where one or more **keys** are used to transform data from plain to encrypted form and back.

密码学保障**以安全的方式进行数据的存储和传输**，使得只有那些预期的用户才能读取和处理数据。这可能涉及使用对称或非对称加密方案**对数据进行加密和解密**，其中一个或多个**密钥**用于数据在原始格式与加密格式之间的转换。

**Symmetric encryption** \(like AES, Twofish and ChaCha20\) uses the same key to encrypt and decrypt messages, while **asymmetric encryption** uses a **public-key cryptosystem** \(like RSA or ECC\) and a key-pair: public key \(encryption key\) and corresponding private key \(decryption key\). Encryption algorithms are often combined in encryption schemes \(like AES-256-CTR-HMAC-SHA-256, ChaCha20-Poly1305 or ECIES-secp256k1-AES-128-GCM\).

**对称加密**（例如 AES，Twofish 和 ChaCha20）使用相同的密钥来加密和解密信息，而**非对称加密**使用**公用密钥密码系统**（例如 RSA 或 ECC）和密钥对：公用密钥（加密密钥）和相应的私有密钥（解密密钥）。加密算法通常结合在加密方案中（例如 AES-256-CTR-HMAC-SHA-256，ChaCha20-Poly1305 或 ECIES-secp256k1-AES-128-GCM）。

Cryptography deals with **keys** \(large secret numbers\) and in many scenarios these **keys are derived** from numbers, passwords or passphrases using **key derivation algorithms** \(like PBKDF2 and Scrypt\).

密码学要解决生成**密钥**（用于保密的大数字）的问题，在许多情况下，这些密钥是使用**密钥派生算法**（例如 PBKDF2 和 Scrypt）从数字，密码或密码短语中**派生**的。

### 数字签名和消息认证

Cryptography provides means of **digital signing of messages** which guarantee message authenticity, integrity and non-repudiation. Most digital signature algorithms \(like DSA, ECDSA and EdDSA\) use **asymmetric key pair** \(private and public key\): the message is **signed** by the private key and the signature is **verified** by the corresponding public key. In the bank systems **digital signatures** are used to sign and approve payments. In blockchain signed transactions allow users to transfer a blockchain asset from one address to another.

密码学提供了**对消息进行数字签名**的方法，可以保证消息的真实性，完整性和不可否认性。 大多数数字签名算法（例如 DSA，ECDSA 和 EdDSA）都使用**非对称密钥对**（私钥和公钥）：消息由私钥**签名**，签名由相应的公钥**验证**。 在银行系统中，**数字签名**用于签署和批准付款。 在区块链中，签名交易允许用户将区块链资产从一个地址转移到另一个地址。

Cryptography deals with **message authentication** algorithms \(like HMAC\) and message authentication codes \(MAC codes\) to prove message authenticity, integrity and authorship. Authentication is used side by side with encryption, to ensure secure communication.

密码学提供了**消息验证**算法（如 HMAC）和消息验证码（MAC 码），以证明消息的真实性、完整性和原作者身份。认证与加密一起使用，以确保安全的通信。

### 安全随机数

Cryptography uses **random numbers** and deals with **entropy** \(unpredictable randomness\) and secure generation of random numbers \(e.g. using CSPRNG\). **Secure random numbers** are unpredictable by nature and developers should care about them, because broken random generator means compromised or hacked system or app.

密码学使用**随机数**，处理**熵**（不可预测的随机性）和随机数的安全生成（例如使用 CSPRNG）。**安全的随机数**本质上是不可预测的，开发者应该关心它们，因为无效的随机数生成器意味着系统或应用程序可被入侵。

### 密钥交换

Cryptography defines **key-exchange algorithms** \(like Diffie-Hellman key exchange and ECDH\) and **key establishment schemes**, used to securely establish encryption **keys** between two parties that intend to transmit messages securely using **encryption**. Such algorithms are performed typically when a new secure connection between two parties is established, e.g. when you open a modern Web site or connect to the WiFi network.

密码学定义了**密钥交换算法**（如 Diffie-Hellman 密钥交换和 ECDH）和**密钥建立方案**，用于在希望使用**加密**安全传输消息的双方之间安全地建立加密**密钥**。这种算法通常在双方之间建立新的安全连接时执行，例如，当您打开一个现代网站或连接到 WiFi 网络时。

### 加密哈希和密码哈希

Cryptography provides **cryptographic hash functions** \(like SHA-3 and BLAKE2\), which transform messages to **message digest** \(hash of fixed length\), which cannot be reversed back to the original message and almost uniquely identifies the input. In **blockchain** systems, for example, hashes are used to generate blockchain addresses, transaction ID and in many other algorithms and protocols. In **Git** cryptographic hashes are used for generating unique ID for files and commits.

密码学提供**加密的哈希函数**（如 SHA-3 和 BLAKE2），它们将消息转换为**消息摘要**（固定长度的哈希），消息摘要不能将反推得到原始消息，并且几乎惟一地标识输入。例如，在**区块链**系统中，哈希用于生成区块链地址、事务 ID 和许多其他算法和协议中。在 **Git** 中，密码哈希用于生成文件和提交的唯一 ID。

**Password hashing** and password to **key derivation functions** \(like Scrypt and Argon2\) protect user passwords and password encrypted documents and data by securely deriving a hash \(or key\) from a text-based passwords, injecting random parameters \(salt\) and using a lot of iterations and computing resources to make password cracking slow.

**密码哈希**和**密钥派生函数**（如 Scrypt 和 Argon2）通过安全地从基于文本的密码派生哈希（或密钥）、注入随机参数（salt）和使用大量迭代和计算资源来降低密码破解的速度，从而保护用户密码和密码加密的文档和数据。

### 密码学中的混淆与扩散

In cryptography the hashing, encryption algorithms and random generators follow the Shannon's principles of[ confusion and diffusion](https://en.wikipedia.org/wiki/Confusion_and_diffusion). **Confusion** means that each bit in the output form a cipher should depend on several parts of the key and input data and thus direct mapping cannot be established. **Diffusion** means that changing one bit in the input should change approximately half of the bits in the output. These principles are incorporated in most hash functions, MAC algorithms, random number generators, symmetric and asymmetric ciphers.

在密码学中，哈希、加密算法和随机生成器遵循香农的[混淆和扩散原则](https://en.wikipedia.org/wiki/Confusion_and_diffusion)。**混淆**意味着密码输出形式中的每一比特位应该依赖于密钥和输入数据的几个部分，因此不能建立直接映射。**扩散**意味着改变输入中的一个比特将会改变输出中大约一半的比特。该原则包含在大多数哈希函数、MAC 算法、随机数生成器、对称和非对称密码中。

### 密码库

Developers should know the modern **cryptographic libraries** for their programming language and platform and how to use them. Developing with cryptography requires **understanding of the crypto-concepts**. Copy / pasting code from Internet or following an example from a blog may lead to insecure design and weak security. Cryptographic libraries are very useful, but you should **understand the concepts** first, then choose appropriate combination of algorithms and adjust carefully their parameters.

开发人员应该了解用于其编程语言和平台的**现代密码库**，以及如何使用它们。使用密码技术开发需要**理解密码学概念**。从互联网上复制/粘贴代码或从博客上复制示例代码可能会引入不安全的设计和薄弱的安全性。密码库非常有用，但是您应该首先**理解这些概念**，然后选择适当的算法组合并仔细调整它们的参数。
