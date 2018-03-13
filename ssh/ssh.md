## Install ssh2 extension to php
```sh
sudo apt-get install php7.2-cli -y
sudo apt-get install libssh2-1 php-ssh2 -y
```
## Test ssh2 extension
```sh
php -a
php > $result = ssh2_connect('localhost');
php > var_dump($result);
resource(2) of type (SSH2 Session)
```
## File write code
```php
<?php

$ip = '127.0.0.1';
$port = '22';
$user = 'root';
$pass = 'nopass';

$src = 'test.txt';
$filename = 'copied.txt';

$dest = '/var/www/html/'.$filename;

// Set up sftp ssh-sftp connection
$connection = ssh2_connect($ip, $port);
ssh2_auth_password($connection, $user, $pass);

// Create SFTP session
$sftp = ssh2_sftp($connection);

$sftpStream = @fopen('ssh2.sftp://'.$sftp.$dest, 'w');

try {
		
	if (!$sftpStream) {
		throw new Exception("Could not open remote file: $dest");
	}

	$data_to_send = @file_get_contents($src);

	if ($data_to_send === false) {
		throw new Exception("Could not open local file: $src.");
	}

	if (@fwrite($sftpStream, $data_to_send) === false) {
		throw new Exception("Could not send data from file: $src.");
	} else {
		
		//Upload was successful, post-upload actions go here...
		echo "File Copied Successfully";
		
	}

	fclose($sftpStream);
				   
} catch (Exception $e) {

	error_log('Exception: ' . $e->getMessage());

	fclose($sftpStream);
}
```
