# JavaScript实现凯撒加密

```javascript
function caesarCipherEncrypt(message, shift) {
    let encryptedMessage = '';
    for (let i = 0; i < message.length; i++) {
        let charCode = message.charCodeAt(i);
        // 判断字符是否是字母
        if (charCode >= 65 && charCode <= 90) { // 大写字母 A-Z
            charCode = ((charCode - 65 + shift) % 26) + 65;
        } else if (charCode >= 97 && charCode <= 122) { // 小写字母 a-z
            charCode = ((charCode - 97 + shift) % 26) + 97;
        }
        encryptedMessage += String.fromCharCode(charCode);
    }
    return encryptedMessage;
}

// 测试加密函数
let message = "Hello, World!";
let shift = 3;
let encryptedMessage = caesarCipherEncrypt(message, shift);
console.log("Encrypted message:", encryptedMessage); // 输出: Khoor, Zruog!
```

在这个例子中，`caesarCipherEncrypt`函数接受两个参数：要加密的消息和移位量（shift）。它遍历消息中的每个字符，并根据字符的ASCII码值来进行移位加密。对于字母字符，它将其转换为ASCII码值，应用移位操作后，再转换回字符。非字母字符保持不变。

你可以尝试不同的消息和移位量来测试加密函数的效果。