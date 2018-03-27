Cen�rio
=================================================================================

GLPI

CENTOS 7 - GLPI
================================================================================

## Instala��o

1- Atualizando sistema

	yum install update

2- Instala��o de de ambiente LAMP

	yum install -y httpd
	yum install -y maraiadb
	yum install -y mariadb-server
	rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
	rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm
	yum install -y php70w php70w-gd php70w-mstring
	yum install -y php70w-mysql

3- Baixar GLPI

	wget https://github.com/glpi-project/glpi/releases/download/9.2.2/glpi-9.2.2.tgz

4- Descompactar arquivo baixado do GLPI no diret�rio padr�o do Apache

	tar -xzf glpi-9.2.2.tgz -C /var/www/html

5- Alterar permiss�es do da pasta glpi

	chmod -R 775 /var/www/html/
	chown -R www-data. /var/www/html

6- Inciar e habiltar servi�os

	systemctl start httpd
	systemctl enable httpd
	systemctl start mariadb
	systemctl enable mariadb

7- Cadastrar senha mysql

	mysql_secure_installation

8- Criar base de dados chamado glpi e usu�rio glpi

	mysql -u root -p 	

		create database glpi;
		grant all privileges on glpi.* to glpi@localhost identified by 'SENHA-USUARIO-GLPI'.;
		flush privelges
		quit;

9- Reiniciar servi�os

	systemctl restart httpd
	systemctl restart mariadb


10- Parar e Desabilitar firewall

	systemctl stop firewalld
	systemctl disable firewalld

