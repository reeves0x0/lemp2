![tree](https://user-images.githubusercontent.com/36474638/125097304-aaedba00-e0de-11eb-823c-ae00c52edd53.png)

<h3>Описание</h3>
1 STACK ginx+mariadb+php-fpm+memcached+haproxy
 
 
<hr></hr>
<h3>Порядок действий</h3>

mkdir /opt/docker && cd /opt/docker/

git clone https://github.com/reeves0x0/lemp2
 
ansible-playbook /opt/docker/lemp2/ansible/global.yaml --ask-vault-pass 
 
<hr></hr>
<h3>Benchmark (yandex Tank)</h3>


docker run --rm -v /opt/docker/lemp2/benchmark:/var/loadtest -it --network lemp2_default direvius/yandex-tank
