# Web Streams API

Web Streams API предоставляет интерфейсы для работы с потоками данных, позволяя обрабатывать данные по частям, а не загружать их целиком в память. Это особенно полезно для работы с большими объемами данных, такими как файлы или сетевые запросы.

## Методы Web Streams API

### 1. `ReadableStream`

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `ReadableStream()`             | Конструктор для создания нового читаемого потока.                      |
| `getReader()`                 | Возвращает объект `ReadableStreamDefaultReader`, который позволяет читать данные из потока. |
| `pipeTo(destination[, options])` | Перенаправляет данные из читаемого потока в целевой поток.            |
| `tee()`                       | Разделяет поток на два читаемых потока.                                 |

### 2. `ReadableStreamDefaultReader`

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `read()`                      | Читает данные из потока и возвращает объект с результатом.              |
| `releaseLock()`               | Освобождает блокировку на потоке, позволяя другим читателям получить доступ. |

### 3. `WritableStream`

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `WritableStream()`             | Конструктор для создания нового записываемого потока.                   |
| `getWriter()`                 | Возвращает объект `WritableStreamDefaultWriter`, который позволяет записывать данные в поток. |

### 4. `WritableStreamDefaultWriter`

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `write(chunk)`                | Записывает данные в поток.                                              |
| `close()`                     | Закрывает поток, предотвращая дальнейшую запись.                       |
| `abort(reason)`               | Прерывает поток с указанной причиной.                                   |
| `releaseLock()`               | Освобождает блокировку на потоке, позволяя другим писателям получить доступ. |

### 5. `TransformStream`

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `TransformStream()`            | Конструктор для создания нового трансформирующего потока.               |
| `getReader()`                 | Возвращает объект `ReadableStreamDefaultReader` для чтения данных.      |
| `getWriter()`                 | Возвращает объект `WritableStreamDefaultWriter` для записи данных.      |

## Примеры использования

### Читаемый поток

```javascript
const { ReadableStream } = require('stream/web');

const readableStream = new ReadableStream({
    start(controller) {
        controller.enqueue('Hello');
        controller.enqueue('World');
        controller.close();
    }
});

const reader = readableStream.getReader();

reader.read().then(({ done, value }) => {
    console.log(value); // 'Hello'
});
```

### Записываемый поток

```javascript
const { WritableStream } = require('stream/web');

const writableStream = new WritableStream({
    write(chunk) {
        console.log(chunk); // Выводит данные, которые были записаны
    }
});

const writer = writableStream.getWriter();
writer.write('Hello');
writer.write('World');
writer.close();
```

```
