# Модуль http

Модуль для создания HTTP-серверов и клиентов. Он предоставляет функции для работы с HTTP-запросами и ответами, что позволяет разрабатывать веб-приложения и API.

## Методы модуля http

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `http.createServer([requestListener])` | Создает HTTP-сервер, который принимает запросы и отправляет ответы. |
| `http.request(options[, callback])` | Выполняет HTTP-запрос и возвращает объект `ClientRequest`.            |
| `http.get(options[, callback])` | Выполняет HTTP GET-запрос и возвращает объект `ClientRequest`.         |
| `http.IncomingMessage`         | Класс, представляющий входящее HTTP-сообщение (запрос).                |
| `http.ServerResponse`          | Класс, представляющий ответ HTTP-сервера.                               |
| `http.STATUS_CODES`            | Объект, содержащий коды состояния HTTP и их описания.                  |
| `http.Agent`                   | Класс, представляющий HTTP-агент, который управляет пулом соединений.  |
| `http.globalAgent`             | Глобальный HTTP-агент, используемый по умолчанию для всех HTTP-запросов. |
| `http.createAgent([options])`  | Создает новый HTTP-агент с заданными параметрами.                      |

## Примеры использования

```javascript
const http = require('http');

const server = http.createServer((req, res) => {
    res.statusCode = 200;
    res.setHeader('Content-Type', 'text/plain');
    res.end('Hello World\n');
});

server.listen(3000, () => {
    console.log('Сервер запущен на порту 3000');
});
```

```
