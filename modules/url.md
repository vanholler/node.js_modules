# Модуль url

Модуль для работы с URL, включая парсинг, форматирование и манипуляцию с URL-адресами. Он предоставляет функции для разбора URL и их создания, что упрощает работу с веб-адресами в приложениях.

## Методы модуля url

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `url.parse(urlString[, parseQueryString][, slashesDenoteHost])` | Разбирает строку URL и возвращает объект с его компонентами.         |
| `url.format(urlObject)`        | Форматирует объект URL в строку.                                       |
| `url.resolve(from, to)`       | Разрешает относительный URL на основе базового URL.                     |
| `url.URL`                     | Класс, представляющий URL, который позволяет работать с его компонентами. |
| `url.URLSearchParams`         | Класс, представляющий параметры строки запроса URL и предоставляющий методы для работы с ними. |
| `url.format(urlObject)`        | Форматирует объект URL в строку.                                       |
| `url.parse(urlString[, parseQueryString])` | Разбирает строку URL и возвращает объект с его компонентами, включая параметры запроса. |

## Примеры использования

```javascript
const url = require('url');

// Парсинг URL
const parsedUrl = url.parse('https://example.com:8000/path?query=string#hash');
console.log(parsedUrl);
/*
{
  protocol: 'https:',
  slashes: true,
  auth: null,
  host: 'example.com:8000',
  port: '8000',
  hostname: 'example.com',
  hash: '#hash',
  search: '?query=string',
  query: 'query=string',
  pathname: '/path',
  path: '/path?query=string',
  href: 'https://example.com:8000/path?query=string#hash'
}
*/

// Форматирование URL
const formattedUrl = url.format(parsedUrl);
console.log(formattedUrl); // 'https://example.com:8000/path?query=string#hash'
```

```
