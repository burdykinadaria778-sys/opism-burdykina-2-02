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
# Частина A. Збір експериментальних даних
## A.1. Запит із діагностичним виводом
### Команда:
> curl -v https://example.net
### Вивід:
```console 
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
```
## A.2. Запит без захисту з'єднання
### Команда:
> curl -v http://neverssl.com
### Вивід:
```console
C:\Users\Дар'я>curl -v http://neverssl.com
* Host neverssl.com:80 was resolved.
* IPv6: (none)
* IPv4: 34.223.124.45
*   Trying 34.223.124.45:80...
* Established connection to neverssl.com (34.223.124.45 port 80) from 192.168.3.173 port 56594
* using HTTP/1.x
> GET / HTTP/1.1
> Host: neverssl.com
> User-Agent: curl/8.21.0
> Accept: */*
>
* Request completely sent off
< HTTP/1.1 200 OK
< Date: Mon, 21 Sep 2026 08:16:34 GMT
< Server: Apache/2.4.68 ()
< Upgrade: h2,h2c
< Connection: Upgrade
< Last-Modified: Wed, 29 Jun 2022 00:23:33 GMT
< ETag: "f79-5e28b29d38e93"
< Accept-Ranges: bytes
< Content-Length: 3961
< Vary: Accept-Encoding
< Content-Type: text/html; charset=UTF-8
<
<html>
        <head>
                <title>NeverSSL - Connecting ... </title>
                <style>
                body {
                        font-family: Montserrat, helvetica, arial, sans-serif;
                        font-size: 16x;
                        color: #444444;
                        margin: 0;
                }
                h2 {
                        font-weight: 700;
                        font-size: 1.6em;
                        margin-top: 30px;
                }
                p {
                        line-height: 1.6em;
                }
                .container {
                        max-width: 650px;
                        margin: 20px auto 20px auto;
                        padding-left: 15px;
                        padding-right: 15px
                }
                .header {
                        background-color: #42C0FD;
                        color: #FFFFFF;
                        padding: 10px 0 10px 0;
                        font-size: 2.2em;
                }
                .notice {
                        background-color: red;
                        color: white;
                        padding: 10px 0 10px 0;
                        font-size: 1.25em;
                        animation: flash 4s infinite;
                }
                @keyframes flash {
                0% {
                        background-color: red;
                }
                50% {
                        background-color: #AA0000;
                }
                0% {
                        background-color: red;
                }
                }
                <!-- CSS from Mark Webster https://gist.github.com/markcwebster/9bdf30655cdd5279bad13993ac87c85d -->
                </style>

                <script>
                        var adjectives = [ 'cool' , 'calm' , 'relaxed', 'soothing', 'serene', 'slow',
                                                        'beautiful', 'wonderful', 'wonderous', 'fun', 'good',
                                                        'glowing', 'inner', 'grand', 'majestic', 'astounding',
                                                        'fine', 'splendid', 'transcendent', 'sublime', 'whole',
                                                        'unique', 'old', 'young', 'fresh', 'clear', 'shiny',
                                                        'shining', 'lush', 'quiet', 'bright', 'silver' ];

                        var nouns =       [ 'day', 'dawn', 'peace', 'smile', 'love', 'zen', 'laugh',
                                                        'yawn', 'poem', 'song', 'joke', 'verse', 'kiss', 'sunrise',
                                                        'sunset', 'eclipse', 'moon', 'rainbow', 'rain', 'plan',
                                                        'play', 'chart', 'birds', 'stars', 'pathway', 'secret',
                                                        'treasure', 'melody', 'magic', 'spell', 'light', 'morning'];

                        var prefix =
                                        // Choose 3 zen adjectives
                                        adjectives.sort(function(){return 0.5-Math.random()}).slice(-3).join('')
                                        +
                                        // Coupled with a zen noun
                                        nouns.sort(function(){return 0.5-Math.random()}).slice(-1).join('');
                        window.location.href = 'http://' + prefix + '.neverssl.com/online';
                </script>
        </head>
        <body>
        <noscript>
                <div class="notice">
                        <div class="container">
                                ⚠️ JavaScript appears to be disabled. NeverSSL's cache-busting works better if you enable JavaScript for <code>neverssl.com</code>.
                        </div>
                </div>
        </noscript>
        <div class="header">
                <div class="container">
                <h1>NeverSSL</h1>
                </div>
        </div>
        <div class="content">
        <div class="container">

        <h1 id="status"></h1>
        <script>document.querySelector("#status").textContent = "Connecting ...";</script>
        <noscript>

                <h2>What?</h2>
                <p>This website is for when you try to open Facebook, Google, Amazon, etc
                on a wifi network, and nothing happens. Type "http://neverssl.com"
                into your browser's url bar, and you'll be able to log on.</p>

                <h2>How?</h2>
                <p>neverssl.com will never use SSL (also known as TLS). No
                encryption, no strong authentication, no <a
                href="https://en.wikipedia.org/wiki/HTTP_Strict_Transport_Security">HSTS</a>,
                no HTTP/2.0, just plain old unencrypted HTTP and forever stuck in the dark
                ages of internet security.</p>

                <h2>Why?</h2>
                <p>Normally, that's a bad idea. You should always use SSL and secure
                encryption when possible. In fact, it's such a bad idea that most websites
                are now using https by default.</p>

                <p>And that's great, but it also means that if you're relying on
                poorly-behaved wifi networks, it can be hard to get online.  Secure
                browsers and websites using https make it impossible for those wifi
                networks to send you to a login or payment page. Basically, those networks
                can't tap into your connection just like attackers can't. Modern browsers
                are so good that they can remember when a website supports encryption and
                even if you type in the website name, they'll use https.</p>

                <p>And if the network never redirects you to this page, well as you can
                see, you're not missing much.</p>

        <a href="https://twitter.com/neverssl">Follow @neverssl</a>

        </noscript>

        </div>
        </div>

        </body>
</html>
* Connection #0 to host neverssl.com:80 left intact
```
## A.3. Запит до служби доменних імен
### Команда (перше виконання):
> nslookup -debug example.net
### Вивід:
```console 
C:\Users\Дар'я>nslookup -debug example.net
------------
Got answer:
    HEADER:
        opcode = QUERY, id = 1, rcode = NXDOMAIN
        header flags:  response, want recursion
        questions = 1,  answers = 0,  authority records = 0,  additional = 0

    QUESTIONS:
        1.3.168.192.in-addr.arpa, type = PTR, class = IN

------------
Server:  UnKnown
Address:  192.168.3.1

------------
Got answer:
    HEADER:
        opcode = QUERY, id = 2, rcode = NOERROR
        header flags:  response, want recursion, recursion avail.
        questions = 1,  answers = 2,  authority records = 0,  additional = 0

    QUESTIONS:
        example.net, type = A, class = IN
    ANSWERS:
    ->  example.net
        internet address = 172.66.175.59
        ttl = 300 (5 mins)
    ->  example.net
        internet address = 104.20.21.8
        ttl = 300 (5 mins)

------------
Non-authoritative answer:
------------
Got answer:
    HEADER:
        opcode = QUERY, id = 3, rcode = NOERROR
        header flags:  response, want recursion, recursion avail.
        questions = 1,  answers = 2,  authority records = 0,  additional = 0

    QUESTIONS:
        example.net, type = AAAA, class = IN
    ANSWERS:
    ->  example.net
        AAAA IPv6 address = 2606:4700:10::ac42:af3b
        ttl = 300 (5 mins)
    ->  example.net
        AAAA IPv6 address = 2606:4700:10::6814:1508
        ttl = 300 (5 mins)

------------
Name:    example.net
Addresses:  2606:4700:10::ac42:af3b
          2606:4700:10::6814:1508
          172.66.175.59
          104.20.21.8
```
### Команда (повторне виконання через 5–7 хвилин):
> nslookup -debug example.net
Вивід:
```console
C:\Users\Дар'я>nslookup -debug example.net
------------
Got answer:
    HEADER:
        opcode = QUERY, id = 1, rcode = NXDOMAIN
        header flags:  response, want recursion
        questions = 1,  answers = 0,  authority records = 0,  additional = 0

    QUESTIONS:
        1.3.168.192.in-addr.arpa, type = PTR, class = IN

------------
Server:  UnKnown
Address:  192.168.3.1

------------
Got answer:
    HEADER:
        opcode = QUERY, id = 2, rcode = NOERROR
        header flags:  response, want recursion, recursion avail.
        questions = 1,  answers = 2,  authority records = 0,  additional = 0

    QUESTIONS:
        example.net, type = A, class = IN
    ANSWERS:
    ->  example.net
        internet address = 104.20.21.8
        ttl = 300 (5 mins)
    ->  example.net
        internet address = 172.66.175.59
        ttl = 300 (5 mins)

------------
Non-authoritative answer:
------------
Got answer:
    HEADER:
        opcode = QUERY, id = 3, rcode = NOERROR
        header flags:  response, want recursion, recursion avail.
        questions = 1,  answers = 2,  authority records = 0,  additional = 0

    QUESTIONS:
        example.net, type = AAAA, class = IN
    ANSWERS:
    ->  example.net
        AAAA IPv6 address = 2606:4700:10::6814:1508
        ttl = 300 (5 mins)
    ->  example.net
        AAAA IPv6 address = 2606:4700:10::ac42:af3b
        ttl = 300 (5 mins)

------------
Name:    example.net
Addresses:  2606:4700:10::6814:1508
          2606:4700:10::ac42:af3b
          104.20.21.8
          172.66.175.59
```
