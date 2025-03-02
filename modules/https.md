# Модуль https

Модуль для работы с HTTPS-соединениями. Он предоставляет функции для создания безопасных HTTP-серверов и клиентов, используя SSL/TLS для шифрования данных.

## Методы модуля https

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `https.createServer(options[, requestListener])` | Создает HTTPS-сервер, который принимает запросы и отправляет ответы. |
| `https.request(options[, callback])` | Выполняет HTTPS-запрос и возвращает объект `ClientRequest`.            |
| `https.get(options[, callback])` | Выполняет HTTPS GET-запрос и возвращает объект `ClientRequest`.         |
| `https.Agent`                  | Класс, представляющий HTTPS-агент, который управляет пулом соединений.  |
| `https.globalAgent`            | Глобальный HTTPS-агент, используемый по умолчанию для всех HTTPS-запросов. |
| `https.STATUS_CODES`           | Объект, содержащий коды состояния HTTPS и их описания.                  |
| `https.createAgent([options])` | Создает новый HTTPS-агент с заданными параметрами.                      |

## Примеры использования

```javascript
const https = require('https');

https.get('https://api.github.com', (resp) => {
    let data = '';

    resp.on('data', (chunk) => {
        data += chunk;
    });

    resp.on('end', () => {
        console.log(JSON.parse(data));
    });

}).on('error', (err) => {
    console.log('Ошибка: ' + err.message);
});
```

```
