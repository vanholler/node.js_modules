# Модуль net

Модуль `net` в Node.js предоставляет асинхронные сетевые API для создания серверов и клиентов TCP. Он позволяет устанавливать соединения, обмениваться данными и обрабатывать сетевые события.

## Методы модуля `net`

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `net.createServer([options][, connectionListener])` | Создает новый TCP-сервер.                                      |
| `net.connect(options[, connectionListener])` | Создает новое TCP-соединение к указанному хосту и порту.       |
| `net.createConnection(options[, connectionListener])` | Альтернативное имя для `net.connect()`.                       |
| `net.Socket`                   | Конструктор для создания нового сокета.                              |
| `net.isIP(input)`             | Проверяет, является ли входная строка допустимым IP-адресом.         |
| `net.isIPv4(input)`           | Проверяет, является ли входная строка допустимым IPv4-адресом.      |
| `net.isIPv6(input)`           | Проверяет, является ли входная строка допустимым IPv6-адресом.      |

## Примеры использования

### Создание TCP-сервера

```javascript
import net from 'node:net';

const server = net.createServer((socket) => {
    console.log('Клиент подключен');

    socket.on('data', (data) => {
        console.log(`Получено: ${data}`);
        socket.write('Ответ от сервера');
    });

    socket.on('end', () => {
        console.log('Клиент отключен');
    });
});

server.listen(8080, () => {
    console.log('Сервер запущен на порту 8080');
});
```

### Создание TCP-клиента

```javascript
import net from 'node:net';

const client = net.createConnection({ port: 8080, host: 'localhost' }, () => {
    console.log('Подключено к серверу');
    client.write('Привет, сервер!');
});

client.on('data', (data) => {
    console.log(`Получено: ${data}`);
    client.end();
});

client.on('end', () => {
    console.log('Отключено от сервера');
});
```

### Проверка IP-адреса

```javascript
console.log(net.isIP('192.168.1.1')); // Вывод: 4 (IPv4)
console.log(net.isIPv4('192.168.1.1')); // Вывод: true
console.log(net.isIPv6('::1')); // Вывод: true
```

```
