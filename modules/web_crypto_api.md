# Web Crypto API

Web Crypto API предоставляет интерфейсы для выполнения криптографических операций в веб-приложениях. Он позволяет выполнять такие операции, как хеширование, шифрование, расшифровка и создание цифровых подписей, обеспечивая безопасность данных.

## Методы Web Crypto API

### 1. `SubtleCrypto`

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `generateKey(algorithm, extractable, keyUsages)` | Генерирует криптографический ключ.                                   |
| `importKey(format, keyData, algorithm, extractable, keyUsages)` | Импортирует ключ из заданного формата.                             |
| `exportKey(format, key)`       | Экспортирует ключ в заданном формате.                                  |
| `encrypt(algorithm, key, data)` | Шифрует данные с использованием заданного алгоритма и ключа.          |
| `decrypt(algorithm, key, data)` | Расшифровывает данные с использованием заданного алгоритма и ключа.   |
| `sign(algorithm, key, data)`   | Создает цифровую подпись для данных с использованием заданного алгоритма и ключа. |
| `verify(algorithm, key, signature, data)` | Проверяет цифровую подпись для данных.                             |
| `digest(algorithm, data)`       | Вычисляет хеш для данных с использованием заданного алгоритма.        |
| `deriveKey(algorithm, baseKey, derivedKeyType, extractable, keyUsages)` | Производит новый ключ из существующего ключа.                     |
| `deriveBits(algorithm, baseKey, length)` | Производит битовые данные из существующего ключа.                |

### 2. `CryptoKey`

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `CryptoKey`                   | Класс, представляющий криптографический ключ.                           |

## Примеры использования

### Генерация ключа

```javascript
const subtle = window.crypto.subtle;

async function generateKey() {
    const key = await subtle.generateKey(
        {
            name: "AES-GCM",
            length: 256,
        },
        true, // Экспортируемый
        ["encrypt", "decrypt"] // Использование ключа
    );
    console.log(key);
}

generateKey();
```

### Шифрование данных

```javascript
const subtle = window.crypto.subtle;

async function encryptData(key, data) {
    const iv = window.crypto.getRandomValues(new Uint8Array(12)); // Инициализационный вектор
    const encrypted = await subtle.encrypt(
        {
            name: "AES-GCM",
            iv: iv,
        },
        key,
        data
    );
    return encrypted;
}
```

### Хеширование данных

```javascript
const subtle = window.crypto.subtle;

async function hashData(data) {
    const hash = await subtle.digest("SHA-256", data);
    console.log(new Uint8Array(hash));
}
```

```
