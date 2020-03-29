# HMAC 与密钥派生

Simply calculating `hash_func(key + msg)` to obtain a MAC \(message authentication code\) is considered **insecure** \(see the [details](https://en.wikipedia.org/wiki/HMAC#Design_principles)\). It is recommended to use the **HMAC algorithm instead**, e.g. `HMAC-SHA256` or `HMAC-SHA3-512` or other secure MAC algorithm.

简单地计算 h`ash_func(key+msg)`以获得 MAC（消息认证码）被认为是**不安全**的（请参阅[详细信息](https://en.wikipedia.org/wiki/HMAC#Design_principles)）。建议改用 **HMAC 算法**，例如 `HMAC-SHA256` 或 `HMAC-SHA3-512` 或其他安全 MAC 算法。

## 什么是 HMAC？

[**HMAC**](https://en.wikipedia.org/wiki/HMAC) = **H**ash-based **M**essage **A**uthentication **C**ode \(MAC code, calculated using a cryptographic hash function\):

[**HMAC**](https://en.wikipedia.org/wiki/HMAC) = **H**ash-based **M**essage **A**uthentication **C**ode（MAC 码，使用加密哈希函数计算）：

```text
HMAC(key, msg, hash_func) -> hash
```

The results MAC code is a **message hash** mixed with a secret key. It has the cryptographic properties of hashes: **irreversible**, **collision resistant**, etc.

结果 MAC 码是一个混合了密钥的消息哈希。它具有哈希的加密特性：**不可逆**、**抗碰撞**等。

The `hash_func` can be any cryptographic hash function like `SHA-256`, `SHA-512`, `RIPEMD-160`, `SHA3-256` or `BLAKE2s`.

`hash_func` 可以是任何加密哈希函数，例如 `SHA-256`, `SHA-512`, `RIPEMD-160`, `SHA3-256` 或 `BLAKE2s`。

**HMAC** is used for message **authenticity**, message **integrity** and sometimes for **key derivation**.

**HMAC** 用于验证消息**真实性**，消息**完整性**，有时还用于**密钥派生**。

## 密钥派生函数（KDF）

**Key derivation function** \(KDF\) is a function which transforms a variable-length password to fixed-length key \(sequence of bits\):

**密钥派生函数**（Key Derivation Functions， KDF）是将可变长度密码转换为固定长度密钥（位序列）的函数：

```text
function(password) -> key
```

As **very simple KDF function**, we can use SHA256: just hash the password. Don't do this, because it is **insecure**. Simple hashes are vulnerable to **dictionary attacks**.

作为**非常简单的 KDF 函数**，我们可以使用 SHA256：仅对密码进行哈希处理。不要这样做，因为它是**不安全的**。简单的哈希很容易受到**字典攻击**。

As more complicated KDF function, you can derive a password by calculating **HMAC\(salt, msg, SHA256\)** using some random value called "**salt**", which is stored along with the derived key and used later to derive the same key again from the password.

作为更复杂的 KDF 函数，我们可以通过使用一些称为“**盐**”的随机值来计算 **HMAC（salt，msg，SHA256）**来派生密钥，该随机值与派生密钥一起存储，用于以后再次从密码中派生相同的密钥。

Using **HKDF \(HMAC-based key derivation\)** for key derivation is **less secure** than modern KDFs, so experts recommend using stronger key derivation functions like [PBKDF2](https://en.wikipedia.org/wiki/PBKDF2), [Bcrypt](https://en.wikipedia.org/wiki/Bcrypt), [Scrypt](https://en.wikipedia.org/wiki/Scrypt) and [Argon2](https://en.wikipedia.org/wiki/Argon2). We shall discuss all these KDF functions later.

与现代 KDF 函数相比，使用 **HKDF（基于 HMAC 的密钥派生）**进行密钥派生的**安全性较低**，因此专家建议使用更强大的密钥派生函数，例如 [PBKDF2](https://en.wikipedia.org/wiki/PBKDF2)， [Bcrypt](https://en.wikipedia.org/wiki/Bcrypt)， [Scrypt](https://en.wikipedia.org/wiki/Scrypt) 和 [Argon2](https://en.wikipedia.org/wiki/Argon2)。稍后我们将讨论这些 KDF 函数。

## HMAC 计算——示例

To get a better idea of **HMAC** and how it is calculated, try this online tool: [https://www.freeformatter.com/hmac-generator.html](https://www.freeformatter.com/hmac-generator.html)

要更好地了解 **HMAC** 及其计算方式，请尝试此在线工具：[https://www.freeformatter.com/hmac-generator.html](https://www.freeformatter.com/hmac-generator.html)

![](../.gitbook/assets/hmac-online.png)

Play with calculating **HMAC\('sample message', '12345', 'SHA256'\)**:

尝试计算 **HMAC\('sample message', '12345', 'SHA256'\)**：

```text
HMAC('sample message', '12345', 'SHA256') =
  'ee40ca7bc90df844d2f5b5667b27361a2350fad99352d8a6ce061c69e41e5d32'
```

Try the above example yourself.

可自行尝试如上示例代码。
