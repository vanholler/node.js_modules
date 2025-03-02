# Модуль querystring

Модуль `querystring` в Node.js предоставляет утилиты для работы с строками запроса. Он позволяет парсить строки запроса в объекты и преобразовывать объекты в строки запроса, что удобно для работы с URL и HTTP-запросами.

## Методы модуля `querystring`

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `querystring.parse(str)`      | Преобразует строку запроса в объект.                                    |
| `querystring.stringify(obj)`   | Преобразует объект в строку запроса.                                   |
| `querystring.escape(str)`     | Кодирует строку, заменяя специальные символы на их эквиваленты в URL.  |
| `querystring.unescape(str)`   | Декодирует строку, заменяя эквиваленты URL на их оригинальные символы. |

## Примеры использования

### Парсинг строки запроса

```javascript
const querystring = require('node:querystring');

const parsed = querystring.parse('name=John&age=30');
console.log(parsed); // Вывод: { name: 'John', age: '30' }
```

### Преобразование объекта в строку запроса

```javascript
const obj = { name: 'John', age: 30 };
const str = querystring.stringify(obj);
console.log(str); // Вывод: 'name=John&age=30'
```

### Кодирование строки

```javascript
const encoded = querystring.escape('Hello World!');
console.log(encoded); // Вывод: 'Hello%20World%21'
```

### Декодирование строки

```javascript
const decoded = querystring.unescape('Hello%20World%21');
console.log(decoded); // Вывод: 'Hello World!'
```

```
