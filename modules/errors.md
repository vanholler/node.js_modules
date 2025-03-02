# Модуль errors

Модуль `errors` в Node.js предоставляет классы и функции для работы с ошибками. Он позволяет создавать и обрабатывать пользовательские ошибки, а также предоставляет стандартные ошибки, используемые в Node.js.

## Методы и классы модуля `errors`

| Класс/Метод                    | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `Error`                        | Базовый класс для всех ошибок.                                          |
| `Error.captureStackTrace(targetObject, constructorOpt)` | Создает стек вызовов для указанного объекта.                     |
| `Error.stack`                  | Свойство, содержащее стек вызовов ошибки.                             |
| `TypeError`                    | Ошибка, возникающая при неправильном типе данных.                      |
| `RangeError`                   | Ошибка, возникающая при выходе значения за пределы допустимого диапазона. |
| `ReferenceError`               | Ошибка, возникающая при обращении к несуществующей переменной.         |
| `SyntaxError`                  | Ошибка, возникающая при синтаксической ошибке в коде.                 |
| `URIError`                     | Ошибка, возникающая при неправильном использовании глобальных функций `encodeURI` или `decodeURI`. |

## Примеры использования

### Создание пользовательской ошибки

```javascript
class CustomError extends Error {
    constructor(message) {
        super(message);
        this.name = 'CustomError';
    }
}

try {
    throw new CustomError('Это пользовательская ошибка');
} catch (err) {
    console.error(`${err.name}: ${err.message}`);
}
```

### Обработка стандартных ошибок

```javascript
try {
    // Пример, который вызывает ошибку
    const result = someUndefinedFunction();
} catch (err) {
    if (err instanceof ReferenceError) {
        console.error('Ссылка на несуществующую переменную:', err.message);
    } else {
        console.error('Произошла ошибка:', err.message);
    }
}
```

### Использование captureStackTrace

```javascript
function MyError(message) {
    Error.captureStackTrace(this, MyError);
    this.message = message;
    this.name = 'MyError';
}

MyError.prototype = Object.create(Error.prototype);

try {
    throw new MyError('Ошибка с трассировкой стека');
} catch (err) {
    console.error(err.stack);
}
```

```
