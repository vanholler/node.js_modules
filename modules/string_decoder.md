р# Модуль string_decoder

Модуль `string_decoder` в Node.js предоставляет инструменты для декодирования буферов в строки. Он особенно полезен при работе с потоками, где данные могут поступать в виде буферов, и необходимо преобразовать их в строки с учетом кодировки.

## Методы модуля `string_decoder`

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `StringDecoder`                | Конструктор для создания нового экземпляра декодера.                   |
| `StringDecoder.write(buffer)`  | Декодирует переданный буфер и возвращает строку.                       |
| `StringDecoder.end()`          | Завершает декодирование и возвращает оставшиеся данные в виде строки.  |
| `StringDecoder.setDefaultEncoding(encoding)` | Устанавливает кодировку по умолчанию для декодирования. |

## Примеры использования

### Декодирование буфера

```javascript
const { StringDecoder } = require('string_decoder');
const decoder = new StringDecoder('utf8');

const buffer = Buffer.from('Привет, мир!');
const str = decoder.write(buffer);
console.log(str); // Вывод: Привет, мир!
```

### Завершение декодирования

```javascript
const remaining = decoder.end();
console.log(remaining); // Выводит оставшиеся данные, если они есть
```

```
