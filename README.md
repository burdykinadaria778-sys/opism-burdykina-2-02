# opism-burdykina-2-02
# Практична робота № 1
## Дисципліна: Основи побудови інформаційних систем та мереж
### Тема: Спостереження за процесом звернення до вебресурсу. Побудова власної моделі рівнів взаємодії
| | |
|---|---|
| **Прізвище, ім'я** | Бурдикіна Дар'я |
| **Група** |F5 2.02 |
| **Номер варіанта** | 3 |
| **Домен варіанта** |  example.net |
| **Середовище виконання** | *Windows* |
| **Версія curl** | *curl 8.21.0* |
| **Дата виконання** | 21.09.2026 |
## Частина A. Збір експериментальних даних
### A.1. Запит із діагностичним виводом
Команда:
curl -v https://example.net
Вивід:
C:\Users\Дар'я>curl -v https://example.net
* Host example.net:443 was resolved.
* IPv6: (none)
* IPv4: 172.66.175.59, 104.20.21.8
*   Trying 172.66.175.59:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* ALPN: server accepted http/1.1
* Established connection to example.net (172.66.175.59 port 443) from 192.168.3.173 port 57044
* using HTTP/1.x
> GET / HTTP/1.1
> Host: example.net
> User-Agent: curl/8.21.0
> Accept: */*
>
* Request completely sent off
* schannel: remote party requests renegotiation
* schannel: renegotiating SSL/TLS connection
* schannel: SSL/TLS connection renegotiated
< HTTP/1.1 200 OK
< Date: Mon, 21 Sep 2026 06:39:10 GMT
< Content-Type: text/html
< Transfer-Encoding: chunked
< Connection: keep-alive
< Server: cloudflare
< last-modified: Tue, 15 Sep 2026 23:38:37 GMT
< allow: GET, HEAD
< Accept-Ranges: bytes
< Age: 7546
< Cache-Control: max-age=14400
< cf-cache-status: HIT
< CF-RAY: a3e71238bd925bad-VIE
<
<!doctype html><html lang="en"><head><title>Example Domain</title><link rel="icon" href="data:,"><meta name="viewport" content="width=device-width, initial-scale=1"><style>body{background:#eee;width:60vw;margin:15vh auto;font-family:system-ui,sans-serif}h1{font-size:1.5em}div{opacity:0.8}a:link,a:visited{color:#348}</style></head><body><div><h1>Example Domain</h1><p>This domain is for use in documentation examples without needing permission. Avoid use in operations.</p><p><a href="https://iana.org/domains/example">Learn more</a></p></div></body></html>
* Connection #0 to host example.net:443 left intact
