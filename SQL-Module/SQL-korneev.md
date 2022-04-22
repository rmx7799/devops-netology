# Домашнее задание к занятию "6.2. SQL"

## Введение

Перед выполнением задания вы можете ознакомиться с 
[дополнительными материалами](https://github.com/netology-code/virt-homeworks/tree/master/additional/README.md).

## Задача 1

Используя docker поднимите инстанс PostgreSQL (версию 12) c 2 volume, 
в который будут складываться данные БД и бэкапы.

Приведите получившуюся команду или docker-compose манифест.

Ответ:

docker pull postgres:12

docker volume create vol2

docker volume create vol1

docker run --rm --name postgres-docker -e POSTGRES_PASSWORD=postgres  -v vol1:/var/lib/postgresql/data -v vol2:/var/lib/postgresql postgres:12


## Задача 2

В БД из задачи 1: 
- создайте пользователя test-admin-user и БД test_db
- в БД test_db создайте таблицу orders и clients (спeцификация таблиц ниже)
- предоставьте привилегии на все операции пользователю test-admin-user на таблицы БД test_db
- создайте пользователя test-simple-user  
- предоставьте пользователю test-simple-user права на SELECT/INSERT/UPDATE/DELETE данных таблиц БД test_db

Таблица orders:
- id (serial primary key)
- наименование (string)
- цена (integer)

Таблица clients:
- id (serial primary key)
- фамилия (string)
- страна проживания (string, index)
- заказ (foreign key orders)

Приведите:
- итоговый список БД после выполнения пунктов выше,
- описание таблиц (describe)
- SQL-запрос для выдачи списка пользователей с правами над таблицами test_db
- список пользователей с правами над таблицами test_db

Ответ:

postgres=# \l

                                 List of databases

   Name    |  Owner   | Encoding |  Collate   |   Ctype    |   Access privileges

-----------+----------+----------+------------+------------+-----------------------

 postgres  | postgres | UTF8     | en_US.utf8 | en_US.utf8 |

 template0 | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres          +

           |          |          |            |            | postgres=CTc/postgres

 template1 | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres          +

           |          |          |            |            | postgres=CTc/postgres

 test_db   | postgres | UTF8     | en_US.utf8 | en_US.utf8 |
(4 rows)


postgres=# \dt
          List of relations

 Schema |  Name   | Type  |  Owner

--------+---------+-------+----------

 public | clients | table | postgres

 public | orders  | table | postgres
(2 rows)

postgres=# \d+ clients

                                   Table "public.clients"

  Column  |  Type   | Collation | Nullable | Default | Storage  | Stats target | Description

----------+---------+-----------+----------+---------+----------+--------------+-------------

 id       | integer |           | not null |         | plain    |              |

 lastname | text    |           |          |         | extended |              |

 country  | text    |           |          |         | extended |              |

 booking  | integer |           |          |         | plain    |              |

Indexes:

    "clients_pkey" PRIMARY KEY, btree (id)

Foreign-key constraints:

    "clients_booking_fkey" FOREIGN KEY (booking) REFERENCES orders(id)

Access method: heap

postgres=# \d+ orders

                                   Table "public.orders"

 Column |  Type   | Collation | Nullable | Default | Storage  | Stats target | Description

--------+---------+-----------+----------+---------+----------+--------------+-------------

 id     | integer |           | not null |         | plain    |              |

 name   | text    |           |          |         | extended |              |

 price  | integer |           |          |         | plain    |              |

Indexes:

    "orders_pkey" PRIMARY KEY, btree (id)

Referenced by:

    TABLE "clients" CONSTRAINT "clients_booking_fkey" FOREIGN KEY (booking) REFERENCES orders(id)

Access method: heap

postgres=#

SELECT grantee, string_agg(privilege_type, ', ') AS privileges FROM information_schema.
role_table_grants WHERE table_name='orders' GROUP BY grantee;

SELECT grantee, string_agg(privilege_type, ', ') AS privileges FROM information_schema.role_table_grants WHERE table_name='clients' GROUP BY grantee;


postgres=# SELECT grantee, string_agg(privilege_type, ', ') AS privileges FROM information_schema.role_table_grants WHERE table_name='orders' GROUP BY grantee;

     grantee      |                          privileges

------------------+---------------------------------------------------------------

 postgres         | INSERT, SELECT, UPDATE, DELETE, TRUNCATE, REFERENCES, TRIGGER

 test-simple-user | INSERT, SELECT, UPDATE, DELETE

(2 rows)


postgres=# SELECT grantee, string_agg(privilege_type, ', ') AS privileges FROM 
information_schema.role_table_grants WHERE table_name='clients' GROUP BY grantee;

     grantee      |                          privileges

------------------+---------------------------------------------------------------

 postgres         | INSERT, SELECT, UPDATE, DELETE, TRUNCATE, REFERENCES, TRIGGER

 test-simple-user | INSERT, SELECT, UPDATE, DELETE

(2 rows)

postgres=#

## Задача 3

Используя SQL синтаксис - наполните таблицы следующими тестовыми данными:

Таблица orders

|Наименование|цена|
|------------|----|
|Шоколад| 10 |
|Принтер| 3000 |
|Книга| 500 |
|Монитор| 7000|
|Гитара| 4000|

Таблица clients

|ФИО|Страна проживания|
|------------|----|
|Иванов Иван Иванович| USA |
|Петров Петр Петрович| Canada |
|Иоганн Себастьян Бах| Japan |
|Ронни Джеймс Дио| Russia|
|Ritchie Blackmore| Russia|

Используя SQL синтаксис:
- вычислите количество записей для каждой таблицы 
- приведите в ответе:
    - запросы 
    - результаты их выполнения.

Ответ:

postgres=# insert into orders VALUES (1, 'Шоколад', 10), (2, 'Принтер', 3000), (3, 'Книга', 500), (4, 'Монитор', 7000), (5, 'Гитара', 4000);

INSERT 0 5

postgres=# insert into clients VALUES (1, 'Иванов Иван Иванович', 'USA'), (2, 'Петров Петр Петрович', 'Canada'), (3, 'Иоганн Себастьян Бах', 'Japan'), (4, 'Ронни Джеймс Дио', 'Russia'), (5, 'Ritchie Blackmore', 'Russia');

INSERT 0 5

postgres=# select count (*) from orders;

 count

-------

     5
(1 row)

postgres=# select count (*) from clients;

 count
-------

     5

(1 row)

postgres=#

## Задача 4

Часть пользователей из таблицы clients решили оформить заказы из таблицы orders.

Используя foreign keys свяжите записи из таблиц, согласно таблице:

|ФИО|Заказ|
|------------|----|
|Иванов Иван Иванович| Книга |
|Петров Петр Петрович| Монитор |
|Иоганн Себастьян Бах| Гитара |

Приведите SQL-запросы для выполнения данных операций.

Приведите SQL-запрос для выдачи всех пользователей, которые совершили заказ, а также вывод данного запроса.
 
Подсказк - используйте директиву `UPDATE`.

Ответ:


postgres=# update  clients set booking = 3 where id = 1;

UPDATE 1

postgres=# update  clients set booking = 4 where id = 2;

UPDATE 1

postgres=# update  clients set booking = 5 where id = 3;

UPDATE 1

postgres=#

postgres=# select * from clients as c where  exists (select id from orders as o where c.booking = o.id);

 id |       lastname       | country | booking

----+----------------------+---------+---------

  1 | Иванов Иван Иванович | USA     |       3

  2 | Петров Петр Петрович | Canada  |       4

  3 | Иоганн Себастьян Бах | Japan   |       5

(3 rows)

## Задача 5

Получите полную информацию по выполнению запроса выдачи всех пользователей из задачи 4 
(используя директиву EXPLAIN).

Приведите получившийся результат и объясните что значат полученные значения.

Ответ:

postgres=# explain select * from clients as c where  exists (select id from orders as o where c.booking = o.id);
                               QUERY PLAN

------------------------------------------------------------------------

 Hash Join  (cost=37.00..57.24 rows=810 width=72)

   Hash Cond: (c.booking = o.id)

   ->  Seq Scan on clients c  (cost=0.00..18.10 rows=810 width=72)

   ->  Hash  (cost=22.00..22.00 rows=1200 width=4)

         ->  Seq Scan on orders o  (cost=0.00..22.00 rows=1200 width=4)

(5 rows)

postgres=#

пояснение.

вывод explain показывает стоимость(нагрузку на исполнение) запроса , шаги связи и сбор сканирование таблиц после связи.


## Задача 6

Создайте бэкап БД test_db и поместите его в volume, предназначенный для бэкапов (см. Задачу 1).

Остановите контейнер с PostgreSQL (но не удаляйте volumes).

Поднимите новый пустой контейнер с PostgreSQL.

Восстановите БД test_db в новом контейнере.

Приведите список операций, который вы применяли для бэкапа данных и восстановления. 


---

Ответ:

docker exec -t postgres-docker pg_dump -U postgres test_db -f /var/lib/postgresql/data/dump_test.sql


docker run --rm --name postgres-docker2 -e POSTGRES_PASSWORD=postgres  -v vol1:/var/lib/postgresql/data -v vol2:/var/lib/postgresql postgres:12


PostgreSQL Database directory appears to contain a database; Skipping initialization

2022-04-22 15:10:23.796 UTC [1] LOG:  starting PostgreSQL 12.10 (Debian 12.10-1.pgdg110+1) on 
x86_64-pc-linux-gnu, compiled by gcc (Debian 10.2.1-6) 10.2.1 20210110, 64-bit

2022-04-22 15:10:23.797 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432

2022-04-22 15:10:23.797 UTC [1] LOG:  listening on IPv6 address "::", port 5432

2022-04-22 15:10:23.810 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"

2022-04-22 15:10:23.836 UTC [27] LOG:  database system was shut down at 2022-04-22 15:08:26 UTC

2022-04-22 15:10:23.845 UTC [1] LOG:  database system is ready to accept connections


docker exec -i postgres-docker2 psql -U postgres -d test_db -f /var/lib/postgresql/data/dump_test.sql

SET

SET

SET

SET

SET

 set_config

------------


(1 row)

SET

SET

SET

SET


PS C:\Program Files\Docker\Docker> docker ps

CONTAINER ID   IMAGE         COMMAND                  CREATED         STATUS         PORTS      
NAMES

ce23dc02ef3a   postgres:12   "docker-entrypoint.s…"   4 minutes ago   Up 4 minutes   5432/tcp   
postgres-docker2


PS C:\Program Files\Docker\Docker>

PS C:\Program Files\Docker\Docker>

PS C:\Program Files\Docker\Docker> docker exec -it postgres-docker2 bash

root@ce23dc02ef3a:/# su postgres

postgres@ce23dc02ef3a:/$ psql

psql (12.10 (Debian 12.10-1.pgdg110+1))

Type "help" for help.

postgres=#

postgres=# \l
                                 List of databases

   Name    |  Owner   | Encoding |  Collate   |   Ctype    |   Access privileges

-----------+----------+----------+------------+------------+-----------------------
 postgres  | postgres | UTF8     | en_US.utf8 | en_US.utf8 |

 template0 | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres          +

           |          |          |            |            | postgres=CTc/postgres

 template1 | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres          +

           |          |          |            |            | postgres=CTc/postgres

 test_db   | postgres | UTF8     | en_US.utf8 | en_US.utf8 |

(4 rows)

postgres=# \dt

          List of relations

 Schema |  Name   | Type  |  Owner

--------+---------+-------+----------

 public | clients | table | postgres

 public | orders  | table | postgres


(2 rows)




postgres=# \d+ clients

                                   Table "public.clients"


  Column  |  Type   | Collation | Nullable | Default | Storage  | Stats target | Description

----------+---------+-----------+----------+---------+----------+--------------+-------------


 id       | integer |           | not null |         | plain    |              |

 lastname | text    |           |          |         | extended |              |

 country  | text    |           |          |         | extended |              |

 booking  | integer |           |          |         | plain    |              |


Indexes:

    "clients_pkey" PRIMARY KEY, btree (id)

Foreign-key constraints:

    "clients_booking_fkey" FOREIGN KEY (booking) REFERENCES orders(id)

Access method: heap


postgres=# \d+ orders
                                   Table "public.orders"

 Column |  Type   | Collation | Nullable | Default | Storage  | Stats target | Description

--------+---------+-----------+----------+---------+----------+--------------+-------------

 id     | integer |           | not null |         | plain    |              |

 name   | text    |           |          |         | extended |              |

 price  | integer |           |          |         | plain    |              |

Indexes:

    "orders_pkey" PRIMARY KEY, btree (id)

Referenced by:

    TABLE "clients" CONSTRAINT "clients_booking_fkey" FOREIGN KEY (booking) REFERENCES orders(id)

Access method: heap





postgres=# \dt+ orders

                    List of relations

 Schema |  Name  | Type  |  Owner   | Size  | Description

--------+--------+-------+----------+-------+-------------


 public | orders | table | postgres | 16 kB |

(1 row)


postgres=# \dt+ clients

                     List of relations

 Schema |  Name   | Type  |  Owner   | Size  | Description

--------+---------+-------+----------+-------+-------------

 public | clients | table | postgres | 16 kB |

(1 row)


postgres=#
### Как cдавать задание

Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.

---