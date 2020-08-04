## About this project
* Based on [Yubico's version for PEAR](https://github.com/Yubico/php-yubico/)
* Replaced PEAR with PHP Composer

The Yubico authentication PHP class provides an easy way to integrate the Yubikey into your existing PHP-based user authentication infrastructure. Installation is simple usiing Composer
##  Installation 

``` composer require shiji/php-yubico ```

## Dependency 
cURL module from PHP is required. 
You may check with:

```php -m | grep curl```

### Debian/Ununtu
```sudo apt-get install curl php-curl```

### Install from source
[Official Guide](https://www.php.net/manual/en/curl.installation.php)

### OSX
cURL and php_curl are included if you install PHP with Homebrew



## Example
```
<?php
 use Yubico\Auth;
 use Yubico\AuthException;
 
 $otp = "ccbbddeertkrctjkkcglfndnlihhnvekchkcctif";

 # Generate a new id+key from https://upgrade.yubico.com/getapikey
 $yubi = new Auth_Yubico('42', 'FOOBAR=');
 try{
    $yubi->verify($otp);
 } catch (AuthException $e){
    // Verification failed
    print $e->getMessage();
    // Return error message and 
    // Make sure the execution stops here
    return;
 }
 // Verification passed, continue

?>
```


## License
The project is licensed under a BSD license.  See the file COPYING for
exact wording.  For any copyright year range specified as YYYY-ZZZZ in
this package note that the range specifies every single year in that
closed interval.
