# 前言

You are a **software developer**? And sometimes you need to use **cryptography** in your daily job, like hashes, encryption or digital signatures? And you think cryptography is complex and full of math and it is for nerds only? No, this is not true, every developer can learn **how to use cryptographic algorithms**. This book will show you how: with code examples and hands-on coding experience, with less math and more practice.

你是一名**软件开发人员**吗？ 你是否在日常工作中有时候需要使用**密码学**知识，例如哈希，加密或数字签名？你是否认为密码学太复杂并且充满了数学知识，只有“书呆子”能理解？ 不，事实并非如此，每个开发人员都可以学会“**如何使用加解密算法**“。本书将通过少量的数学知识、更多的示例代码与编程练习教会你如何使用。

It is not required to be а strong mathematician or even not strong mathematician to **understand the cryptographic concepts from the developer perspective**. This book will teach you the basics of **applied cryptography** in almost free of math style, following a step-by-step approach with lots of **code examples** and **practical exercises** \(hands-on experience\), just like when you learn Web development, databases or mobile apps. Yes, if you can learn Web development or RESTful services, you can learn the practical aspect of cryptography as well. It is just like learning a new API or a new Web development framework: you learn a combination of **concepts** + **APIs** \(crypto algorithms implemented in crypto libraries\) + **tools** + **best practices** how to use these APIs and tools.

**从开发人员的角度理解密码学概念**不需要你是一名优秀的数学家，甚至不必是一名数学家。就像学习 Web 开发，数据库或移动应用开发一样，本书将几乎没有数学推导，而是通过大量的**示例代码**和**实际练习**（动手实践）教你一步步地学会**应用密码学**的基础知识。这意味着如果你可以学会 Web 开发或 RESTful 服务，那么你同样可以学会实用密码学。你将学会**概念** + **API**（在加密库中实现的加密算法）+ **工具** + 使用这些 API 和工具的**最佳实践**，正如学习新的 API 或新的 Web 开发框架一样。

From this book you will learn **how to use cryptographic algorithms and cryptosystems** like hashes, MAC codes and key derivation functions \(KFD\), random generators, key exchange protocols, symmetric ciphers, encryption schemes, asymmetric cryptosystems, public-key cryptography, elliptic curves, digital signatures and quantum-safe crypto algorithms, together with modern cryptographic tools and libraries.

从这本书中，你将学会**如何使用密码算法和密码系统**，例如哈希、MAC代码和密钥推导函数（KFD）、随机生成器、密钥交换协议、对称密码、加密方案、非对称密码系统、公共密钥密码学、椭圆曲线、数字签名和量子安全加密算法，以及现代加密工具和库。

I am happy to publish this free **developer-friendly practical cryptography book**. It holds just **what developers need to know** in order to **use cryptography in their every day work**. It does not cover the internals of the algorithms and how to design symmetric ciphers, public-key cryptosystems or authentication schemes. It covers the basic understanding of the **core cryptographic concepts** and how to use them from developer's perspective: **libraries**, **tools**, **code examples**. This is what most developers need to know about cryptography. This is what this book gives to you for free.

我很高兴出版这本**对开发人员友好的实用密码学书籍**，它是用来学习**开发人员在日常工作中使用加密技术所需的知识**。它不涉及算法的内部原理或如何设计对称密码、公钥密码系统或身份验证方案，而是只涵盖了**核心密码学概念**的基本理解以及从开发人员的角度如何使用它们：**库**，**工具**，**示例代码**。这正是大多数开发人员需要了解的密码学知识。

## 这本书适合开发人员！

This book is designed **for developers** who write code every day, for **software engineers** who create software systems, Web applications, mobile apps and other software. It may be useful also for **DevOps engineers** who deal with crypto algorithms and write code to automate the IT infrastructure, for **system administrators**, who want to learn practical cryptography better, for **information security engineers**, who need to deal with cryptography every day and to know which ciphers and crypto algorithms are safe and which are broken, along with the possible attacks, for experienced **QA engineers** who perform security testing and code reviews about security and cryptography, and for many other **IT professionals**.

本书适用于以下每天编写代码的**开发人员**：开发软件系统、Web 应用程序、移动应用程序和其他软件的**软件工程师**；需要处理加密算法并编写代码以使 IT 基础架构自动化的 **DevOps 工程师**；希望更好地学习实用密码学的**系统管理员**；每天需要处理密码学并了解哪种密码和加密算法是安全的，哪些会被破坏以及可能的攻击手段信息的**信息安全工程师**；执行安全性测试和审查有关安全性和加密技术代码的经验丰富的 **QA 工程师**; 以及其他 **IT 专业人员**。

This book is about **using crypto algorithms** and cryptographic packages, not about designing ciphers, signature schemes and cryptosystems. You will learn how cryptosystems work \(without too much math\) and how to use them in your daily job. This book is not 100% free of math, but the complexity level is reduced to match the average developer's level, and complex concepts are explained in simplified and understandable style. This book is created **by developers for developers**, not by university professors or mathematicians. It is about coding in a smart way, with understanding the concepts and **using the crypto algorithms and crypto libraries the right way**. It is about the modern crypto algorithms and cryptographic techniques, used today in the software industry \(as of Nov 2018\).

这本书是介绍**使用密码算法**和密码库的，而不是介绍设计密码、签名方案或密码系统的。你将学会密码系统是如何工作（无需过多的数学推导）以及如何在日常工作中使用它们。本书并非完全没有数学知识，但降低了复杂度以适应普通开发人员的水平，并且以简化且易于理解的方式解释了复杂的概念。本书是**由开发人员为开发人员**创建的，而不是由大学教授或数学家创建的。它通过理解概念和**正确的加密算法和加密库使用方式**来学习如何编码。它涉及当今软件行业中使用的现代加密算法和加密技术（截至 2018 年 11 月）。

We assume that most developers use **higher level programming languages** \(such as JavaScript, Python, C\#, Java and PHP\), so most code examples in the book are given in **Python**, which can be translated to other languages with ease.

我们假设大多数开发人员使用**高级编程语言**（例如 JavaScript，Python，C＃，Java 和 PHP），因此本书中的大多数示例代码都是使用 **Python** 给出的，它们可以轻松地翻译为其他语言。

## 这本书完全免费！

The main book author **Dr. Svetlin Nakov** donates this book and its entire content and code examples **for free** to the developer and IT community as **open-source project**, under [the MIT license](https://opensource.org/licenses/MIT). Why? Because the main book author and the people behind this project believe that the **knowledge is for everyone** and it should be **shared for free**, because developers should learn to use cryptography the right way, because our world needs more secure software, because **sharing knowledge and skills for free** is the greatest miracle of the modern education.

书籍的主要作者 **Svetlin Nakov 博士**使用 [MIT 许可](https://opensource.org/licenses/MIT)，将这本书及其全部内容和示例代码作为**开源项目免费**提供给开发人员和 IT 社区。为什么这样做？因为书的主要作者和该项目的幕后工作人员认为**知识是为所有人提供的**，应该**免费共享**，因为开发人员应该以正确的方式学习使用加密技术，因为我们的世界需要更安全的软件，因为**免费共享知识和技能**是现代教育的最大奇迹。

For the same reasons, which drive the people to build **Wikipedia** and share knowledge for free, to publish open-source projects in **GitHub** and share code for free, to develop open-source software like **GNU/Linux** and **Firefox** and distribute it for free, I write and publish this open-source cryptography book for developers. I want to **share knowledge and skills**, to help the developers to become **better professionals**. I personally as a developer, when I learn a new technology, I search for free resources and code examples in Internet and I am happy that someone creates and shares them for free. Now it is time to return back to the society and to the developer community and this makes me happy.

出于同样的原因，这促使人们创立 **Wikipedia** 并免费共享知识、在 **GitHub** 上发布开源项目并免费共享代码以及开发 **GNU/Linux** 和 **Firefox** 等开源软件并免费分发，促使我为开发人员编写和出版此开源密码学书。我想**分享知识和技能**，以帮助开发人员变得**更加专业**。我个人是开发人员，当我学习一种新技术时，我从 Internet 上搜索免费的资源和示例代码，并且为有人免费创建和共享它们感到高兴。现在是时候回馈社会和开发者社区了，这让我感到高兴。

## About the Author: Dr. Svetlin Nakov

Dr. **Svetlin Nakov** \([http://www.nakov.com](http://www.nakov.com)\) is a passionate **software engineer**, inspirational **technical trainer** and tech **entrepreneur** from Bulgaria, experienced in broad range of languages, software technologies and platforms. He is co-founder of several highly successful **tech startups** and non-profit organizations and is a **technical advisor** in several successful blockchain **ICO projects**. Svetlin is training, innovation and inspiration manager at [**SoftUni**](https://softuni.org) - the largest tech education provider in South-Eastern Europe.

![](.gitbook/assets/svetlin-nakov-photo-face.jpg)

Svetlin Nakov has 20+ years of technical background as software engineer, software project manager, consultant, **trainer** and **entrepreneur** with rich experience with .NET, Java EE, information systems, databases, cryptography and software security, Web development, JavaScript, PHP, Python and software engineering. He is the leading **author of 15 books** on computer programming, software technologies, cryptography, C\#, Java, JavaScript, Python and tens of technical and scientific publications. He is a big fan of **knowledge sharing** and is proud Wikipedia contributor, free books author and open-source supporter.

Svetlin has been a **speaker** at hundreds of conferences, seminars, meetups, courses and other trainings in the United States, Singapore, Germany, Egypt, Bulgaria and other locations. He holds a **PhD** degree in computer science \(for his research on computational linguistics and machine learning\), several **medals** from the **International Informatics Olympiads** \(IOI\) and the Bulgarian **President’s award “John Atanasoff”**. He has been a part-time assistant professor / trainer in Sofia University, New Bulgarian University, the Technical University of Sofia, Ngee Ann Polytechnic \(Singapore\), Kingsland University \(USA\) and few others.

Currently **Svetlin Nakov** together with his partners drive the global expansion of the largest training center for software engineers in Bulgaria and the region – the [**Software University**](https://softuni.org), where he inspires and **teaches hundred of thousands of young people** in computer science, software development, information technologies and digital skills, and gives them a profession and a job.

## The History behind This Book

Svetlin Nakov together with tens of co-authors has created and published as open-source projects \(in the period 2004-2018\) **tens of technical books** about computer programming and software technologies \(see [http://www.introprogramming.info](http://www.introprogramming.info) and [http://www.nakov.com/books](http://www.nakov.com/books)\), most of which in Bulgarian language. In the last few years Svetlin switches to English and takes **global knowledge sharing initiative** for **better and accessible tech education**, demonstrated with creating and sharing free tech books, free tutorials, free tech webinars and seminars, conference talks and many other activities.

The book author **Svetlin Nakov** is involved with **applied cryptography** from 2005, when he published the book "_Java for Digitally Signing Documents of the Web_" \(in Bulgarian\), following his master thesis on a similar topic. Later Nakov is involved in his practice as software engineer, tech trainer and entrepreneur, with **cryptography**, **software security** and **blockchain** systems, and his technical expertise grows along with his experience. In 2018 he decides to write a **free book** to share his knowledge about cryptography and crypto algorithms from developer's perspective and donate this knowledge to the global dev community. The book takes 3 months to be written and gets published in Nov 2018. You can get a free copy from: [https://cryptobook.nakov.com](https://cryptobook.nakov.com).

## The Software University \(SoftUni\)

The development of this book is supported by the [**Software University \(SoftUni\)**](https://softuni.org): the biggest and most respected training center for software engineering and digital skills in the South-Eastern Europe, which gives high-quality tech education, practical skills, profession and job to tens of thousands of young people.

[![](.gitbook/assets/softuni-banner.jpg)](https://softuni.org)

**SoftUni** teaches software engineers in the [**Software University**](https://softuni.org) program, creative and design in the [**SoftUni Creative**](https://creative.softuni.bg) program, digital marketing in the [**SoftUni Digital**](https://digital.softuni.bg) program, programming and tech skills for kids in the [**SoftUni Kids**](https://kids.softuni.bg) program, runs a high school for digital skills [**SoftUni Svetlina**](https://svetlina.softuni.bg) and shares knowledge and skills through the [**SoftUni Foundation**](http://softuni.foundation) and its [**SoftUni Free**](http://free.softuni.org) tech educational portal.

## Why Yet Another Book on Cryptography?

Most books about cryptography on the market are written either in too **academic style** with a lot of theory and math or are **outdated** and do not describe the cryptography used today or are too small, **weak in content** and unfinished. Others are better, but are **not free** and accessible for everyone.

This book "**Practical Cryptography for Developers**" tries to compensate all above mentioned weak sides of the existing cryptography books on the market: its is **free**, **developer-friendly**, **comprehensive**, with less math and more **code examples**.

### Academic Cryptography Books

Many high-quality **academic cryptography books** exist on the market and some of them are **free**, but I can't recommend such a book to а developer. He will be bored and will start hating cryptography after the first chapter or two. Some examples:

* One of the strongest **academic book on cryptography concepts** is "[**A Graduate Course in Applied Cryptography**](https://crypto.stanford.edu/~dabo/cryptobook/)" \(by Dan Boneh and Victor Shoup\). It is excellent **free** book about **theoretical cryptography**, but is not for developers. It is full of theory, concepts, math and formulas. It does not provide code examples or recommended libraries for developers. Up to date \(published in 2017\).
* The "[**Crypto 101**](https://www.crypto101.io)" is a **free book on cryptography**, which is more **understandable for developers**. It provides more simple explanation for the core cryptographic concepts, but without code examples and recommended libraries and tools. Up to date \(published in 2017\).
* Тhe "[**Handbook of Applied Cryptography**](http://cacr.uwaterloo.ca/hac)" \(by Alfred J. Menezes, Paul C. van Oorschot and Scott A. Vanstone\) is excellent for higher degree students, but is **too academic for developers**. It is available for **free** and explains the theory and the cryptography concepts very well, with lots of high-level math, but it is definitely not for developers. It does not provide working code examples and does not refers the most used crypto libraries in the software industry. Slightly outdated \(published in 2001\).
* Yet another good **academic cryptography book** is "[**Understanding Cryptography: A Textbook for Students and Practitioners**](https://books.google.bg/books?id=f24wFELSzkoC)" \(by Christof Paar, Bart Preneel, Jan Pelzl\). Excellent book on **cryptography concepts**, well organized, with algorithms in pseudocode, but it is not for developers. It does not provide code examples and recommended libraries for developers. Almost up to date \(published in 2010\), not free.
* Yet another **academic book** on cryptographical concepts: "[**Practical Cryptography**](https://books.google.bg/books?id=ThVRAAAAMAAJ)" \(by Niels Ferguson and Bruce Schneier, 2003\). Provides deep concepts and explanations of the popular crypto algorithms, along with pseudo-code. Slightly outdated \(published in 2003\).

### Crypto Libraries and Their Documentation

Some **crypto libraries** try to provide **documentation** with crypto concepts and code examples, but they are typically **limited**, sometimes unfinished and not always consistently organized, with a lot of missing points and can serve to help you using certain library, but are not the best source to learn the cryptographic concepts.

Still, these documentations and manuals are **one of the best free learning resources** for developers who want to **use crypto algorithms**, especially experienced engineers with previous knowledge and skills in the area of cryptography. Examples of good documentation about crypto algorithms, coming with some crypto libraries:

* [**Nettle Documentation**](http://www.lysator.liu.se/~nisse/nettle/nettle.html) - contains very good description of the most popular cryptographic concepts and popular algorithms \(hashes, MAC, symmetric ciphers, signatures\) along with reliable and fast **C** implementation.
* [**PyCA / Cryptography Documentation**](https://cryptography.io/en/latest/hazmat/primitives/) - contains basic description of many cryptographic primitives \(like hashes, MAC codes, symmetric encryption, authenticated encryption, asymmetric algorithms, key exchange, KDF and others\) along with code examples in **Python**, demonstrating how to use the pyca/cryptography library APIs and its crypto algorithms.
* [**Libsodium Documentation**](https://download.libsodium.org/doc/) - combines API documentation with elements of cryptographic concepts. It is bound to the **C** language, used for the Libsodium project. Provides sample code examples.
* [**The Crypto++ Wiki**](https://www.cryptopp.com/wiki/) - explains in brief some cryptography concepts along with guidelines how to use the Crypto++ library and the **C++** classes, implementing certain crypto algorithms. Provides sample code examples.
* [**Botan - Developer's Manual**](https://botan.randombit.net/manual/) - a modern **C++** crypto-library, which comes with implementations of many modern crypto algorithms, along with documentation, which includes brief description of the underlying cryptographic concepts.
* [**Libgcrypt Manual**](https://gnupg.org/documentation/manuals/gcrypt/) - a cryptographic library, written in **C** as part of the GnuPG project. Comes with very light introduction to crypto concepts and a boring API documentation with almost no sample code.

### Practical Cryptography - Existing Books

To be honest, I conducted a **comprehensive research of the book market** \(in Nov 2018\) to find the best developer-friendly cryptography books. I was **deeply disappointed**! I almost didn't find any good practical book about **cryptography for programmers**, which I could recommend to a friend-developer \(not scientist or university student\) with confidence that this book is really good and is really what developers need: modern cryptography + simple explained concepts + code examples. I found **very good academic books** and a few **books for developers** \(rich of code examples\) with either not great quality or very focused on certain technology \(like a API reference or library manual\). Some of them were also outdated, but still valuable.

#### Free Cryptography Books for Developers

This is the list of **free books** about practical cryptography for developers:

* [**Practical Cryptography with Go**](https://leanpub.com/gocrypto/read) \(by Kyle Isom, published 2015\) - a mini-book on how to use cryptography with the **Go** language, full of code examples. It has **free edition** \(read online\) and **paid editions** \(PDF, EPUB, MOBI\). The book is good, but its scope is limited to describe some concepts very briefly and demonstrate how to use them with code examples. It covers modern symmetric ciphers \(like AES-GCM and XSalsa20-Poly1305\), key derivation \(PBKDF2 and Scrypt\), key exchange and ECDH, digital signatures \(ECDSA and Ed25519\), and few other concepts.
* [**The Laws of Cryptography with Java Code**](http://www.cs.utsa.edu/~wagner/lawsbookcolor/laws.pdf) \(by Neal Wagner, published 2003\) - academic-style book on cryptography with working Java examples, implementing certain crypto algorithms \(like the AES cipher and the RSA cryptosystem\).
* [**Cryptography in .NET Succinctly**](https://www.syncfusion.com/ebooks/cryptography_in_net_succinctly/cryptography-a-brief-history) \(by Dirk Strauss, 2017\) - a compilation of **.NET code examples** about using some cryptographic primitives like AES, hashes and RSA signatures from **C\#**. Looks more like a API reference than a serious book explaining when a how to use the mentioned cryptographic algorithms, the concepts of the underlying cryptosystems and the specifics of the underlying algorithms.

#### Non-Free Cryptography Books for Developers

I could list a few developer-friendly **books for practical cryptography** with code examples, which have only paid / commercial versions \(**no free edition**\). Most of them are too deeply bound to certain technology like C, C++, Java or JavaScript and don't explain the concepts well. Others have different focus. Some are outdated, some are quite new. This is the list of what I found from my research about developer-friendly crypto books:

* [**Serious Cryptography: A Practical Introduction to Modern Encryption**](https://books.google.bg/books?id=hLcrDwAAQBAJ) \(by by Jean-Philippe Aumasson\) - a strong book on cryptography, which combines academic approach with more practical approach, with some code examples in **Python**, but not for all concepts. Recent \(published in 2017\). Explains the modern cryptographic concepts and crypto-suits like AES-GCM, ChaCha20-Poly1305 and quantum-safe cryptography. This is maybe the best book of what I found.
* [**Secure Programming Cookbook for C and C++**](https://books.google.bg/books?id=aL3P3eJdiREC) \(by John Viega, Matt Messier\) - provides secure coding guidelines for **C++** developers, including topics from cryptography \(hashes, MAC codes, symmetric ciphers, RSA and DSA, random numbers\), with code examples \(published in 2009, slightly outdated\).
* [**Cryptography for Developers**](https://books.google.bg/books?id=VaiYIZHduXQC) \(by Tom Denis\) - provides solid fundamentals in cryptography and crypto algorithms, along with implementations in **C** and **assembler** with lots of code examples. Written in the middle between an academic style and a developer style. Covers hashes, HMAC, AES, slightly RSA and ECC. Slightly outdated \(published in 2007\).
* [**Beginning Cryptography with Java**](https://books.google.bg/books?id=WLLAD2FKH3IC) \(by David Hook\) - a reference for JCA, JCE, JSSE and the Bouncy Castle crypto library with lots of code examples in **Java** \(published in 2005, outdated\).
* [**Cryptography for JavaScript Developers: Web Cryptography API, SJCL**](https://books.google.bg/books?id=8oBxDwAAQBAJ) \(by Anish Nath\) - a reference full of code examples in **JS**, but does not explain the concepts like symmetric ciphers, authenticated encryption, etc. \(published in 2018\).
* [**Hands-On Cryptography with Python**](https://books.google.bg/books?id=LsNiDwAAQBAJ) \(by Samuel Bowne\) - nice mini book \(87 pages, published in 2018\) with lots of code examples in **Python**, but with very limited scope: hashes, AES and RSA. No signatures, no elliptic curves, no MAC and key derivation functions.
* [**Cryptography in C and C++**](https://books.google.bg/books?id=5cEYAAAAQBAJ) \(by Michael Welschenbach\) - guidelines how to implement crypto algorithms like AES and RSA in **C** / **C++**. No signatures, no elliptic curves, no MAC and key derivation functions. Published in 2005 \(outdated\).

The absence of **good free practical book about cryptography and crypto algorithms for developers with code examples** motivates me even more to share my knowledge and skills in a developer-friendly cryptography book. I am happy to be one of the first authors to publish a high-quality free book on practical cryptography for software engineers.

## What Does this Book Cover?

This book covers the most important modern cryptographic concepts, crypto algorithms and cryptographic constructions, used in the software industry, well illustraed and demonstrated with working code examples:

* Cryptographic **hash functions**: concepts, SHA-2, SHA-3, BLAKE2, RIPEMD160, code examples, collisions
* **MAC** codes: concepts, HMAC, CMAK, UMAC, applications, MAC-based random generators, code examples
* Key derivation functions \(**KDF**\): concepts, from password to encryption key, PBKDF2, Scrypt, Bcrypt, Linux crypt\(\), Argon2, code examples
* **Password encryption** techniques: from clear text, through hashing, to modern secure KDFs like Argon2
* Random numbers and **secure random generators**: concepts, entropy, secure random numbers, CSPRNG, code examples
* **Key exchange** techniques: key establishment and key agreement, Diffie–Hellman Key Exchange \(DHKE\) and Elliptic Curve Diffie–Hellman \(ECDH\) with code examples
* **Encryption** concepts: symmetric and asymmetric ciphers, secret keys, symmetric encryption, encryption schemes, public-key cryptosystems, private and public keys, hybrid encryption, digital signatures
* Modern **symmetric key ciphers**: concepts, block ciphers and stream ciphers, cipher block modes \(CBC, CTR, GCM\), the AES \(Rijndael\) cipher, the Salsa20 / ChaCha20 ciphers, with code examples
* Symmetric encryption **constructions**: authenticated encryption, AES-256-GCM, ChaCha20-Poly1307, AES-256-CTR-HMAC, with code examples
* **Asymmetric key ciphers** and public-key cryptosystems: the RSA cryptosystem \(RSA key pairs, encryption, decryption\), ECC \(elliptic curve cryptography, EC points and multiplication, named curves\), ECDH \(elliptic-curve Diffie–Hellman\) key exchange, code examples
* **Elliptic curves**: widely used named curves like secp256k1, P-256, P-521, Curve25519, Curve448-Goldilocks, with code examples
* **Integrated encryption** schemes: combining public-key cryptography with symmetric encryption algorithms, the ECIES hybrid encryption scheme, with code examples
* **Digital signature** algorithms: concepts, signing messages, verifying signatures, RSA signatures, ECDSA and EdDSA
* **Quantum-safe cryptography**: which classical cryptosystems are quantum-broken and which are quantum-safe, quantum-safe signatures and quantum-safe key exchange algorithms, SPHINCS+, NewHope and others, with code examples
* Other **cryptographic concepts**: digital certificates, TLS \(Transport Layer Security\), one-time passwords \(OTP\), external authentication and OAuth
* **Crypto libraries** and packages for developers: cryptography in JavaScript, C\#, Java, Python, C and C++
* A lot of **code examples** and exercises, following each major section

## Why Python is Used for the Examples?

**Python** is one of easiest languages, a language, which is **readable** and **understandable** by all developers \(even devs who has zero experience with it\). The idea of the **code examples** is to illustrate the crypto algorithms, encryption schemes and other cryptography concepts in action, not to promote certain library, API, language or technology.

Use the **code examples** as reference only, as guideline of how your code might look like, and adopt them to your favorite language and framework. Don't directly copy and paste the code examples. Sometimes we use a library, which is more user friendly and easier to install and use, instead of a faster and more reliable library from another vendor. Sometimes we use **hex-encoded** keys, ciphertexts, signatures and other values, in order to display them easier on the console, but in practice most apps will use binary encodings for increased performance and reduced network overhead.

You are free to adopt the code examples to other languages. At the end of the book we have given examples how to use cryptography in the most popular programming languages: **JavaScript**, **C\#**, **Java** and **Python**. We skip giving examples with the lower level languages like **C** and **C++** because they work better for library writers \(to implement efficiently certain algorithm\), not for app developers. **C** and **C++** are more complex to setup and build, need more effort to manage the project dependencies and are more prone to errors.

Most **application developers** \(e.g. Web devs, back-end devs, mobile devs and front-end devs\) **use higher level languages** \(like JS, Python, C\#, Java, PHP and Go\), but all of them will **understand the Python code** from the examples. If the code was given in C, it would be longer, more complex and less readable.

**Python is widely supported** everywhere \(in Linux, Windows, Mac, on mobile devices and microcontrollers\). All examples can also run online in a virtual machine in **online Python environments** such as: [**Repl.it**](https://repl.it/languages/python3) and [**PythonAnywhere**](https://www.pythonanywhere.com).

## How to Read This Book?

The recommended way to read this is **topic by topic** \(from the start to the end\). You may skip chapters and sections that you don't like, but please pass through them, because the content has internal dependencies.

Play with the **code examples**: run them, modify them, break them, explore and experiment with the code and **learn by playing**.

Try to solve the **practical exercises** in chapter. Developers **learn best by writing code** and this is what I recommend. You are given well described exercise problems, with clear input and output, covering well the content after each major section.

Now, start your developer **journey into the modern practical cryptography**. Enjoy the book!

