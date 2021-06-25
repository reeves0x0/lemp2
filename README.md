![lemp-structure](https://user-images.githubusercontent.com/36474638/122211855-dc90ae00-ceaf-11eb-96ec-94c14e014313.png)

<h3>Описание</h3>
1 STACK ginx+mariadb+php-fpm+memcached+haproxy
 
 
<hr></hr>
<h3>Порядок действий</h3>

mkdir /opt/docker && cd /opt/docker/

git clone https://github.com/reeves0x0/lemp2
 
ansible-playbook /opt/docker/lemp2/ansible/master-yaml
 
