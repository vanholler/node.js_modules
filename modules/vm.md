# Модуль vm

Модуль `vm` в Node.js предоставляет возможность компилировать и выполнять JavaScript-код в контексте виртуальной машины. Это позволяет изолировать выполнение кода и управлять его окружением.

## Методы модуля `vm`

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `vm.runInThisContext(code[, options])` | Выполняет код в текущем контексте.                                   |
| `vm.runInNewContext(code[, sandbox])` | Выполняет код в новом контексте с заданным песочницей.               |
| `vm.compileFunction(code, params[, options])` | Компилирует функцию из кода и возвращает её.                     |
| `vm.createContext(sandbox)`    | Создает новый контекст с заданной песочницей.                         |
| `vm.isContext(sandbox)`         | Проверяет, является ли объект контекстом.                             |
| `vm.runInContext(code, context)` | Выполняет код в указанном контексте.                                 |

## Примеры использования

### Выполнение кода в текущем контексте

```javascript
const vm = require('vm');

const result = vm.runInThisContext('2 + 2');
console.log(result); // 4
```

### Выполнение кода в новом контексте

```javascript
const vm = require('vm');

const sandbox = { x: 1 };
vm.createContext(sandbox); // Создание нового контекста

const result = vm.runInNewContext('x + 1', sandbox);
console.log(result); // 2
```

### Компиляция функции

```javascript
const vm = require('vm');

const code = 'return x + y;';
const params = ['x', 'y'];
const compiledFunction = vm.compileFunction(code, params);

const result = compiledFunction(2, 3);
console.log(result); // 5
```

### Создание контекста

```javascript
const vm = require('vm');

const sandbox = { a: 1, b: 2 };
vm.createContext(sandbox);

vm.runInContext('a + b', sandbox); // 3
```

```
