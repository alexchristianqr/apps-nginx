# Laravel(PHP7.2) + Nginx(1.15.5) + Ubuntu(Cosmic18.10)
Configuraciones de NGINX para el deploy de aplicaciones en Laravel PHP, Html5, Vuejs, React, Angular, Nodejs etc.

## Guia
Para usar este repositorio es necesario cumplir lo que indica la guia y continuar paso a paso

## Instalar dependencias npm y composer

``` bash
# Instalar nginx
sudo apt-get install nginx -y

# Instalar nodejs #1
curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
sudo apt-get install nodejs -y

# Instalar nodejs #2
npm cache clean -f
npm install -g n
n stable

# Instalar php
add-apt-repository ppa:ondrej/php
sudo apt-get install software-properties-common
sudo apt-get install python-software-properties -y
sudo apt-get update
sudo apt-get install unzip zip nginx php7.2 php7.2-mysql php7.2-fpm php7.2-mbstring php7.2-xml php7.2-curl php7.2-intl php7.2-xsl -y

# Instalar git
sudo apt-get install git -y

# Instalar composer #1
sudo apt-get install composer -y

# Instalar composer #2
wget https://getcomposer.org/composer.phar
chmod +x composer.phar
mv composer.phar /usr/local/bin/composer
composer self-update

# Instalar certificate with cerbot
add-apt-repository ppa:certbot/certbot
sudo apt-get update
sudo apt-get install python-certbot-nginx -y
certbot --nginx -d yourdomain.com # Una vez installado solo ejecutar este comando para generar certificado SSL
```

## Ejecutar comandos en la consola

``` bash
# Clonar el repositorio GIT
git clone https://github.com/acqrdeveloper/deploy-apps-with-nginx.git myserver

# Ubicarse en la carpeta "myserver"
cd /myserver

# Crear carpeta "www"
mkdir /myserver/www

# Crear carpeta "logs"
mkdir /myserver/logs

# Preparar "nginx"
cd /etc/nginx/ # Testear instalacion
rm -rf /etc/nginx # Eliminar carpeta
ln -s /myserver/nginx /etc/ //Crear link simbolico
```

## Deployar aplicaciones
``` bash
# Habilitar permisos en las siguientes carpetas para un proyecto "Laravel"
chown -R www-data.www-data storage/framework/cache storage/framework/views storage/framework/sessions storage/logs .env vendor 
chown -R www-data.www-data storage .env vendor public
chmod -R 775 storage/framework/cache storage/framework/views storage/framework/sessions storage/logs .env vendor 
chmod -R 775 storage .env vendor public
```
