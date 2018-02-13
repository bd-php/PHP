## Access password or session protected pages using PHP CURL

In our previous articles, we explained how to use data mining using CURL.
In data mining, you will encounter an instance when you can't mine the data
because it is protected by a password and/or a session. We will incorporate
what we have learned from the previous articles to mine data protected by a password or a session.

First, we need to know how sessions work. After entering a user-name and a password,
the server checks the validity of the user-name and password. If the information is valid,
the server then starts the session. During session start, a random value is generated 
which is sent via a cookie to the browser. 
The browser then sends this value back each time you visit the site page.

The following example demonstrates the process:

```php
<?php
$curl=curl_init();
curl_setopt($curl, CURLOPT_RETURNTRANSFER, true);
curl_setopt($curl, CURLOPT_URL, 'http://example.com/path_to_login_action');
curl_setopt($curl, CURLOPT_CUSTOMREQUEST, "POST");
curl_setopt($curl, CURLOPT_POSTFIELDS, array('name'=>'sonu', 'password'=>'password'));
curl_setopt($curl, CURLOPT_COOKIEJAR, dirname(__FILE__).'/cookie.txt');
curl_exec($curl);
curl_close($curl);
$curl=curl_init();
curl_setopt($curl, CURLOPT_RETURNTRANSFER, true);
 
curl_setopt($curl, CURLOPT_URL, 'http://example.com/path_of_protected_page');
curl_setopt($curl, CURLOPT_CUSTOMREQUEST, "GET");
curl_setopt($curl, CURLOPT_COOKIEFILE, dirname(__FILE__).'/cookie.txt');
 
echo curl_exec($curl);
curl_close($curl);
```

We have used init and close twice in the example above.
This is required because the cookie data will be stored only at the closing of the handler.

Be sure that the page you want to access is on the same domain as the login page.
Cookies are only allowed in the same domain, cookies follow the Same-origin policy.
