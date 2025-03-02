# Модуль child_process

Модуль для создания дочерних процессов. Он позволяет выполнять команды в командной строке и взаимодействовать с ними, что полезно для выполнения асинхронных операций и управления процессами.

## Методы модуля child_process

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `child_process.exec(command[, options][, callback])` | Выполняет команду в оболочке и возвращает буфер с результатом. |
| `child_process.execFile(file[, args][, options][, callback])` | Выполняет файл с аргументами и возвращает буфер с результатом. |
| `child_process.spawn(command[, args][, options])` | Запускает новый процесс с заданной командой и аргументами.       |
| `child_process.spawnSync(command[, args][, options])` | Запускает новый процесс синхронно.                               |
| `child_process.fork(modulePath[, args][, options])` | Создает новый процесс, который выполняет указанный модуль.       |
| `child_process.execSync(command[, options])` | Выполняет команду синхронно и возвращает буфер с результатом.    |
| `child_process.execFileSync(file[, args][, options])` | Выполняет файл синхронно и возвращает буфер с результатом.      |
| `child_process.spawnSync(command[, args][, options])` | Запускает новый процесс синхронно и возвращает объект с результатом. |
| `child_process.ChildProcess`   | Класс, представляющий дочерний процесс, с методами для взаимодействия с ним. |

## Примеры использования

```javascript
const { exec } = require('child_process');

exec('ls', (error, stdout, stderr) => {
    if (error) {
        console.error(`Ошибка: ${error.message}`);
        return;
    }
    if (stderr) {
        console.error(`Ошибка: ${stderr}`);
        return;
    }
    console.log(`Результат: ${stdout}`);
});
```
```
