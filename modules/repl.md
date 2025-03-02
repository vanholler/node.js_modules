d# Модуль repl

Модуль `repl` в Node.js предоставляет интерфейс для создания интерактивных сеансов чтения, оценки и вывода (Read-Eval-Print Loop). Он позволяет пользователям вводить JavaScript-код и получать результаты его выполнения в реальном времени.

## Методы модуля `repl`

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `repl.start([options])`       | Запускает новый REPL-сессии с заданными параметрами.                   |
| `repl.createContext([context])` | Создает новый контекст для REPL с заданными переменными.              |
| `repl.eval(code, context, filename, callback)` | Оценивает код в заданном контексте.                             |
| `repl.write(text, [options])` | Записывает текст в REPL.                                                |
| `repl.clearBufferedCommand()`  | Очищает буферированную команду.                                        |

## Примеры использования

### Запуск REPL-сессии

```javascript
import repl from 'node:repl';

const server = repl.start('> ');

// Добавление переменной в контекст
server.context.myVar = 42;
```

### Оценка кода

```javascript
server.eval('myVar + 1', server.context, 'repl', (err, result) => {
    if (err) {
        console.error(err);
    } else {
        console.log(result); // Вывод: 43
    }
});
```

### Запись текста в REPL

```javascript
server.write('console.log("Hello, World!");\n');
```

```
