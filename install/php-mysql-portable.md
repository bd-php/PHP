### PHP MYSQL Portable Install in Windows

#### PHP Install

* Download [windows.php.net](http://windows.php.net/download/) => Thread Safe 64 Bit PHP (Like VC14 x64 Thread Safe)
* Unzip To ` C:/ ` Drive For Example ` C:/tools/php `
* Rename a ` php.ini-development ` to ` php.ini `
* Uncomment Required Extensions
* Uncomment ` ;extension_dir = "ext" ` to ` extension_dir = "ext" `
* Create System Environmental Path Variable By Latest php ` C:/tools/php `
* Check Whether the php server can be run by
```sh
 php -S localhost:8000
 php -S 0.0.0.0:80   [Access Through Device IP from Outside of PC]
 php -S 0.0.0.0:8000 [Access Through Device IP from Outside of PC]
```

#### MySQL Install

* Download [dev.mysql.com](https://dev.mysql.com/downloads/mysql/) => Windows (x86, 64-bit) ZIP Archive
* Unzil Zip Say for Example ` C:/database/mysql ` Folder
* Make a Copy of ` my-default.ini ` to ` my.ini ` in current Directory
* Make a ` data ` directory in current Folder
* Add these lines in ` my.ini `
* If ` my.ini ` Not Found Then Create ` my.ini ` with Following Configs
```sh
 [mysqld]
 basedir = "C:/database/mysql"
 datadir = "C:/database/mysql/data"
 max_allowed_packet=100M
```

* Navigate to ` C:/database/mysql/bin ` directory through two command prompt
* Run following commands step by step
```sh
 mysqld --initialize
 mysqld --initialize-secure
 mysqld --console
```

* Another command prompt run: ` mysql -h localhost -u root -p newpass `
* An error file will be generated in `data` directory say for example ` username.err `
* Find [Note] A temporary password is generated for ` root@localhost: q1;dusbRjkzJ `
* Connect By this Generated Password
* Executed Following Command to `mysql>` Command Prompt
```sql
 ALTER USER root@localhost IDENTIFIED BY 'newpass'
```
* Now quit and reconnect: ` mysql -h localhost -u root -p newpass `
* Everything is working fine
* Mind it. First Start mysqld by 
```sh
 mysqld --console
```
* Or open cmd and type
```sh
mysqld
```
