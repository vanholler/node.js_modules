# Модуль zlib

Модуль для сжатия и распаковки данных. Он предоставляет функции для работы с алгоритмами сжатия, такими как Gzip и Deflate, что позволяет уменьшать размер данных для хранения или передачи.

## Методы модуля zlib

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `zlib.deflate(input[, options], callback)` | Сжимает данные с использованием алгоритма Deflate.                  |
| `zlib.deflateSync(input[, options])` | Сжимает данные синхронно с использованием алгоритма Deflate.        |
| `zlib.gzip(input[, options], callback)` | Сжимает данные с использованием алгоритма Gzip.                     |
| `zlib.gzipSync(input[, options])` | Сжимает данные синхронно с использованием алгоритма Gzip.           |
| `zlib.unzip(input[, options], callback)` | Распаковывает данные, сжатые с использованием алгоритма Gzip.      |
| `zlib.unzipSync(input[, options])` | Распаковывает данные синхронно, сжатые с использованием алгоритма Gzip. |
| `zlib.inflate(input[, options], callback)` | Распаковывает данные, сжатые с использованием алгоритма Deflate.   |
| `zlib.inflateSync(input[, options])` | Распаковывает данные синхронно, сжатые с использованием алгоритма Deflate. |
| `zlib.createGzip([options])`   | Создает поток для сжатия данных с использованием алгоритма Gzip.      |
| `zlib.createGunzip([options])`  | Создает поток для распаковки данных, сжатых с использованием алгоритма Gzip. |
| `zlib.createDeflate([options])` | Создает поток для сжатия данных с использованием алгоритма Deflate.   |
| `zlib.createInflate([options])` | Создает поток для распаковки данных, сжатых с использованием алгоритма Deflate. |

## Примеры использования

```javascript
const zlib = require('zlib');

// Сжатие данных
const input = 'Hello World!';
zlib.gzip(input, (err, buffer) => {
    if (!err) {
        console.log('Сжатые данные:', buffer.toString('base64'));
    }
});

// Распаковка данных
const compressedData = Buffer.from('H4sIAAAAAAAA/8tIzcnJVyjPL8pJAQAAAP//AwC0gU0AAAA=', 'base64');
zlib.unzip(compressedData, (err, buffer) => {
    if (!err) {
        console.log('Распакованные данные:', buffer.toString());
    }
});
```

```
