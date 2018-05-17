## xdebug linux install
```sh
https://github.com/xdebug/xdebug
sudo apt install php7.2-dev
cd xdebug-master
phpize
./configure --enable-xdebug
make clean
make
locate mysql.so  [/usr/lib/php/20170718/pdo_mysql.so]
sudo cp modules/xdebug.so /usr/lib/php/20170718/
locate php.ini
sudo gedit /etc/php/7.2/cli/php.ini
```
```sh
zend_extension="/usr/lib/php/20170718/xdebug.so"
xdebug.remote_enable=1
xdebug.remote_handler=dbgp
xdebug.remote_mode=req
xdebug.remote_host=127.0.0.1
xdebug.remote_port=9000
```
```sh
php -version
```
```sh
PHP 7.2.5-0ubuntu0.18.04.1 (cli) (built: May  9 2018 17:21:02) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.2.0, Copyright (c) 1998-2018 Zend Technologies
    with Xdebug v2.7.0alpha2-dev, Copyright (c) 2002-2018, by Derick Rethans
    with Zend OPcache v7.2.5-0ubuntu0.18.04.1, Copyright (c) 1999-2018, by Zend Technologies
```
