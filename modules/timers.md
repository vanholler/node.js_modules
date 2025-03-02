# Модуль timers

Модуль `timers` в Node.js предоставляет функции для работы с таймерами, позволяя выполнять код через заданные интервалы времени или после определенной задержки. Это полезно для создания асинхронных операций и управления временем выполнения.

## Методы модуля `timers`

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `setTimeout(callback, delay[, ...args])` | Запускает функцию `callback` после задержки `delay` в миллисекундах. |
| `clearTimeout(timeoutId)`      | Останавливает таймер, созданный с помощью `setTimeout()`.              |
| `setInterval(callback, delay[, ...args])` | Запускает функцию `callback` через каждые `delay` миллисекунд.      |
| `clearInterval(intervalId)`    | Останавливает интервал, созданный с помощью `setInterval()`.           |
| `setImmediate(callback[, ...args])` | Запускает функцию `callback` сразу после текущей операции ввода-вывода. |
| `clearImmediate(immediateId)`   | Останавливает выполнение функции, запланированной с помощью `setImmediate()`. |

## Примеры использования

### Использование `setTimeout`

```javascript
import { setTimeout } from 'node:timers/promises';

const timeoutId = setTimeout(() => {
    console.log('Это сообщение появится через 2 секунды');
}, 2000);

// Остановка таймера (если необходимо)
clearTimeout(timeoutId);
```

### Использование `setInterval`

```javascript
import { setInterval, clearInterval } from 'node:timers/promises';

const intervalId = setInterval(() => {
    console.log('Это сообщение будет выводиться каждые 1 секунду');
}, 1000);

// Остановка интервала через 5 секунд
setTimeout(() => {
    clearInterval(intervalId);
    console.log('Интервал остановлен');
}, 5000);
```

### Использование `setImmediate`

```javascript
import { setImmediate as setImmediatePromise } from 'node:timers/promises';

setImmediatePromise(() => {
    console.log('Это сообщение появится сразу после текущей операции ввода-вывода');
});
```

```
