# Модуль querystring

Модуль для работы с строками запроса URL. Он предоставляет функции для парсинга и форматирования строк запроса, что упрощает работу с параметрами URL в веб-приложениях.

## Методы модуля querystring

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `querystring.parse(str[, sep][, eq])` | Парсит строку запроса и возвращает объект с параметрами.             |
| `querystring.stringify(obj[, sep][, eq])` | Форматирует объект в строку запроса.                               |
| `querystring.escape(str)`      | Кодирует строку, заменяя специальные символы на их эквиваленты в URL. |
| `querystring.unescape(str)`    | Декодирует закодированную строку.                                    |
| `querystring.stringify(obj[, sep][, eq])` | Форматирует объект в строку запроса с заданными разделителями.     |
| `querystring.parse(str[, sep][, eq])` | Парсит строку запроса в объект с заданными разделителями.          |

## Примеры использования

```javascript
const querystring = require('querystring');

// Парсинг строки запроса
const parsed = querystring.parse('foo=bar&abc=xyz&abc=123');
console.log(parsed); // { foo: 'bar', abc: [ 'xyz', '123' ] }

// Форматирование объекта в строку запроса
const stringified = querystring.stringify({ foo: 'bar', abc: ['xyz', '123'] });
console.log(stringified); // 'foo=bar&abc=xyz&abc=123'
```

```
