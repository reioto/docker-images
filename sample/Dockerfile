FROM centos:7

RUN yum -y update
RUN yum -y install php.x86_64 \
php-bcmath.x86_64 \
php-cli.x86_64 \
php-common.x86_64 \
php-gd.x86_64 \
php-intl.x86_64 \
php-mbstring.x86_64 \
php-pdo.x86_64 \
php-process.x86_64 \
php-pspell.x86_64 \
php-recode.x86_64 \
php-snmp.x86_64 \
php-soap.x86_64 \
php-xml.x86_64 \
php-xmlrpc.x86_64 \
php-ldap.x86_64

RUN yum -y install mod_ssl
RUN yum clean all

VOLUME /var/www/html 

EXPOSE 80
CMD["systemctl", "start", "httpd"]
