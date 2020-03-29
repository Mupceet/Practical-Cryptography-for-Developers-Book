# MAC 和密钥派生

**Message authentication codes** \(**MAC**\), **HMAC** \(hash-based message authentication code\) and **KDF** \(key derivation functions\) play important role in cryptography. Let's explain when we need **MAC**, how to calculate **HMAC** and how it is related to key derivation functions.

**消息认证码**（**MAC**），**HMAC**（基于哈希的消息认证码）和 **KDF**（密钥派生功能，key derivation functions）在加密中起着重要的作用。 让我们解释一下何时需要 **MAC**，如何计算 **HMAC** 以及其与密钥派生函数的关系。

## 消息认证码（MAC）

**M**essage **A**uthentication **C**ode \(**MAC**\) is cryptographic code, calculated by given **key** and given **message**:

消息认证码（**M**essage **A**uthentication **C**ode，**MAC**）是由给定**密钥**和给定**消息**计算得出的密码：

```text
auth_code = MAC(key, msg)
```

Typically, it behaves **like a hash function**: a minor change in the message or in the key results to totally different **MAC value**. It should be practically infeasible to change the key or the message and get the same **MAC value**. MAC codes, like hashes, are **irreversible**: it is impossible to recover the original message or the key from the MAC code. MAC algorithms are also known as "**keyed hash functions**", because they behave like a hash function with a key.

通常，它的行为**类似于哈希函数**：消息或密钥的微小变化将导致 **MAC 值**完全不同。 更改密钥或消息并得出相同的 **MAC 值**实际上是不可行的。 MAC 值像哈希值一样是**不可逆**的：无法从 MAC 值中恢复原始消息或密钥。 MAC 算法也称为“**键控哈希函数**”，因为它们的行为类似于带有键值的哈希函数。

For example, the MAC code can be calculated by the **HMAC-SHA256** algorithm like this:

例如，可以通过 **HMAC-SHA256** 算法计算 MAC 值，如下所示：

```text
HMAC-SHA256('key', 'some msg') = 32885b49c8a1009e6d66662f8462e7dd5df769a7b725d1d546574e6d5d6e76ad
```

The above HMAC-SHA256 calculation can be coded in Python like this:

上述 HMAC-SHA256 计算可用 Python 编码如下：

```python
import hashlib, hmac, binascii

mac = hmac.new(b'key', b'some msg', hashlib.sha256).digest()
print(binascii.hexlify(mac))
```

Run the above code example: [https://repl.it/@nakov/HMAC-SHA256-in-Python](https://repl.it/@nakov/HMAC-SHA256-in-Python).

运行上述的示例代码：[https://repl.it/@nakov/HMAC-SHA256-in-Python](https://repl.it/@nakov/HMAC-SHA256-in-Python)。

The MAC code is **digital authenticity code**, like a **digital signature**, but with **pre-shared key**. We shall learn more about digital signing and digital signatures later.

MAC 值是**数字认证码**，类似于**数字签名**，但需要**预共享密钥**。稍后我们将学习更多关于数字签名的内容。

## MAC 算法

Many **algorithms** for calculating message authentication codes \(MAC\) exist in modern cryptography. The most popular are based on **hashing** algorithms, like [**HMAC**](https://en.wikipedia.org/wiki/HMAC) \(Hash-based MAC, e.g. HMAC-SHA256\) and [**KMAC**](https://www.cryptosys.net/manapi/api_kmac.html) \(Keccak-based MAC\). Others are based on **symmetric ciphers**, like [**CMAC**](https://en.wikipedia.org/wiki/One-key_MAC) \(Cipher-based MAC\), [**GMAC**](https://en.wikipedia.org/wiki/Galois/Counter_Mode) \(Galois MAC\) and [**Poly1305**](https://en.wikipedia.org/wiki/Poly1305) \(Bernstein's one-time authenticator\). Other MAC algorithms include [**UMAC**](https://en.wikipedia.org/wiki/UMAC) \(based on universal hashing\), [**VMAC**](https://en.wikipedia.org/wiki/VMAC) \(high-performance block cipher-based MAC\) and [**SipHash**](https://en.wikipedia.org/wiki/SipHash) \(simple, fast, secure MAC\).

现代密码学中存在许多计算消息认证码（MAC）的**算法**。最流行的是基于**哈希**算法的，比如 [**HMAC**](https://en.wikipedia.org/wiki/HMAC)（基于哈希的 MAC，例如 HMAC-sha256）和 [**KMAC**](https://www.cryptosys.net/manapi/api_kmac.html)（基于 Keccak 的 MAC）。其他一些基于**对称加密**，如 [**CMAC**](https://en.wikipedia.org/wiki/One-key_MAC)（基于密码的 MAC）、[**GMAC**](https://en.wikipedia.org/wiki/Galois/Counter_Mode)（Galois MAC）和 [**Poly1305**](https://en.wikipedia.org/wiki/Poly1305)（Bernstein 的一次性身份验证器)。其他的 MAC 算法包括 [**UMAC**](https://en.wikipedia.org/wiki/UMAC)（基于通用哈希）、[**VMAC**](https://en.wikipedia.org/wiki/VMAC)（基于高性能块密码的 MAC）和 [**SipHash**](https://en.wikipedia.org/wiki/SipHash) （简单、快速、安全的 MAC）。

## 什么时候需要 MAC 值?

A sample scenario for using MAC codes is like this:

使用MAC代码的场景示例如下：

* Two parties exchange somehow a certain secret **MAC key** \(pre-shared **key**\).
* 双方以某种方式交换保密的 MAC 密钥（预共享密钥）。
* We receive a **msg** + **auth\_code** from somewhere \(e.g. from Internet, from the blockchain, or from email message\).
* 我们从某个地方（例如从互联网、区块链或电子邮件）接收到一个消息和验证码。
* We want to be sure that the **msg** is **not tampered**, which means that both the **key** and **msg** are correct and match the MAC code.
* 我们想确认消息没有被篡改，即密钥和消息都是正确的，并且与 MAC 码匹配。
* In case of **tampered message**, the MAC code will be incorrect.
* 如果消息被篡改，MAC 码将不正确。

![](../.gitbook/assets/mac-message-authentication-code.png)

## 认证加密：使用 MAC 加密/解密消息

Another scenario to use **MAC codes** is for [**authenticated encryption**](https://en.wikipedia.org/wiki/Authenticated_encryption)**:** when we **encrypt a message** and we want to be sure the **decryption password is correct** and the decrypted message is the same like the original message before encryption.

使用 **MAC 码**的另一个场景是用于[认证加密](https://en.wikipedia.org/wiki/Authenticated_encryption)：我们加密一条消息时，我们想确保有正确的解密密码，并且解密后的消息与加密前的原始消息相同。

* First, we **derive a key** from the password. We can use this key for the MAC calculation algorithm \(directly or hashed for better security\).
* 首先，我们从密码中得到一个**派生密钥**。我们可以将此密钥用于 MAC 计算算法（直接使用或使用哈希以获得更好的安全性）。
* Next, we **encrypt the message** using the derived key and store the ciphertext in the output.
* 接下来，我们使用派生密钥**加密消息**并将密文存储在输出中。
* Finally, we calculate the **MAC code** using the derived key and the original message and we append it to the output.
* 最后，我们使用派生密钥和原始消息来计算 **MAC码**，并将其附加到输出中。

When we **decrypt the encrypted message** \(ciphertext + MAC\), we proceed as follows:

当我们**解密加密的消息**（密文+MAC）时，我们按如下步骤进行：

* First, we **derive a key** from the password, entered by the user. It might be the correct password or wrong. We shall find out later.
* 首先，我们从用户输入的密码中得到**派生密钥**。密码可能是正确的，也可能是错误的。我们稍后可以确认。
* Next, we **decrypt the message** using the derived key. It might be the original message or incorrect message \(depends on the password entered\).
* 接下来，我们使用派生密钥**解密消息**。它可能是原始消息，也可能是错误消息（这取决于输入的密码）。
* Finally, we calculate a **MAC code** using the derived key + the decrypted message.
* 最后，我们使用派生密钥和解密的消息计算 **MAC 码**。
  * If the calculated MAC code matches the MAC code in the encrypted message, the **password is correct**.
  * 如果计算出的 MAC 码与加密消息中的 MAC 码匹配，则**密码正确**。
  * Otherwise, it will be proven that the decrypted message is not the original message and this means that the **password is incorrect**
  * 否则，将证明解密后的消息不是原始消息，这意味着**密码不正确**。

Some **authenticated encryption algorithms** \(such as **AES-GCM** and **ChaCha20-Poly1305**\) integrate the MAC calculation into the encryption algorithm and the MAC verification into the decryption algorithm. We shall learn more about these algorithms later.

一些**认证加密算法**（如 **AES-GCM** 和 **ChaCha20-Poly1305**）将 MAC 计算集成到加密算法中，将MAC 验证集成到解密算法中。我们稍后将进一步了解这些算法。

The MAC is stored along with the ciphertext and it **does not reveal** the password or the original message. Storing the MAC code, visible to anyone is safe, and after decryption, we know whether the message is the original one or not \(wrong password\).

MAC 与密文一起存储**不会揭示**密码或原始消息。存储任何人都能看到的 MAC 码是安全的，解密后，我们可以知道消息是否是原始消息（密码是否正确）。

## 基于 MAC 的伪随机发生器

Another application of MAC codes is for **pseudo-random generator** functions. We can start from certain **salt** \(constant number or the current date and time or some other randomness\) and some **seed** number \(last random number generated, e.g. **0**\). We can calculate the **next\_seed** as follows:

MAC 码的另一个应用是用于**伪随机发生器**函数。我们可以从某个**盐**（常数或当前日期和时间或其他一些随机数）和某个**种子**数（最近生成的随机数，例如 0）开始。我们可以如下计算**下一个种子**：

```text
next_seed = MAC(salt, seed)
```

This **next pseudo-random number** is "randomly changed" after each calculation of the above formula and we can use it to generate the next random number in certain range. We shall demonstrated a fully working example in the "[Secure Random Generators](../secure-random-generators/pseudo-random-numbers-examples.md)" chapter.

在上述公式每次计算之后，该**下一个伪随机数**将“随机更改”，我们可以使用它来生成特定范围内的下一个随机数。 我们将在“[安全随机生成器](../secure-random-generators/pseudo-random-numbers-examples.md)”一章中演示一个完整的示例。

