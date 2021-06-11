![lemp-structure](https://user-images.githubusercontent.com/36474638/121544598-8684bc00-ca12-11eb-99ba-cf4b6feb873d.jpg)
<h3>Описание</h3>
1 STACK ginx+mariadb+php-fpm+memcached+haproxy
 
 
<hr></hr>
<h3>Порядок действий</h3>
На сервер ансибла добавить плейбуки из https://github.com/reeves0x0/lemp2/tree/main/ansible Первым запустить install-docker.yaml он добавляет репозиторий docker, установит зависимости, docker, docker-compose, клонит репу lemp2 из мастер ветки и запускает docker-compose.yaml файл.

docker-compose.yaml - собирает контейнеры nginx+mariadb+php-fpm+memcached+haproxy. Данные для БД берет из .env файла (создать самостоятельно, тут для примера синтаксиса). В хостовую машину прокинуты volume для быстрой подстановки нужных конфигов и чтения логов. на каждый контейнер для удобства будет свой playbook. 

Описание плейбуков:



