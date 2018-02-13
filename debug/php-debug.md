## PHP Debugging
1. Collect
```sh
    php -i > phpinfo.txt 
```
2. Put Contents to [PHP Custom Debugger](https://xdebug.org/wizard.php), Download the DLL file and put in ext folder of PHP

3. Append following code in php.ini

```sh
    zend_extension = php_xdebug-XXXXX-x86_64.dll
    [xdebug]
    xdebug.remote_enable = On
    xdebug.remote_host=localhost
    xdebug.remote_port=9000
    xdebug.remote_handler="dbgp"
```
4. In Jetbrains configure PHP Environment.
5. Congrats! you're done.
