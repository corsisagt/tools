# Guia de instalacion odoo 12 en ubuntu 18.04

#### Actualizando el sistema
```
$ sudo apt update 
$ sudo apt upgrade
```
#### Instalamos Git
```
$ sudo apt install git
```
#### Python3
```
$ sudo apt install python3-pip
$ sudo apt install python-dev
```
#### Instalamos Dependencias
```
$ sudo apt install -y libpq-dev libldap2-dev libsasl2-dev libxslt1-dev python3-setuptools python3-wheel wget 
ca-certificates openssl build-essential libssl-dev libxrender-dev git-core libx11-dev libxext-dev 
libfontconfig1-dev libfreetype6-dev fontconfig
$ pip3 install wheel
```
#### Clonamos el Codigo Fuente de odoo
```
$ sudo git clone -b 12.0 https://www.github.com/odoo/odoo /opt/
```
#### Instalacion y configuracion de Postgresql

Agregamos nuevo ppa
```
$ sudo nano /etc/apt/sources.list.d/pgdg.list
```
Se Agrega las siguientes lineas al archivo.
```
deb http://apt.postgresql.org/pub/repos/apt/ bionic-pgdg main
```
Cerramos nano

Agregamos llave.
```
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
```
Actualizamos repositorios
```
$ sudo apt update
```
Instalamos Postgresql
```
$ sudo apt install postgresql-11
```
Creamos usuarios de la base de datos
```
$ sudo su postgres
$ cd
$ createuser -s odoo
$ createuser -s nombre_usr_so
```
Cambiamos las claves de los usuarios creados
```
$ psql
$ alter user usuario  with password 'laclave';
$ \q
$ exit
```
#### Instalamos requerimientos de odoo
```
$ pip3 install -r /opt/odoo/requirements.txt
```
#### Instalamos visor PDF
```
$ wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.4/wkhtmltox-0.12.4_linux-generic-amd64.tar.xz
$ tar xvf wkhtmltox*.tar.xz
$ sudo mv wkhtmltox/bin/wkhtmlto* /usr/bin
```
#### Instalamos google app api
```
$ sudo wget https://pypi.python.org/packages/a8/70/bd554151443fe9e89d9a934a7891aaffc63b9cb5c7d608972919a002c03c/gdata-2.0.18.tar.gz
$ sudo tar zxvf gdata-2.0.18.tar.gz
$ sudo chown -R odoo: gdata-2.0.18
$ sudo -s
$ cd gdata-2.0.18/
$ python setup.py install
$ exit
```




