# Модуль test_runner

Модуль `test_runner` в Node.js предоставляет интерфейс для запуска тестов и управления их выполнением. Он позволяет организовывать тесты, собирать результаты и выводить отчеты о тестировании.

## Методы модуля `test_runner`

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `testRunner.run(tests)`       | Запускает указанные тесты и возвращает результаты.                      |
| `testRunner.addTest(name, fn)` | Добавляет новый тест с указанным именем и функцией.                    |
| `testRunner.setOptions(options)` | Устанавливает параметры для выполнения тестов.                       |
| `testRunner.getResults()`      | Возвращает результаты выполненных тестов.                              |
| `testRunner.on(event, listener)` | Добавляет обработчик для указанного события (например, 'pass', 'fail'). |

## Примеры использования

### Запуск тестов

```javascript
const testRunner = require('test_runner');

// Добавление тестов
testRunner.addTest('Тест 1', () => {
    // Логика теста
    if (true) {
        console.log('Тест 1 пройден');
    } else {
        throw new Error('Тест 1 не пройден');
    }
});

testRunner.addTest('Тест 2', () => {
    // Логика теста
    if (false) {
        console.log('Тест 2 пройден');
    } else {
        throw new Error('Тест 2 не пройден');
    }
});

// Запуск тестов
testRunner.run();
```

### Получение результатов тестов

```javascript
const results = testRunner.getResults();
console.log('Результаты тестов:', results);
```

### Установка параметров

```javascript
testRunner.setOptions({
    verbose: true, // Включает подробный вывод
});
```

```
