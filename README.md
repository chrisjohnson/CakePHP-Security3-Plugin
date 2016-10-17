# Security3 - CakePHP 3.x Security Utility for 2.x

## Why

I wanted a cakey-way to do encryption/decryption on my cake 2.x app, using OpenSSL. Cake 2.x has a Security library which is nice but uses mcrypt, which is now deprecated. I didn't find any other openssl wrappers that I liked for cake

Cake 3.x's Security library makes use of the newer and simpler openssl functions, and is written without any real external dependencies. So I figured I would copy it, rewrite it slightly to fit into Cake 2.x more easily (which is not very namespace friendly), and use it directly

## Requirements

 * mbstring extension
 * openssl extension

## Usage

In bootstrap.php:

```
CakePlugin::load('Security3');
App::uses('Security3', 'Security3.Lib');
```

In `Config/core.php`:

```
Configure::write('Security.salt', 'some very long and varied salt value');
```

In your code:

```
// Assuming key is stored somewhere it can be re-used for
// decryption later.
$key = 'wt1U5MACWJFTXGenFoZoiLwQGrLgdbHA';

$cipher = Security3::encrypt($value, $key);

...

$result = Security3::decrypt($cipher, $key);
```

## More Help

This is just the Security Utility from 3.x so [their documentation](http://book.cakephp.org/3.0/en/core-libraries/security.html) should be accurate
