# HMAC 计算——示例

In **Python** we can **calculate HMAC** codes as follows \(using the `hashlib` and `hmac` libraries\):

在 **Python** 中，我们可以如下**计算 HMAC**码（使用 `hashlib` 和 `hmac` 库）：

```python
import hashlib, hmac, binascii

def hmac_sha256(key, msg):
  return hmac.new(key, msg, hashlib.sha256).digest()

key = b"12345"
msg = b"sample message"
print(binascii.hexlify(hmac_sha256(key, msg)))
```

Run the above code example: [https://repl.it/@nakov/HMAC-SHA256-Examples](https://repl.it/@nakov/HMAC-SHA256-Examples-in-Python).

可在此链接中运行该示例代码：[https://repl.it/@nakov/HMAC-SHA256-Examples](https://repl.it/@nakov/HMAC-SHA256-Examples-in-Python)。

The above code will calculate and print the expected HMAC code \(like in our previous example\):

上面的代码将计算并打印预期的 HMAC 代码（如我们之前的示例中所示）：

```text
ee40ca7bc90df844d2f5b5667b27361a2350fad99352d8a6ce061c69e41e5d32
```

Try the code yourself and play with it.

你可以尝试以上代码并修改试试。
