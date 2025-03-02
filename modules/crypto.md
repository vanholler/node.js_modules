# Модуль crypto

Модуль для работы с криптографией, включая хеширование, шифрование и создание цифровых подписей. Он предоставляет различные функции для обеспечения безопасности данных.

## Методы модуля crypto

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `crypto.createHash(algorithm)` | Создает объект хеширования с заданным алгоритмом (например, 'sha256'). |
| `crypto.createHmac(algorithm, key)` | Создает объект HMAC с заданным алгоритмом и ключом.                |
| `crypto.createCipher(algorithm, password)` | Создает объект шифрования с заданным алгоритмом и паролем.      |
| `crypto.createDecipher(algorithm, password)` | Создает объект расшифровки с заданным алгоритмом и паролем.     |
| `crypto.createSign(algorithm)` | Создает объект для создания цифровой подписи с заданным алгоритмом.   |
| `crypto.createVerify(algorithm)` | Создает объект для проверки цифровой подписи с заданным алгоритмом. |
| `crypto.randomBytes(size)`     | Генерирует криптографически безопасные случайные байты.                |
| `crypto.pbkdf2(password, salt, iterations, keylen, digest, callback)` | Выполняет PBKDF2 для генерации ключа.                          |
| `crypto.pbkdf2Sync(password, salt, iterations, keylen, digest)` | Выполняет PBKDF2 синхронно для генерации ключа.                 |
| `crypto.getHashes()`           | Возвращает массив доступных алгоритмов хеширования.                   |
| `crypto.createCipheriv(algorithm, key, iv)` | Создает объект шифрования с заданным алгоритмом, ключом и вектором инициализации. |
| `crypto.createDecipheriv(algorithm, key, iv)` | Создает объект расшифровки с заданным алгоритмом, ключом и вектором инициализации. |

## Примеры использования

```javascript
const crypto = require('crypto');

// Хеширование
const hash = crypto.createHash('sha256');
hash.update('Hello World');
console.log(hash.digest('hex')); // Хеш строки
```
```
