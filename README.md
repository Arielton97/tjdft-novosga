Este arquivo tem permissão 006 para leitura e gravação
## Install webserver apache2
`sudo yum update httpd`

`sudo yum install httpd`

`sudo firewall-cmd --permanent --add-service=http`

`sudo firewall-cmd --reload`

`sudo systemctl start httpd`

`sudo systemctl status httpd`

`hostname -I`

## Install php v. 8.3
### Step 1: Update System Packages
`sudo dnf update`
### Step 2: Habilitar os repositórios EPEL para o RHEL 
`sudo subscription-manager repos --enable codeready-builder-for-rhel-9-$(arch)-rpms`

`sudo dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-9.noarch.rpm`
### Step 3: Habilitar os repositorios Remi para o RHEL
`sudo dnf install https://rpms.remirepo.net/enterprise/remi-release-9.rpm`
### Step 4: Instalar PHP 8.3 para o RHEL
`sudo dnf module install php:remi-8.3`

`php -v`
### Step 5: Instalar extensões PHP adicionais (Opcional)
`sudo dnf search php-*`

`sudo dnf install php-gd php-xml`

`sudo systemctl restart httpd`

## Instalando MySQL no Linux usando o repositório MySQL Yum
### Adicionar Repositório MySQL Yum 
a. Baixar o repositório MySQL Yum (https://dev.mysql.com/downloads/repo/yum/) ou (https://repo.mysql.com/mysql84-community-release-el9-1.noarch.rpm) para a pasta Downloads.
`wget https://repo.mysql.com/mysql84-community-release-el9-1.noarch.rpm`

`sudo yum install plataforma-e-versão-especifica-nome-do-pacote.rpm`

`sudo yum install mysql84-community-release-el9-1.noarch.rpm`

b. Verificar se o repositório MySQL Yum foi adicionado com sucesso usando o comando a seguir.
`yum repolist enabled | grep "mysql.*-community.*"` ou `dnf repolist enabled | grep "mysql.*-community.*"`

## Iniciando o MySQL
a. Após a instalação bem-sucedida do MySQL, é hora de iniciar e habilitar o servidor MySQL com os seguintes comandos:
`systemctl start mysqld`

`systemctl enable mysqld.service`
b. Verificar o status do servidor
`systemctl status mysqld.service` ou `service mysql status`
c. Agora, finalmente, verifique a versão instalada do MySQL usando o seguinte comando.
`mysql --version`

### Protegendo a instalação do MySQL
O comando mysql_secure_installation permite que você proteja sua instalação do MySQL executando configurações importantes, como definir a senha de root, remover usuários anônimos, remover login de root e assim por diante.

Nota: O MySQL versão 8.0 ou superior gera uma senha aleatória temporária após a instalação./var/log/mysqld.log

a. Use o comando abaixo para ver a senha antes de executar o comando seguro do MySQL.
`grep 'temporary password' /var/log/mysqld.log`
b. Depois de saber a senha, você pode executar o seguinte comando para proteger sua instalação do MySQL.
`mysql_secure_installation`

Nota: Digite a nova senha de root significa sua senha temporária de um arquivo ./var/log/mysqld.log

### Conecte ao MySQL Server
`mysql -u root -p`

### Atualizando o MySQL com yum
`yum update mysql-server` o u `dnf update mysql-serve`

## References
[How to install the Apache Web Server on CentOS 7 | DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-centos-7)

[How to install PHP 8.3 in RHEL 9 Linux](https://www.tecmint.com/install-php-in-rhel-9/#:~:text=How%20to%20Install%20PHP%208.3%20in%20RHEL%209,Step%205%3A%20Install%20Additional%20PHP%20Extensions%20%28Optional%29%20)

[How to install MySQL8.0 on RHEL/CentOS 8/7 and Fedora 35](https://www.tecmint.com/install-latest-mysql-on-rhel-centos-and-fedora/)

[How to install MySQL 8.0 on RHEL/CentOS 9/7 and Fedora 35](https://www.tecmint.com/install-latest-mysql-on-rhel-centos-and-fedora/)
