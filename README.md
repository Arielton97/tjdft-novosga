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
### Step 2: Enable EPEL repository in RHEL 
`sudo subscription-manager repos --enable codeready-builder-for-rhel-9-$(arch)-rpms`

`sudo dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-9.noarch.rpm`
### Step 3: Enable Remi Repository in RHEL
`sudo dnf install https://rpms.remirepo.net/enterprise/remi-release-9.rpm`
### Step 4: Install PHP 8.3 in RHEL
`sudo dnf module install php:remi-8.3`

`php -v`
### Step 5: Install Additions PHP Extensions (Optional)
`sudo dnf search php-*`

`sudo dnf install php-gd php-xml`

`sudo systemctl restart httpd`

## Instalando MySQL no Linux usando o repositório MySQL Yum
### Adicionando Repositório MySQL Yum 
a. Vá para a página Baixar o repositório MySQL Yum (https://dev.mysql.com/downloads/repo/yum/) na zona do desenvolvedor do MySQL.
b. Seleciona e baixe o pacote ed lançamento para a sua plataforma.
c. Instale o pacote de versão baixado com o comando a seguir, substituindo platform-and-version-specific-package-name pelo nome do pacote baixado.
`$> sudo yum install platform-and-version-specific-package-name.rpm`

ou baixe do mediafire
[repository-mysql-comunity-rpm](https://download1588.mediafire.com/yu2cm5731bhgLFpQJhDTO90MOKUzspzuKJOK6ynH8D6l3uXes4NeylcaqpjGmYRiKBaCZgzDY3Urdu2xV5J7FscJHbzLegEhUhAZ-qcFIamtg6P6b0XnU_MkHQeeBzGJf_WgRIfy227QcDbyoEXjhJZLxMgy2-SH7u5Aq0Vs4z-B6U0/2n1k655g6lfhzno/mysql84-community-release-el9-1.noarch.rpm)

### Verificar se o reporitório MySQL Yum foi adicionado com êxito pelo seguinte comando
`yum repolist enabled | grep "mysql.*-community.*"`
### Seleção de uma série de lançamentos 
`yum repolist all | grep mysql`
### Para plataformas habilitadas com dnf
`sudo dnf config-manager --disable mysql-8.4-lts-community`

`sudo dnf config-manager --disable mysql-tools-8.4-lts-community`

`sudo dnf config-manager --enable mysql80-community`

`sudo dnf config-manager --enable mysql-tools-community`

### Verifique se o sub-repositórios foram habilitados corretamente
`yum repolist enabled | grep mysql`

## Instalando o MySQL
### Execute o comando
`sudo yum install mysql-community-server`



## References
[How to install the Apache Web Server on CentOS 7 | DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-centos-7)

[How to install PHP 8.3 in RHEL 9 Linux](https://www.tecmint.com/install-php-in-rhel-9/#:~:text=How%20to%20Install%20PHP%208.3%20in%20RHEL%209,Step%205%3A%20Install%20Additional%20PHP%20Extensions%20%28Optional%29%20)

[How to install MySQL8.0 on RHEL/CentOS 8/7 and Fedora 35](https://www.tecmint.com/install-latest-mysql-on-rhel-centos-and-fedora/)

[MySQL :: Manual de Referência do MySQL 8.0 :: 2.5.1 Instalando o MySQL no Linux usando o repositório MySQL Yum](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

