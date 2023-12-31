## Генерация записей журналов

Nginx по-умолчанию журналирует все входящие запросы. 
Эти журналы по-умолчанию хранятся в папке /var/log/nginx/.

```bash
sudo cat /var/log/nginx/access.log # посмотреть журналы. их может быть много)
sudo less /var/log/nginx/access.log # аккуратно посмотреть журналы (q для выхода)
```

```bash
curl http://127.0.0.1
```

Рассмотрим пример записи журнала:
Стандартный формат записи журнала access.log

127.0.0.1 - - [26/Aug/2023:12:08:55 +0000] "GET / HTTP/1.1" 200 612 "-" "curl/7.81.0"

1. 127.0.0.1 = адрес с которого пришел запрос
2,3. [26/Aug/2023:12:08:55 +0000] = дата и время запроса
4,5,6. "GET / HTTP/1.1" = запрос
7. 200 = статус-код
8. 612 = размер запроса в байтах
9. "curl/7.81.0" = User-Agent

сканером в данном случае выступит nuclei.

```bash
nuclei -u http://127.0.0.1 # стандартное сканирование локального адреса
```
