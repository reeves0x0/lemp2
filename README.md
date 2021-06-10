![lemp-structure](https://user-images.githubusercontent.com/36474638/121544598-8684bc00-ca12-11eb-99ba-cf4b6feb873d.jpg)
<h3>Описание</h3>
1 STACK ginx+mariadb+php-fpm+memcached+haproxy

2 ansible/install-docker.yaml playbook для ansible - добавляет репозиторий docker, установит зависимости, docker, docker-compose, клонит репу lemp2 из мастер ветки и запускает docker-compose.yaml файл.

3 docker-compose.yaml - собирает контейнеры nginx+mariadb+php-fpm+memcached+haproxy. Данные для БД берет из .env файла. В хостовую машину прокинуты volume для быстрой подстановки нужных конфигов и чтения логов. На данном этапе конфиги имеют вид стандартных, для production - конфиги будем заливать  через ansible, на каждый контейнер будет свой playbook. 

--------> NGINX идет с self signed сертификатом (/nginx/cert/)

--------> mariaBD указать свои названия юзера, бд, пароли в файле .env

--------> PHP-pool

--------> MEMCcached

--------> HAproxy 
<hr></hr>
<h3>Порядок действий</h3>
