## Install PECL Libraries
```sh
sudo pecl install redis
sudo pecl install mongodb
```
## Add Library(.so) files to `php.ini`
* sudo gedit /etc/php/7.2/cli/php.ini
```sh
extension=redis.so
extension=mongodb.so
```
