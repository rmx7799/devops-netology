
# Домашнее задание к занятию "5.3. Введение. Экосистема. Архитектура. Жизненный цикл Docker контейнера"

## Как сдавать задания

Обязательными к выполнению являются задачи без указания звездочки. Их выполнение необходимо для получения зачета и диплома о профессиональной переподготовке.

Задачи со звездочкой (*) являются дополнительными задачами и/или задачами повышенной сложности. Они не являются обязательными к выполнению, но помогут вам глубже понять тему.

Домашнее задание выполните в файле readme.md в github репозитории. В личном кабинете отправьте на проверку ссылку на .md-файл в вашем репозитории.

Любые вопросы по решению задач задавайте в чате учебной группы.

---

## Задача 1

Сценарий выполения задачи:

- создайте свой репозиторий на https://hub.docker.com;
- выберете любой образ, который содержит веб-сервер Nginx;
- создайте свой fork образа;
- реализуйте функциональность:
запуск веб-сервера в фоне с индекс-страницей, содержащей HTML-код ниже:
```
<html>
<head>
Hey, Netology
</head>
<body>
<h1>I’m DevOps Engineer!</h1>
</body>
</html>
```
Опубликуйте созданный форк в своем репозитории и предоставьте ответ в виде ссылки на https://hub.docker.com/username_repo.

### Ответ:

Ссылка на образ контейнера https://hub.docker.com/layers/nginx/rmx7799/nginx/version1.0/images/sha256-fa767c04b2bbc65f4209f91681e87105fa3084c3d3e9485b3f33849d3cbfae79?context=repo

Демонстрация работы:
```
root@bda838fba1a3:/usr/share/nginx/html# curl http://localhost
<html>
<head>
Hey, Netology
</head>
<body>
<h1>I’m DevOps Engineer!</h1>
</body>
</html>
root@bda838fba1a3:/usr/share/nginx/html#

`````




## Задача 2

Посмотрите на сценарий ниже и ответьте на вопрос:
"Подходит ли в этом сценарии использование Docker контейнеров или лучше подойдет виртуальная машина, физическая машина? Может быть возможны разные варианты?"

Детально опишите и обоснуйте свой выбор.

--

Сценарий:

- Высоконагруженное монолитное java веб-приложение;

### Ответ: Думаю, что для данной задачи лучше подойдет виртуальную машину или отдельный сервер. 


- Nodejs веб-приложение;

### Ответ: Для данного сценария лучше подойдёт контейнеры. 


- Мобильное приложение c версиями для Android и iOS;

### Ответ: Для данной задачи Docker скорее не подойдёт. Для данной задачи лучше использовать виртуальную машину.


- Шина данных на базе Apache Kafka;

### Ответ: Думаю что если это будет использоваться для продуктива, лучше использовать виртуальную машину, но можно использовать и Docker.


- Elasticsearch кластер для реализации логирования продуктивного веб-приложения - три ноды elasticsearch, два logstash и две ноды kibana;

### Ответ: На основании открытых источников данный сценарий в Docker ELK запустить можно.

- Мониторинг-стек на базе Prometheus и Grafana;

### Ответ: В контейнерах можно запустить, на основании рекомендаций это вполне распространенная практика. 

- MongoDB, как основное хранилище данных для java-приложения;

### Ответ: Для данной задачи на лучше подойдет виртуальная машина, так как база имеет свойство расти и конфигурацию сервера придётся менять время от времени. Однако судя по статьям в интернете, в Docker запустить тоже возможно.

- Gitlab сервер для реализации CI/CD процессов и приватный (закрытый) Docker Registry.

### Ответ: На мой взгляд для данного сценария подойдёт ВМ, так как GitLab предпологает частое изменение данных и в случае удаления контейнера возможна потеря данных.

## Задача 3

- Запустите первый контейнер из образа ***centos*** c любым тэгом в фоновом режиме, подключив папку ```/data``` из текущей рабочей директории на хостовой машине в ```/data``` контейнера;
- Запустите второй контейнер из образа ***debian*** в фоновом режиме, подключив папку ```/data``` из текущей рабочей директории на хостовой машине в ```/data``` контейнера;
- Подключитесь к первому контейнеру с помощью ```docker exec``` и создайте текстовый файл любого содержания в ```/data```;
- Добавьте еще один файл в папку ```/data``` на хостовой машине;
- Подключитесь во второй контейнер и отобразите листинг и содержание файлов в ```/data``` контейнера.


### Ответ:
Стартуем контейнеры и подключаем папки:
`````
PS C:\Program Files\Docker\Docker> docker run -v /data:/data -dt --name centos centos
dd846ef28de62487aed0b6dcf2cfd423311021fa906728eab8dbcb4edb6c431a
PS C:\Program Files\Docker\Docker> docker run -v /data:/data -dt --name debian debian
0957caa9b1d0778135a64049c5a8a0d43dca08dd6e56004564e01aa959d6f118

Заранее создал в centos и на Localhost текстовые файлы:
результат на Debian:

PS C:\Program Files\Docker\Docker> docker exec -ti debian bash
root@0957caa9b1d0:/# ls
bin  boot  data  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@0957caa9b1d0:/# cd data
root@0957caa9b1d0:/data# ls
test.txt  
root@0957caa9b1d0:/data# cat test.txt
Test File ubuntu
root@0957caa9b1d0:/data#

````