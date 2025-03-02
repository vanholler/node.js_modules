# Модуль TLS/SSL

Модуль `tls` в Node.js предоставляет интерфейсы для работы с протоколами TLS (Transport Layer Security) и SSL (Secure Sockets Layer). Он позволяет создавать защищенные соединения для передачи данных по сети, обеспечивая шифрование и аутентификацию.

## Методы модуля `tls`

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `tls.createServer(options, secureConnectionListener)` | Создает новый TLS-сервер.                                          |
| `tls.connect(options[, secureConnectListener])` | Создает новое TLS-соединение.                                      |
| `tls.TLSSocket`               | Класс, представляющий TLS-сокет, который расширяет `net.Socket`.       |
| `tls.checkServerIdentity(host, cert)` | Проверяет идентичность сервера с использованием сертификата.      |
| `tls.getCiphers()`            | Возвращает список доступных шифров.                                   |
| `tls.DEFAULT_ECDHE_CURVE`     | Устанавливает значение по умолчанию для кривой ECDHE.                 |
| `tls.createSecureContext(options)` | Создает новый контекст безопасности для TLS.                      |

## Примеры использования

### Создание TLS-сервера

```javascript
const tls = require('tls');
const fs = require('fs');

const options = {
    key: fs.readFileSync('server-key.pem'),
    cert: fs.readFileSync('server-cert.pem')
};

const server = tls.createServer(options, (socket) => {
    console.log('Клиент подключен:', socket.remoteAddress);
    socket.write('Добро пожаловать на защищенный сервер!\n');
    socket.setEncoding('utf8');
    socket.pipe(socket);
});

server.listen(8000, () => {
    console.log('TLS-сервер запущен на порту 8000');
});
```

### Создание TLS-клиента

```javascript
const tls = require('tls');
const fs = require('fs');

const options = {
    host: 'localhost',
    port: 8000,
    ca: [fs.readFileSync('server-cert.pem')] // Сертификат сервера
};

const client = tls.connect(options, () => {
    console.log('Подключено к серверу!');
    client.write('Привет, защищенный сервер!');
});

client.on('data', (data) => {
    console.log('Получено от сервера:', data.toString());
    client.end();
});
```

### Проверка идентичности сервера

```javascript
const tls = require('tls');

const options = {
    host: 'example.com',
    port: 443,
    rejectUnauthorized: true // Отклонить неавторизованные сертификаты
};

const socket = tls.connect(options, () => {
    console.log('Подключено к серверу:', socket.authorized ? 'да' : 'нет');
    if (!socket.authorized) {
        console.log('Ошибка:', socket.authorizationError);
    }
});
```

```
