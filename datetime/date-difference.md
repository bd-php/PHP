### PHP Date Difference Calculation
```php
<?php

// MySQL Year-Days-Month
$assigned = '2015-15-12'; 

// Swaping Days and Months
$array = explode('-', $assigned);
$tmp = $array[1];
$array[1] = $array[2];
$array[2] = $tmp;
unset($tmp);
$assigned = implode('-', $array);

$assigned = new DateTime($assigned);
$now = new DateTime(date('Y-m-d'));
$interval = $assigned->diff($now); 

$interval = $interval->format('%Y years, %m months, %d days');
echo $interval;
?>
```
