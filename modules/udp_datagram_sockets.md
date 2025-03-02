# Модуль UDP Datagram Sockets

Модуль `dgram` в Node.js предоставляет интерфейс для работы с UDP (User Datagram Protocol) сокетами. Он позволяет отправлять и получать датаграммы, что делает его полезным для приложений, требующих низкой задержки и высокой производительности, таких как игры и потоковая передача.

## Методы модуля `dgram`

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `dgram.createSocket(type[, options])` | Создает новый сокет с указанным типом (например, 'udp4' или 'udp6'). |
| `socket.bind(port[, address][, callback])` | Привязывает сокет к указанному порту и адресу.                     |
| `socket.send(msg, offset, length, port, address[, callback])` | Отправляет сообщение на указанный адрес и порт.                   |
| `socket.close([callback])`     | Закрывает сокет.                                                       |
| `socket.on(event, listener)`   | Добавляет обработчик события для сокета (например, 'message', 'error'). |
| `socket.address()`             | Возвращает объект с информацией о текущем адресе сокета.              |
| `socket.setBroadcast(flag)`    | Включает или отключает режим широковещательной рассылки.              |
| `socket.setMulticastTTL(ttl)`  | Устанавливает время жизни для многокастовых пакетов.                  |
| `socket.joinGroup(multicastAddress)` | Присоединяет сокет к многокастовой группе.                       |
| `socket.leaveGroup(multicastAddress)` | Покидает многокастовую группу.                                   |

## Примеры использования

### Создание UDP сокета

```javascript
const dgram = require('dgram');
const socket = dgram.createSocket('udp4');

socket.on('message', (msg, rinfo) => {
    console.log(`Получено сообщение: ${msg} от ${rinfo.address}:${rinfo.port}`);
});

socket.bind(41234, () => {
    console.log('Сокет привязан к порту 41234');
});
```

### Отправка сообщения

```javascript
const dgram = require('dgram');
const socket = dgram.createSocket('udp4');

const message = Buffer.from('Привет, UDP!');
socket.send(message, 0, message.length, 41234, 'localhost', (err) => {
    if (err) {
        console.error('Ошибка при отправке:', err);
    } else {
        console.log('Сообщение отправлено');
    }
});
```

### Закрытие сокета

```javascript
socket.close(() => {
    console.log('Сокет закрыт');
});
```

```
