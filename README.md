![lemp-structure](https://user-images.githubusercontent.com/36474638/122211855-dc90ae00-ceaf-11eb-96ec-94c14e014313.png)

<h3>Описание</h3>
1 STACK ginx+mariadb+php-fpm+memcached+haproxy
 
 
<hr></hr>
<h3>Порядок действий</h3>
На сервер ансибла добавить плейбуки из https://github.com/reeves0x0/lemp2/tree/main/ansible Первым запустить install-docker.yaml он добавляет репозиторий docker, установит зависимости, docker, docker-compose, клонит репу lemp2 из мастер ветки и запускает docker-compose.yaml файл.

docker-compose.yaml - собирает контейнеры nginx+mariadb+php-fpm+memcached+haproxy. Данные для БД берет из .env файла (создать самостоятельно, тут для примера синтаксиса). В хостовую машину прокинуты volume для быстрой подстановки нужных конфигов и чтения логов. на каждый контейнер для удобства будет свой playbook. 

Плейбуки в папках lemp2/ansible/haproxy/  lemp2/ansible/maria/   lemp2/ansible/php-fpm/ предназначены для быстрой смены конфигов
       
не забыть применить права на папку chmod 0750 -R /opt/docker/lemp2/mysql/log (ансибл)


<h3>maria BD replication (master-slave)</h3>

для создания репликации БД необходимо запустить несколько плейбуков из папки lemp2/ansible/maria

lemp2/ansible/maria/master-maria.yaml  обновить файл my.cnf (настройки для master) и перезапустит контейнер database_srv

lemp2/ansible/maria/slave-maria.yaml  обновить файл my.cnf (настройки для slave) и перезапустит контейнер database_srv

lemp2/ansible/maria/dump_bd.yaml сделает бэкап базы на мастере и сложит его volume 

lemp2/ansible/maria/restore_bd.yaml  заберет бэкап бд из volume на локальный сервер, скопирует его на slave, создаст БД и восстановит базу из бэкапа

lemp2/ansible/maria/replication.yaml Настройка самой репликации.Создает юзера для репликаци, забирает данные binlog position/file и передает их передает их на slave
