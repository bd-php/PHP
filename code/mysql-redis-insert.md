## Insert From MySQL to Redis

```php
//////////////////////////////////
$host = '127.0.0.1';
$user = 'root';
$pass = 'nopass';
$db = 'mydb';

$redishost = '127.0.0.1';
$redisport = '6379';
$redispass = 'nopass';
$userdb = 10;
//////////////////////////////////

$con = new mysqli($host, $user, $pass, $db);

$redis = new Redis();
$redis->connect($redishost, $redisport);
$redis->auth($redispass);

$redis->select($userdb);
$redis->flushDB($userdb);

$result = $con->query('select * from users');

if ($result->num_rows > 0) {
    while ($row = $result->fetch_assoc()) {
        $redis->hMset($row['username'],
            array('id' => $row['id'], 'password' => $row['password']));
    }
} else {
    echo '0 rows returned';
}

$con->close();
```
