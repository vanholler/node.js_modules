# Модуль http2

Модуль `http2` в Node.js предоставляет API для работы с протоколом HTTP/2. Он позволяет создавать серверы и клиенты, использующие HTTP/2, что обеспечивает более эффективную передачу данных по сравнению с HTTP/1.1.

## Методы модуля `http2`

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `http2.createServer([options], requestListener)` | Создает новый HTTP/2 сервер.                                      |
| `http2.connect(url[, options])` | Создает новое HTTP/2 соединение к указанному URL.                    |
| `http2.createSecureServer([options], requestListener)` | Создает новый защищенный HTTP/2 сервер.                       |
| `http2.get(url[, options])`    | Выполняет HTTP/2 GET запрос к указанному URL.                        |
| `http2.request(url[, options])` | Выполняет HTTP/2 запрос к указанному URL.                           |

## Примеры использования

### Создание HTTP/2 сервера

```javascript
const http2 = require('node:http2');
const fs = require('fs');

const server = http2.createSecureServer({
    key: fs.readFileSync('server-key.pem'),
    cert: fs.readFileSync('server-cert.pem')
}, (req, res) => {
    res.writeHead(200, { 'Content-Type': 'text/plain' });
    res.end('Hello, HTTP/2!');
});

server.listen(3000, () => {
    console.log('HTTP/2 сервер запущен на порту 3000');
});
```

### Создание HTTP/2 клиента

```javascript
const http2 = require('node:http2');

const client = http2.connect('https://localhost:3000');

const req = client.request({ ':path': '/' });

req.on('response', (headers, flags) => {
    console.log('Response headers:', headers);
});

req.setEncoding('utf8');
req.on('data', (chunk) => {
    console.log('Response body:', chunk);
});

req.on('end', () => {
    client.close();
});
```

### Выполнение HTTP/2 GET запроса

```javascript
const http2 = require('node:http2');

http2.get('https://localhost:3000', (res) => {
    console.log('Response status code:', res.statusCode);
    res.on('data', (chunk) => {
        console.log('Response body:', chunk.toString());
    });
});
```

```
