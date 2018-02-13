## Encode Decode a Bangla/Unicode Text

```php
$message = "আমার নাম এমরান";
$message = str_replace("\r\n", "\n", $message);
$mb_hex = '';
for ($kb = 0; $kb < mb_strlen($message, 'UTF-8'); $kb++) {
    $c = mb_substr($message, $kb, 1, 'UTF-8');
    $o = unpack('N', mb_convert_encoding($c, 'UCS-4BE', 'UTF-8'));
    $mb_hex .= sprintf('%04X', $o[1]);
}
$mb_hex;
print($mb_hex);
```

```php
function hexToStr($hex){
    $string='';
    for ($i=0; $i < strlen($hex)-1; $i+=2){
        $string .= chr(hexdec($hex[$i].$hex[$i+1]));
    }
    return $string;
}
$s = '098609AE09BE09B0002009A809BE09AE0020098F09AE09B009BE09A8';
echo mb_convert_encoding(hexToStr($s), 'UTF-8', 'Unicode');
```
