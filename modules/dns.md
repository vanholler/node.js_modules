d# Модуль dns

Модуль `dns` в Node.js предоставляет API для работы с системой доменных имен (DNS). Он позволяет выполнять запросы DNS, такие как разрешение доменных имен в IP-адреса и наоборот.

## Методы модуля `dns`

| Метод                          | Описание                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| `dns.lookup(hostname[, options], callback)` | Разрешает доменное имя в IP-адрес.                               |
| `dns.resolve(domain[, rrtype], callback)` | Выполняет запрос DNS для указанного домена и типа записи.         |
| `dns.resolve4(domain, callback)` | Разрешает доменное имя в IPv4-адреса.                               |
| `dns.resolve6(domain, callback)` | Разрешает доменное имя в IPv6-адреса.                               |
| `dns.resolveMx(domain, callback)` | Разрешает доменное имя в записи MX (Mail Exchange).                 |
| `dns.resolveTxt(domain, callback)` | Разрешает доменное имя в записи TXT.                                |
| `dns.reverse(ip, callback)`    | Выполняет обратное разрешение IP-адреса в доменное имя.              |
| `dns.getServers()`             | Возвращает массив DNS-серверов, используемых для запросов.           |
| `dns.setServers(servers)`      | Устанавливает массив DNS-серверов для использования.                  |

## Примеры использования

### Разрешение доменного имени

```javascript
import dns from 'node:dns';

dns.lookup('example.com', (err, address, family) => {
    if (err) {
        console.error(err);
    } else {
        console.log(`IP-адрес: ${address}, Семейство: ${family}`);
    }
});
```

### Запрос DNS для записи A

```javascript
dns.resolve4('example.com', (err, addresses) => {
    if (err) {
        console.error(err);
    } else {
        console.log(`IPv4-адреса: ${addresses}`);
    }
});
```

### Запрос DNS для записи MX

```javascript
dns.resolveMx('example.com', (err, addresses) => {
    if (err) {
        console.error(err);
    } else {
        addresses.forEach((record) => {
            console.log(`MX-сервер: ${record.exchange}, Приоритет: ${record.priority}`);
        });
    }
});
```

### Обратное разрешение IP-адреса

```javascript
dns.reverse('8.8.8.8', (err, hostnames) => {
    if (err) {
        console.error(err);
    } else {
        console.log(`Обратное разрешение: ${hostnames}`);
    }
});
```

```
