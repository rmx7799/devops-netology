# Домашнее задание к занятию "3.7. Компьютерные сети, лекция 2"
1. Проверьте список доступных сетевых интерфейсов на вашем компьютере. Какие команды есть для этого в Linux и в Windows?

ответ:
ipconfig /all -windows
ifconfig - linux
ip a -linux

windows:

C:\Users\User>ipconfig /all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : DCE-HPE-AIV
   
   Primary Dns Suffix  . . . . . . . :
   
   Node Type . . . . . . . . . . . . : Hybrid
   
   IP Routing Enabled. . . . . . . . : No
   
   WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Ethernet:

   
   Media State . . . . . . . . . . . : Media disconnected
   
   Connection-specific DNS Suffix  . :
   
   Description . . . . . . . . . . . : Realtek PCIe GbE Family Controller
   
   Physical Address. . . . . . . . . : B0-0C-D1-6B-F7-CA
   
   DHCP Enabled. . . . . . . . . . . : No
   
   Autoconfiguration Enabled . . . . : Yes

Unknown adapter OpenVPN Wintun:

   
   Media State . . . . . . . . . . . : Media disconnected
   
   Connection-specific DNS Suffix  . :
   
   Description . . . . . . . . . . . : Wintun Userspace Tunnel
   
   Physical Address. . . . . . . . . :
   
   
   DHCP Enabled. . . . . . . . . . . : No
   
   Autoconfiguration Enabled . . . . : Yes


Ethernet adapter Ethernet 4:


   Connection-specific DNS Suffix  . :

   Description . . . . . . . . . . . : VirtualBox Host-Only Ethernet Adapter

   Physical Address. . . . . . . . . : 0A-00-27-00-00-10

   DHCP Enabled. . . . . . . . . . . : No

   Autoconfiguration Enabled . . . . : Yes

   Link-local IPv6 Address . . . . . : fe80::d549:4f9a:e7bc:1179%16(Preferred)

   IPv4 Address. . . . . . . . . . . : 192.168.56.1(Preferred)

   Subnet Mask . . . . . . . . . . . : 255.255.255.0

   Default Gateway . . . . . . . . . :

   DHCPv6 IAID . . . . . . . . . . . : 1107951655

   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-25-EE-D7-0E-B0-0C-D1-6B-F7-CA

   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1

                                       fec0:0:0:ffff::2%1
                                       fec0:0:0:ffff::3%1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter VirtualBox Host-Only Network #2:


   Connection-specific DNS Suffix  . :

   Description . . . . . . . . . . . : VirtualBox Host-Only Ethernet Adapter #2

   Physical Address. . . . . . . . . : 0A-00-27-00-00-19

   DHCP Enabled. . . . . . . . . . . : No

   Autoconfiguration Enabled . . . . : Yes

   Link-local IPv6 Address . . . . . : fe80::871:6b73:cc24:45ca%25(Preferred)

   IPv4 Address. . . . . . . . . . . : 10.10.10.1(Preferred)

   Subnet Mask . . . . . . . . . . . : 255.255.255.0

   Default Gateway . . . . . . . . . :

   DHCPv6 IAID . . . . . . . . . . . : 1292501031

   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-25-EE-D7-0E-B0-0C-D1-6B-F7-CA

   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1

                                       fec0:0:0:ffff::2%1
                                       fec0:0:0:ffff::3%1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter VirtualBox Host-Only Network #3:


   Connection-specific DNS Suffix  . :

   Description . . . . . . . . . . . : VirtualBox Host-Only Ethernet Adapter #3

   Physical Address. . . . . . . . . : 0A-00-27-00-00-08

   DHCP Enabled. . . . . . . . . . . : No

   Autoconfiguration Enabled . . . . : Yes

   Link-local IPv6 Address . . . . . : fe80::f07e:a8c1:ad62:308c%8(Preferred)

   IPv4 Address. . . . . . . . . . . : 192.168.10.1(Preferred)

   Subnet Mask . . . . . . . . . . . : 255.255.255.0

   Default Gateway . . . . . . . . . :

   DHCPv6 IAID . . . . . . . . . . . : 1376387111

   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-25-EE-D7-0E-B0-0C-D1-6B-F7-CA

   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                      fec0:0:0:ffff::2%1
                                       fec0:0:0:ffff::3%1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter VirtualBox Host-Only Network #4:

   Connection-specific DNS Suffix  . :

   Description . . . . . . . . . . . : VirtualBox Host-Only Ethernet Adapter #4

   Physical Address. . . . . . . . . : 0A-00-27-00-00-13

   DHCP Enabled. . . . . . . . . . . : No

   Autoconfiguration Enabled . . . . : Yes

   Link-local IPv6 Address . . . . . : fe80::1b7:b80c:a897:179c%19(Preferred)

   IPv4 Address. . . . . . . . . . . : 192.168.100.1(Preferred)

   Subnet Mask . . . . . . . . . . . : 255.255.255.0

   Default Gateway . . . . . . . . . :

   DHCPv6 IAID . . . . . . . . . . . : 1460273191

   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-25-EE-D7-0E-B0-0C-D1-6B-F7-CA

   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1

                                       fec0:0:0:ffff::2%1

                                       fec0:0:0:ffff::3%1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Unknown adapter OpenVPN TAP-Windows6:

   Media State . . . . . . . . . . . : Media disconnected

   Connection-specific DNS Suffix  . :

   Description . . . . . . . . . . . : TAP-Windows Adapter V9

   Physical Address. . . . . . . . . : 00-FF-C5-9D-81-D7

   DHCP Enabled. . . . . . . . . . . : Yes

   Autoconfiguration Enabled . . . . : Yes



Wireless LAN adapter Local Area Connection* 1:


   Media State . . . . . . . . . . . : Media disconnected

   Connection-specific DNS Suffix  . :

   Description . . . . . . . . . . . : Microsoft Wi-Fi Direct Virtual Adapter

   Physical Address. . . . . . . . . : D8-F2-CA-DC-63-F7

   DHCP Enabled. . . . . . . . . . . : Yes

   Autoconfiguration Enabled . . . . : Yes



Wireless LAN adapter Local Area Connection* 2:


   Media State . . . . . . . . . . . : Media disconnected

   Connection-specific DNS Suffix  . :

   Description . . . . . . . . . . . : Microsoft Wi-Fi Direct Virtual Adapter #2

   Physical Address. . . . . . . . . : DA-F2-CA-DC-63-F6

   DHCP Enabled. . . . . . . . . . . : No


   Autoconfiguration Enabled . . . . : Yes


Ethernet adapter Ethernet 3:



   Media State . . . . . . . . . . . : Media disconnected

   Connection-specific DNS Suffix  . :

   Description . . . . . . . . . . . : CP-TAP-Windows Adapter V9

   Physical Address. . . . . . . . . : 00-FF-D1-28-40-F2

   DHCP Enabled. . . . . . . . . . . : No

   Autoconfiguration Enabled . . . . : Yes



Wireless LAN adapter Wi-Fi:

   Connection-specific DNS Suffix  . :
   

   Description . . . . . . . . . . . : Intel(R) Wireless-AC 9560 160MHz

   Physical Address. . . . . . . . . : D8-F2-CA-DC-63-F6

   DHCP Enabled. . . . . . . . . . . : Yes

   Autoconfiguration Enabled . . . . : Yes

   Link-local IPv6 Address . . . . . : fe80::2414:5ac6:f3d1:e680%9(Preferred)

   IPv4 Address. . . . . . . . . . . : 192.168.91.76(Preferred)

   Subnet Mask . . . . . . . . . . . : 255.255.255.0

   Lease Obtained. . . . . . . . . . : 24 февраля 2022 г. 13:08:10

   Lease Expires . . . . . . . . . . : 25 февраля 2022 г. 13:08:09

   Default Gateway . . . . . . . . . : 192.168.91.1

   DHCP Server . . . . . . . . . . . : 192.168.91.1

   DHCPv6 IAID . . . . . . . . . . . : 98104010

   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-25-EE-D7-0E-B0-0C-D1-6B-F7-CA

   DNS Servers . . . . . . . . . . . : 192.168.100.100

                                       192.168.100.101
   NetBIOS over Tcpip. . . . . . . . : Enabled

C:\Users\User>

Linux:

vagrant@host-01:~$ ifconfig

eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500

        inet 10.0.2.15  netmask 255.255.255.0  broadcast 10.0.2.255

        inet6 fe80::a00:27ff:fe73:60cf  prefixlen 64  scopeid 0x20<link>

        ether 08:00:27:73:60:cf  txqueuelen 1000  (Ethernet)

        RX packets 817  bytes 107107 (107.1 KB)

        RX errors 0  dropped 0  overruns 0  frame 0

        TX packets 610  bytes 108751 (108.7 KB)

        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



eth1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500

        inet 192.168.100.101  netmask 255.255.255.0  broadcast 192.168.100.255

        inet6 fe80::a00:27ff:fe71:7152  prefixlen 64  scopeid 0x20<link>

        ether 08:00:27:71:71:52  txqueuelen 1000  (Ethernet)

        RX packets 87  bytes 18846 (18.8 KB)

        RX errors 0  dropped 0  overruns 0  frame 0

        TX packets 19  bytes 1456 (1.4 KB)

        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536

        inet 127.0.0.1  netmask 255.0.0.0

        inet6 ::1  prefixlen 128  scopeid 0x10<host>

        loop  txqueuelen 1000  (Local Loopback)

        RX packets 24  bytes 1880 (1.8 KB)

        RX errors 0  dropped 0  overruns 0  frame 0

        TX packets 24  bytes 1880 (1.8 KB)

        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



vagrant@host-01:~$

vagrant@host-01:~$ ip a

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000

    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00

    inet 127.0.0.1/8 scope host lo

       valid_lft forever preferred_lft forever

    inet6 ::1/128 scope host

       valid_lft forever preferred_lft forever

2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 

1000

    link/ether 08:00:27:73:60:cf brd ff:ff:ff:ff:ff:ff

    inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic eth0

       valid_lft 84974sec preferred_lft 84974sec

    inet6 fe80::a00:27ff:fe73:60cf/64 scope link

       valid_lft forever preferred_lft forever

3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 
1000

    link/ether 08:00:27:71:71:52 brd ff:ff:ff:ff:ff:ff

    inet 192.168.100.101/24 brd 192.168.100.255 scope global eth1

       valid_lft forever preferred_lft forever

    inet6 fe80::a00:27ff:fe71:7152/64 scope link

       valid_lft forever preferred_lft forever

vagrant@host-01:~$




2. Какой протокол используется для распознавания соседа по сетевому интерфейсу? Какой пакет и команды есть в Linux для этого?

Ответ: 

Протокол: LLDP

Пакет: lldpd

команда: lldpctl



3. Какая технология используется для разделения L2 коммутатора на несколько виртуальных сетей? Какой пакет и команды есть в Linux для этого? Приведите пример конфига.

Ответ: 

Технология VLAN

root@host-01:~# vconfig add eth1 5



Warning: vconfig is deprecated and might be removed in the future, please migrate to ip(route2) as soon as possible!



root@host-01:~# vconfig add eth1 6


Warning: vconfig is deprecated and might be removed in the future, please migrate to ip(route2) 
as soon as possible!



root@host-01:~# ip -br link

lo               UNKNOWN        00:00:00:00:00:00 <LOOPBACK,UP,LOWER_UP>

eth0             UP             08:00:27:73:60:cf <BROADCAST,MULTICAST,UP,LOWER_UP>

eth1             UP             08:00:27:71:71:52 <BROADCAST,MULTICAST,UP,LOWER_UP>

eth1.5@eth1      DOWN           08:00:27:71:71:52 <BROADCAST,MULTICAST>

eth1.6@eth1      DOWN           08:00:27:71:71:52 <BROADCAST,MULTICAST>

root@host-01:~#





4. Какие типы агрегации интерфейсов есть в Linux? Какие опции есть для балансировки нагрузки? Приведите пример конфига.

Ответ:

1) типы bonding:
 Link Aggregation ( т.е. увеличение пропускной способности)
 High Availability

2) есть следующие режины (modes) агрегации интерфейсов:

•	Mode 0 (balance-rr): также известный как round-robin mode. Пакеты последовательно
отправляются и приходят через каждый из интерфейсов. Режим обеспеяивает балансировку нагрузки на интерфейсы. 

•	Mode 1 (active-backup): Работает только один интерфейс, второй находится в резерве. Если активный интерфейс выключается , резервный начинает работать. Режим обеспечивет отказоустойчивость интерфейсов.

•	Mode 2 (balance-xor): режим определяет, через какой интерфейс отправить пакеты, в зависимости от MAC-адресов источника и получателя. MAC-адрес источника использует логику исключающего или (XOR) с MAC-адресом назначения. Этот расчет гарантирует, что для каждого MAC-адреса назначения выбирается один и тот же резерный интерфейс. Режим обеспечивает отказоустойчивость и балансировку нагрузки.

•	Mode 3 (broadcast): Все пакеты отправляются через каждый интерфейс. Режим обеспечивет отказоустойчивость интерфейсов.

•	Mode 4 (802.3ad): Режим создает группу аггрегации которая  that используют одни и те же настройки скорости и дуплекса. Для режима требуется коммутатор, поддерживающий стандарт IEEE 802.3ad. Режим 4 использует все интерфейсы в активной группе агрегации. Например, вы можете объединить три порта 1 Гбит/с (GBPS) в магистральный порт 3 Гбит/с. Это эквивалентно наличию одного интерфейса со скоростью 3 Гбит/с. Режим обеспечивает отказоустойчивость и балансировку нагрузки.

•	Mode 5 (balance-tlb): режим гарантирует, что распределение исходящего трафика настроено в соответствии с нагрузкой на каждый интерфейс.Если назначенный интерфейс не получает трафик, то назначается другой интерфейс. Режим обеспечивает отказоустойчивость и балансировку нагрузки.

•	Mode 6 (balance-alb): Полученные пакеты распределяются по нагрузке посредством согласования протокола разрешения адресов (ARP). Этот режим обеспечивает отказоустойчивость и балансировку нагрузки.

3) Пример конфига bonding:

Create the file ifcfg-bond1 and modify the configuration by using the following commands:

~]#cd /etc/sysconfig/network-scripts

~]#cat ifcfg-bond1

DEVICE=bond1

TYPE=Ethernet

ONBOOT=yes

USERCTL=no

NM_CONTROLLED=no

MTU=9000

BOOTPROTO=static

IPADDR=179.254.0.2

PREFIX=16


DNS1=<DNS_IP>

BONDING_OPTS="mode=802.3ad miimon=100 lacp_rate=fast xmit_hash_policy=layer2+3"

Modify the slave interface (slave1 and slave2) configurations by using the following commands:


~]#cat ifcfg-p5p1

DEVICE=p5p1

BOOTPROTO=none

ONBOOT=yes


SLAVE=yes

USERCTL=no

NM_CONTROLLED=no

MASTER=bond1




~]#cat ifcfg-p5p2

DEVICE=p5p2

BOOTPROTO=none

ONBOOT=yes

SLAVE=yes

USERCTL=no

NM_CONTROLLED=no

MASTER=bond1



4) опции для баланфировки нагрузки:

ad_select=value - Указывает используемую логику выбора агрегации 802.3ad

arp_interval=time_in_milliseconds - Указывает в миллисекундах, как часто выполняется мониторинг ARP.

arp_ip_target=ip_address[,ip_address_2,…ip_address_16] - Указывает целевой IP-адрес запросов ARP, когда параметр arp_interval включен.

arp_validate=value  - Проверка источника/назначения ARP-probe

downdelay=time_in_milliseconds - Указывает (в миллисекундах), как долго ждать после сбоя соединения перед его отключением.

fail_over_mac=value  - Указывает, должен ли режим активного резервного копирования устанавливать для всех интерфейсов один и тот же MAC-адрес или, если он включен, выполнять специальную обработку MAC-адреса соединения в соответствии с выбранной политикой.

lacp_rate=value - Определяет скорость, с которой интерфейсы собанные в агрегированный канал должны передавать пакеты LACPDU в режиме 802.3ad.

miimon=time_in_milliseconds - Указывает (в миллисекундах), как часто происходит мониторинг канала MII.

mode=value - указывает политику агрегации (подродно описан mode 0 - mode 6 выше)

primary=interface_name - Задает имя основного интерфейса.

primary_reselect=value  - Задает политику повторного выбора для основного и резервного интерфейса.

resend_igmp=range - Указывает количество отчетов о членстве IGMP, которые должны быть выпущены после аварийного переключения (failover)

updelay=time_in_milliseconds - Указывает (в миллисекундах), как долго ждать перед включением резервного интерфейса

use_carrier=number - указывает, должен ли miimon использовать MII/ETHTOOL ioctls или netif_carrier_ok() для определения состояния канала

xmit_hash_policy=value - указывает transmit hash policy используемую для slave selection in balance-xor and 802.3ad modes

5. Сколько IP адресов в сети с маской /29 ? Сколько /29 подсетей можно получить из сети с маской /24. Приведите несколько примеров /29 подсетей внутри сети 10.10.10.0/24.

Ответ:

1) под хосты можно использовать 6 ip адресов с маской /29.

2) сеть с маской /24 можно разделить на 32 подсети с маской /29. 

3) примеры /29 подсетей внутри сети 10.10.10.0/24: 10.10.10.0/29, 10.10.10.8/29, 10.10.10.16/29 


root@host-01:~# ipcalc 10.10.10.0/29

Address:   10.10.10.0           00001010.00001010.00001010.00000 000

Netmask:   255.255.255.248 = 29 11111111.11111111.11111111.11111 000

Wildcard:  0.0.0.7              00000000.00000000.00000000.00000 111

=>

Network:   10.10.10.0/29        00001010.00001010.00001010.00000 000

HostMin:   10.10.10.1           00001010.00001010.00001010.00000 001

HostMax:   10.10.10.6           00001010.00001010.00001010.00000 110

Broadcast: 10.10.10.7           00001010.00001010.00001010.00000 111

Hosts/Net: 6                     Class A, Private Internet



root@host-01:~# ipcalc 10.10.10.0/24

Address:   10.10.10.0           00001010.00001010.00001010. 00000000

Netmask:   255.255.255.0 = 24   11111111.11111111.11111111. 00000000

Wildcard:  0.0.0.255            00000000.00000000.00000000. 11111111

=>

Network:   10.10.10.0/24        00001010.00001010.00001010. 00000000

HostMin:   10.10.10.1           00001010.00001010.00001010. 00000001

HostMax:   10.10.10.254         00001010.00001010.00001010. 11111110

Broadcast: 10.10.10.255         00001010.00001010.00001010. 11111111

Hosts/Net: 254                   Class A, Private Internet


root@host-01:~#



6. Задача: вас попросили организовать стык между 2-мя организациями. Диапазоны 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 уже заняты. Из какой подсети допустимо взять частные IP адреса? Маску выберите из расчета максимум 40-50 хостов внутри подсети.

Ответ: 

можно использовать сеть 100.64.0.0/26.

маска /26:  255.255.255.192 на 62 хоста


7. Как проверить ARP таблицу в Linux, Windows? Как очистить ARP кеш полностью? Как из ARP таблицы удалить только один нужный IP?


Ответ:
Linux:
●	arp -a проверить ARP таблицу 

●	sudo ip neigh flush all - очистить ARP кэш полностью

●	sudo arp -d 192.168.100.100  - удалить нужный хост из ARP таблицы


Windows:

●	arp -a проверить ARP таблицу - проверить таблицу

●	arp -d очистить ARP кэш полностью

●	arp -d 192.168.100.100 удалить нужный хост из ARP таблицы


