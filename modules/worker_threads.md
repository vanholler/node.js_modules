# Модуль worker_threads

Модуль `worker_threads` позволяет создавать многопоточные приложения в Node.js. Он предоставляет возможность выполнять JavaScript-код в отдельных потоках, что позволяет использовать многоядерные процессоры более эффективно.

## Методы модуля worker_threads

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `Worker`                       | Класс, представляющий рабочий поток.                                     |
| `isMainThread`                | Логическое значение, указывающее, является ли текущий поток основным.   |
| `parentPort`                  | Объект `MessagePort`, представляющий связь с родительским потоком.      |
| `workerData`                  | Данные, переданные в рабочий поток при его создании.                    |
| `MessagePort`                  | Класс, представляющий порт для обмена сообщениями между потоками.       |
| `MessageChannel`               | Класс, представляющий канал для обмена сообщениями между потоками.      |
| `worker_threads.parentPort`    | Порт для отправки и получения сообщений от родительского потока.       |
| `worker_threads.isMainThread`  | Проверяет, является ли текущий поток основным.                          |
| `worker_threads.threadId`      | Уникальный идентификатор текущего потока.                               |
| `worker_threads.workerData`    | Данные, переданные в рабочий поток.                                     |

## Примеры использования

### Создание рабочего потока

```javascript
const { Worker, isMainThread, parentPort, workerData } = require('worker_threads');

if (isMainThread) {
    // Код основного потока
    const worker = new Worker(__filename, {
        workerData: { message: 'Hello from main thread!' }
    });

    worker.on('message', (msg) => {
        console.log('Received from worker:', msg);
    });
} else {
    // Код рабочего потока
    parentPort.postMessage(workerData.message);
}
```

### Использование `MessageChannel`

```javascript
const { Worker, MessageChannel } = require('worker_threads');

const { port1, port2 } = new MessageChannel();

const worker = new Worker('./worker.js', { workerData: { port: port2 } });

port1.on('message', (msg) => {
    console.log('Received from worker:', msg);
});

// В worker.js
const { parentPort, workerData } = require('worker_threads');

workerData.port.on('message', (msg) => {
    console.log('Message from main thread:', msg);
    workerData.port.postMessage('Hello from worker!');
});
```

```
