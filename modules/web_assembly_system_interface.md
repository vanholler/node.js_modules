# WebAssembly System Interface (WASI)

Модуль `WASI` в Node.js предоставляет интерфейс для выполнения WebAssembly (Wasm) модулей с доступом к системным функциям, таким как файловая система и сетевые операции.

## Методы модуля `WASI`

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `WASI`                         | Конструктор для создания нового экземпляра WASI.                       |
| `WASI.start(instance)`         | Запускает WASI экземпляр с указанным экземпляром WebAssembly.           |
| `WASI.getMemory()`             | Возвращает объект `WebAssembly.Memory`, используемый WASI.              |
| `WASI.getImports(module)`      | Возвращает список импортов для указанного модуля WebAssembly.           |
| `WASI.getInstance()`           | Возвращает экземпляр WebAssembly, связанный с текущим WASI.             |
| `WASI.getExitCode()`           | Возвращает код выхода последнего завершенного процесса.                 |

## Примеры использования

### Создание и запуск WASI

```javascript
const { WASI } = require('node:wasi');
const { readFileSync } = require('fs');
const { WebAssembly } = require('node:vm');

const wasi = new WASI({
    args: process.argv,
    env: process.env,
    preopens: {
        '/sandbox': './sandbox', // Пример монтирования директории
    },
});

const wasmBuffer = readFileSync('./your_module.wasm');
const module = await WebAssembly.compile(wasmBuffer);
const instance = await WebAssembly.instantiate(module, wasi.getImports(module));

wasi.start(instance);
```

### Получение кода выхода

```javascript
const exitCode = wasi.getExitCode();
console.log(`Код выхода: ${exitCode}`);
```

```
