0) - pic struc
1) STACK ginx+mariadb+php-fpm+memcached+haproxy

2) /ansible/install-docker.yaml playbook для ansible - добавляет репозиторий docker, установит зависимости, docker, docker-compose, клонит репу lemp2 из мастер ветки и запускает docker-compose.yaml файл.

3) docker-compose.yaml - собирает контейнеры nginx+mariadb+php-fpm+memcached+haproxy. Данные для БД берет из .env файла. В хостовую машину прокинуты volume для быстрой подстановки нужных конфигов и чтения логов. На данном этапе конфиги имеют вид стандартных, для production - конфиги будем заливать  через ansible, на каждый контейнер будет свой playbook.

