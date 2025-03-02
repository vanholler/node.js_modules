# Модуль perf_hooks

Модуль `perf_hooks` в Node.js предоставляет API для измерения производительности. Он позволяет отслеживать время выполнения кода и производить более детальный анализ производительности приложений.

## Методы модуля `perf_hooks`

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `performance.now()`           | Возвращает текущее время в миллисекундах с высокой точностью.          |
| `PerformanceObserver`          | Конструктор для создания наблюдателя, который может отслеживать производительность. |
| `performance.mark(name)`      | Устанавливает метку с указанным именем для отслеживания времени.        |
| `performance.measure(name, startMark, endMark)` | Измеряет время между двумя метками.                          |
| `performance.clearMarks(name)` | Очищает метки с указанным именем.                                     |
| `performance.clearMeasures(name)` | Очищает измерения с указанным именем.                               |

## Примеры использования

### Измерение времени выполнения

```javascript
import { performance } from 'node:perf_hooks';

const start = performance.now();

// Код, время выполнения которого нужно измерить
for (let i = 0; i < 1e6; i++) {}

const end = performance.now();
console.log(`Время выполнения: ${end - start} миллисекунд`);
```

### Использование PerformanceObserver

```javascript
import { PerformanceObserver, performance } from 'node:perf_hooks';

const obs = new PerformanceObserver((list) => {
    for (const entry of list.getEntries()) {
        console.log(`${entry.name}: ${entry.duration} миллисекунд`);
    }
});

obs.observe({ entryTypes: ['measure'] });

performance.mark('start');
// Код, который нужно измерить
performance.mark('end');
performance.measure('Моя измеренная операция', 'start', 'end');
```

### Установка и очистка меток

```javascript
performance.mark('start');
// Код, который нужно измерить
performance.mark('end');

performance.measure('Моя операция', 'start', 'end');
performance.clearMarks('start');
performance.clearMarks('end');
```

```
