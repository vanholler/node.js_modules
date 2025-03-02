# Модуль cluster

Модуль `cluster` в Node.js позволяет создавать кластерные приложения, которые могут использовать несколько ядер процессора. Он позволяет запускать несколько экземпляров одного и того же приложения, что улучшает производительность и масштабируемость.

## Методы и свойства модуля `cluster`

| Метод/Свойство                | Описание                                                                 |
|-------------------------------|--------------------------------------------------------------------------|
| `cluster.isMaster`            | Указывает, является ли текущий процесс мастером.                        |
| `cluster.isWorker`            | Указывает, является ли текущий процесс рабочим.                         |
| `cluster.fork()`              | Создает новый рабочий процесс.                                         |
| `cluster.workers`             | Объект, содержащий все рабочие процессы.                               |
| `cluster.on(event, listener)` | Добавляет обработчик для указанных событий (например, 'exit', 'online'). |
| `cluster.disconnect([callback])` | Отключает все рабочие процессы.                                      |

## Примеры использования

### Создание кластера

```javascript
import cluster from 'node:cluster';
import http from 'node:http';
import os from 'node:os';

if (cluster.isMaster) {
    const numCPUs = os.cpus().length;

    // Создание рабочих процессов для каждого ядра
    for (let i = 0; i < numCPUs; i++) {
        cluster.fork();
    }

    cluster.on('exit', (worker, code, signal) => {
        console.log(`Рабочий процесс ${worker.process.pid} завершился`);
    });
} else {
    // Код рабочего процесса
    http.createServer((req, res) => {
        res.writeHead(200);
        res.end('Привет от рабочего процесса!\n');
    }).listen(8000);
}
```

### Обработка событий

```javascript
cluster.on('online', (worker) => {
    console.log(`Рабочий процесс ${worker.process.pid} запущен`);
});

cluster.on('exit', (worker, code, signal) => {
    console.log(`Рабочий процесс ${worker.process.pid} завершился с кодом ${code}`);
});
```

### Отключение кластера

```javascript
cluster.disconnect(() => {
    console.log('Все рабочие процессы отключены');
});
```

```
