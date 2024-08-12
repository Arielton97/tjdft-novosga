### Install webserver apache2
`sudo yum update httpd`

`sudo yum install httpd`

`sudo firewall-cmd --permanent --add-service=http`

`sudo firewall-cmd --reload`

`sudo systemctl start httpd`

`sudo systemctl status httpd`

`hostname -I`

### Install php v. 8.3
## Step 1: Update System Packages
`sudo dnf update`
## Step 2: Enable EPEL repository in RHEL 
`sudo subscription-manager repos --enable codeready-builder-for-rhel-9-$(arch)-rpms`

`sudo dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-9.noarch.rpm`
## Step 3: Enable Remi Repository in RHEL
`sudo dnf install https://rpms.remirepo.net/enterprise/remi-release-9.rpm`
## Step 4: Install PHP 8.3 in RHEL
`sudo dnf module install php:remi-8.3`

`php -v`
## Step 5: Install Additiona PHP Extensions (Optional)
`sudo dnf search php-*`

`sudo dnf install php-gd php-xml`

`sudo systemctl restart httpd`


## References
[How to install the Apache Web Server on CentOS 7 | DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-centos-7)

[How to install PHP 8.3 in RHEL 9 Linux](https://www.tecmint.com/install-php-in-rhel-9/#:~:text=How%20to%20Install%20PHP%208.3%20in%20RHEL%209,Step%205%3A%20Install%20Additional%20PHP%20Extensions%20%28Optional%29%20)


