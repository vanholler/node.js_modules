# Модуль SQLite

Модуль `sqlite3` в Node.js предоставляет интерфейс для работы с базами данных SQLite. Он позволяет выполнять SQL-запросы, управлять транзакциями и обрабатывать результаты запросов.

## Методы модуля `sqlite3`

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `new sqlite3.Database(filename[, options])` | Создает или открывает базу данных SQLite.                          |
| `db.serialize(callback)`       | Выполняет все запросы в последовательном порядке.                      |
| `db.run(sql, params[, callback])` | Выполняет SQL-запрос без возврата результата.                       |
| `db.get(sql, params[, callback])` | Выполняет SQL-запрос и возвращает одну строку результата.           |
| `db.all(sql, params[, callback])` | Выполняет SQL-запрос и возвращает все строки результата.            |
| `db.each(sql, params, callback[, complete])` | Выполняет SQL-запрос и вызывает коллбэк для каждой строки результата. |
| `db.exec(sql, callback)`       | Выполняет несколько SQL-запросов.                                     |
| `db.close(callback)`           | Закрывает базу данных.                                                |
| `db.transaction(callback)`     | Создает транзакцию для выполнения нескольких запросов.                |

## Примеры использования

### Создание и использование базы данных

```javascript
const sqlite3 = require('sqlite3').verbose();

// Создание или открытие базы данных
const db = new sqlite3.Database(':memory:');

// Создание таблицы
db.serialize(() => {
    db.run("CREATE TABLE user (id INT, name TEXT)");

    // Вставка данных
    const stmt = db.prepare("INSERT INTO user VALUES (?, ?)");
    stmt.run(1, "Alice");
    stmt.run(2, "Bob");
    stmt.finalize();

    // Получение данных
    db.each("SELECT id, name FROM user", (err, row) => {
        console.log(row.id + ": " + row.name);
    });
});

// Закрытие базы данных
db.close();
```

### Использование транзакций

```javascript
const sqlite3 = require('sqlite3').verbose();
const db = new sqlite3.Database(':memory:');

db.serialize(() => {
    db.run("CREATE TABLE user (id INT, name TEXT)");

    db.run("BEGIN TRANSACTION");
    const stmt = db.prepare("INSERT INTO user VALUES (?, ?)");
    stmt.run(1, "Alice");
    stmt.run(2, "Bob");
    stmt.finalize();
    db.run("COMMIT");
});

db.close();
```

```
