# Laravel RCE

Simple script to exploit Remote Command Execution (RCE) on Laravel <= 5.4.
To use this script, you must find out the APP_KEY of target.

## Proof of Concept
1. The cookie decryption process calls unserialize() function which can be used to PHP Object Injection.
2. PHP Object Injection can lead to Remote Command Execution, since there are vulnerable code in Laravel PendingBroadcast.php and Monolog
3. Generate PHP Object Injection serialized data and encrypt it using APP_KEY and then set laravel_session or XSRF-TOKEN to encrypted payload. (Some sites change laravel_session to others name)
4. Refresh the page and the command is executed.

To make it automatically, the exploit.py is created.

## Built With
* [PHPGGC](https://github.com/ambionics/phpggc)

About
--------------
Author : Ravi Dharmawan (ravdhr@gmail.com)
