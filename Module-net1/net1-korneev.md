# Домашнее задание к занятию "3.6. Компьютерные сети, лекция 1"
1. Работа c HTTP через телнет.
- Подключитесь утилитой телнет к сайту stackoverflow.com
`telnet stackoverflow.com 80`
- отправьте HTTP запрос
```bash
GET /questions HTTP/1.0
HOST: stackoverflow.com
[press enter]
[press enter]
```
- В ответе укажите полученный HTTP код, что он означает?

Ответ:

код ниже:

HTTP/1.1 301 Moved Permanently

cache-control: no-cache, no-store, must-revalidate

location: https://stackoverflow.com/questions

x-request-guid: 172bbc21-20b4-4d1f-9705-1b6b099c4fd0

feature-policy: microphone 'none'; speaker 'none'

content-security-policy: upgrade-insecure-requests; frame-ancestors 'self' https://stackexchange.com

Accept-Ranges: bytes

Date: Tue, 22 Feb 2022 13:48:10 GMT

Via: 1.1 varnish

Connection: close

X-Served-By: cache-hhn4046-HHN

X-Cache: MISS

X-Cache-Hits: 0

X-Timer: S1645537691.779136,VS0,VE85

Vary: Fastly-SSL

X-DNS-Prefetch-Control: off

Set-Cookie: prov=8800b06a-4d8b-e362-758d-02b20abbd4b4; domain=.stackoverflow.com; expires=Fri, 01-Jan-2055 00:00:00 GMT; path=/; HttpOnly


Connection to host lost.

Метод GET запрашивает, чтобы целевой ресурс передал представление своего состояния. 
Запросы GET должны только извлекать данные и не должны иметь никакого другого эффекта.
Код означает набор параметров для страницы сайта stackoverflow.com

cache-control - Инструкции кеширования для ответов
location - Заголовок ответа Location указывает URL-адрес для перенаправления страницы

x-request-guid - идентификатор запроса, указанный клиентом, в виде GUID. Идея  X-Request-Guid заключается в том, что клиент может создать случайный идентификатор и передать его серверу.

feature-policy - позволяет веб-разработчику выборочно включать, отключать и изменять поведение определённых функций и API в браузере

content-security-policy - это дополнительный уровень безопасности, позволяющий распознавать и устранять определённые типы атак, таких как Cross Site Scripting (XSS (en-US)) и атаки внедрения данных.

Accept-Ranges- маркер, который используется сервером для поддержки частичного запроса клиентов

X-Served-By -  идентичность серверов Fastly cache, обрабатывающих ответ. позволяет быстро записывать этот заголовок в ответы.

X-Cache - указывает был ли запрос в кэш HIT или нет MISS. у нас был зарос в кэш.

X-DNS-Prefetch-Control - заголовок , который информирует браузер о том, следует ли выполнять предварительную выборку DNS или нет.

2. Повторите задание 1 в браузере, используя консоль разработчика F12.
- откройте вкладку `Network`
- отправьте запрос http://stackoverflow.com
- найдите первый ответ HTTP сервера, откройте вкладку `Headers`
- укажите в ответе полученный HTTP код.
- проверьте время загрузки страницы, какой запрос обрабатывался дольше всего?
- приложите скриншот консоли браузера в ответ.

Ответ:

1) код 200.

Request URL: https://stackoverflow.com/
Request Method: GET
Status Code: 200 
Remote Address: 151.101.65.69:443
Referrer Policy: strict-origin-when-cross-origin

2) запрос name: https://stackoverflow.com/ ,  time = 396 ms,  type=document, 
скриншот по адресу 
https://github.com/rmx7799/devops-netology/blob/main/Module-net1/browser.png

3. Какой IP адрес у вас в интернете?

Ответ:

vagrant@host-01:~$ dig +short myip.opendns.com @resolver1.opendns.com

95.25.69.116


4. Какому провайдеру принадлежит ваш IP адрес? Какой автономной системе AS? Воспользуйтесь утилитой `whois`


vagrant@host-01:~$ whois 95.25.69.116

% This is the RIPE Database query service.

% The objects are in RPSL format.

%

% The RIPE Database is subject to Terms and Conditions.

% See http://www.ripe.net/db/support/db-terms-conditions.pdf


% Note: this output has been filtered.

%       To receive output for a database update, use the "-B" flag.


% Information related to '95.24.0.0 - 95.30.255.255'


% Abuse contact for '95.24.0.0 - 95.30.255.255' is 'abuse-b2b@beeline.ru'

inetnum:        95.24.0.0 - 95.30.255.255

netname:        BEELINE-BROADBAND

descr:          Dynamic IP Pool for broadband customers

country:        RU

admin-c:        CORB1-RIPE

tech-c:         CORB1-RIPE

status:         ASSIGNED PA

mnt-by:         RU-CORBINA-MNT

created:        2010-05-12T10:14:50Z

last-modified:  2011-10-24T07:14:07Z

source:         RIPE



vagrant@host-01:~$ whois -h whois.radb.net 95.25.69.116

route:          95.25.69.0/24

descr:          RU-CORBINA-BROADBAND-POOL1

origin:         AS8402

mnt-by:         RU-CORBINA-MNT

notify:         noc@corbina.net

created:        2011-04-28T08:53:20Z

last-modified:  2011-04-28T08:53:20Z

source:         RIPE

remarks:        ****************************

remarks:        * THIS OBJECT IS MODIFIED

remarks:        * Please note that all data that is generally regarded as personal

remarks:        * data has been removed from this object.

remarks:        * To view the original object, please query the RIPE Database at:

remarks:        * http://www.ripe.net/whois

remarks:        ****************************


Ответ: 

Провайдер: BEELINE

AS: AS8402

5. Через какие сети проходит пакет, отправленный с вашего компьютера на адрес 8.8.8.8? Через какие AS? Воспользуйтесь утилитой `traceroute`

Ответ: 

C:\Users\User>tracert -d 8.8.8.8

Tracing route to 8.8.8.8 over a maximum of 30 hops

  1     1 ms     1 ms     1 ms  192.168.1.1

  2     3 ms     2 ms     3 ms  78.107.1.249

  3     *        *        *     Request timed out.

  4     4 ms     4 ms     3 ms  213.234.224.156

  5     4 ms     4 ms     4 ms  72.14.198.182

  6     7 ms     4 ms     4 ms  108.170.250.33

  7     6 ms     4 ms     4 ms  108.170.250.51

  8    17 ms    21 ms     *     142.251.49.158

  9    16 ms    17 ms    17 ms  216.239.57.222

 10    20 ms    24 ms    19 ms  216.239.58.65

 11     *        *        *     Request timed out.

 12     *        *        *     Request timed out.

 13     *        *        *     Request timed out.

 14     *        *        *     Request timed out.

 15     *        *        *     Request timed out.

 16     *        *        *     Request timed out.

 17     *        *        *     Request timed out.

 18     *        *        *     Request timed out.

 19     *        *        *     Request timed out.

 20    17 ms     *       16 ms  8.8.8.8



Trace complete.

root@host-01:~# traceroute -i eth1  -An google.com

traceroute to google.com (108.177.14.100), 30 hops

 max, 60 byte packets

 1  * * *

 2  * * *

 3  * * *

 4  * * *

 5  * * *

 6  * * *

 7  * * *


 8  * * *

 9  * * *

10  * * *

11  * * *

12  * * *

13  * * *

14  * * *

15  * * *

16  * * *

17  * * *

18  * * *

19  * * *

20  * * *

21  * * *

22  * * *

23  * * *

24  * * *

25  * * *

26  * * *

27  * * *

28  * * *

29  * * *

30  * * *

root@host-01:~#

Ответ: traceroute не выдает список AS . вместо них ****

Вывод tracert -d из Windows  вышн, там только IP.

скриншот

https://github.com/rmx7799/devops-netology/blob/main/Module-net1/traceroute.png

6. Повторите задание 5 в утилите `mtr`. На каком участке наибольшая задержка - delay?

host-01 (10.0.2.15)                                                                            2022-02-23T10:01:57+0000
Keys:  Help   Display mode   Restart statistics   Order of fields   quit
                                                                               Packets               Pings
 Host                                                                        Loss%   Snt   Last   Avg  Best  Wrst StDev
 1. AS???    10.0.2.2                                                         0.0%    32    0.4   1.0   0.2  14.9   2.5
 2. AS???    192.168.1.1                                                      0.0%    32   19.0  15.8   1.7 259.2  46.9
 3. AS8402   78.107.1.249                                                     0.0%    32    5.7  11.0   3.5 174.9  30.1
 4. (waiting for reply)
 5. AS8402   213.234.224.156                                                  6.2%    32    5.3  10.0   4.3  61.8  11.5
 6. AS15169  72.14.198.182                                                    0.0%    32    9.3   8.3   4.7  66.9  10.9
 7. AS15169  108.170.250.33                                                   0.0%    32    7.3  11.8   6.1  62.4  13.6
 8. AS15169  108.170.250.51                                                   9.7%    32    6.2  19.1   5.2 222.5  42.0
 9. AS15169  216.239.51.32                                                   54.8%    32   21.6  40.6  21.3 174.5  40.1
10. AS15169  172.253.66.110                                                   0.0%    32   22.5  27.6  19.7  86.7  17.1
11. AS15169  216.239.58.65                                                    0.0%    31   43.4  26.6  24.0  43.4   4.4
12. (waiting for reply)
13. (waiting for reply)
14. (waiting for reply)
15. (waiting for reply)
16. (waiting for reply)
17. (waiting for reply)
18. AS15169  8.8.8.8                                                         66.7%    31   19.9  23.0  19.8  37.8   5.3

Ответ: 

максимальная задержка = 259.2 на втором участке :
   2. AS???    192.168.1.1                                                      0.0%    32   19.0  15.8   1.7 259.2  46.9

7. Какие DNS сервера отвечают за доменное имя dns.google? Какие A записи? воспользуйтесь утилитой `dig`

root@host-01:~# dig dns.google.com

; <<>> DiG 9.16.1-Ubuntu <<>> dns.google.com

;; global options: +cmd

;; Got answer:

;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 37685

;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:

; EDNS: version: 0, flags:; udp: 65494

;; QUESTION SECTION:

;dns.google.com.                        IN      A



;; ANSWER SECTION:

dns.google.com.         3144    IN      A       8.8.8.8

dns.google.com.         3144    IN      A       8.8.4.4



;; Query time: 20 msec

;; SERVER: 127.0.0.53#53(127.0.0.53)

;; WHEN: Wed Feb 23 16:23:07 UTC 2022

;; MSG SIZE  rcvd: 75



Ответ: 


DNS - серверы: 8.8.8.8, 8.8.4.4. 


A записи = 8.8.8.8, 8.8.4.4.

8. Проверьте PTR записи для IP адресов из задания 7. Какое доменное имя привязано к IP? воспользуйтесь утилитой `dig`
В качестве ответов на вопросы можно приложите лог выполнения команд в консоли или скриншот полученных результатов.


root@host-01:~# dig -x 8.8.8.8


; <<>> DiG 9.16.1-Ubuntu <<>> -x 8.8.8.8


;; global options: +cmd

;; Got answer:

;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 28992

;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1




;; OPT PSEUDOSECTION:

; EDNS: version: 0, flags:; udp: 65494

;; QUESTION SECTION:

;8.8.8.8.in-addr.arpa.          IN      PTR



;; ANSWER SECTION:

8.8.8.8.in-addr.arpa.   59340   IN      PTR     dns.google.



;; Query time: 4 msec

;; SERVER: 127.0.0.53#53(127.0.0.53)

;; WHEN: Wed Feb 23 16:27:14 UTC 2022

;; MSG SIZE  rcvd: 73



root@host-01:~# dig -x 8.8.4.4



; <<>> DiG 9.16.1-Ubuntu <<>> -x 8.8.4.4

;; global options: +cmd

;; Got answer:

;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 7633

;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1



;; OPT PSEUDOSECTION:

; EDNS: version: 0, flags:; udp: 65494

;; QUESTION SECTION:

;4.4.8.8.in-addr.arpa.          IN      PTR



;; ANSWER SECTION:

4.4.8.8.in-addr.arpa.   79143   IN      PTR     dns.google.



;; Query time: 4 msec

;; SERVER: 127.0.0.53#53(127.0.0.53)

;; WHEN: Wed Feb 23 16:27:28 UTC 2022

;; MSG SIZE  rcvd: 73


root@host-01:~#


Ответ: 

4.4.8.8.in-addr.arpa.

8.8.8.8.in-addr.arpa.

