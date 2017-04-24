## PHP 

## Save Credentials using HTACCESS
### in the HTACCESS file, set envs with
```
SetEnv NAME value
```
omit "" and ''

### To get the value in a script use 
```php
<?php

    $x = getenv('NAME');
?>
```

## Save Credentials in an INI file above webroot
1. Create a folder above webroot (configexample)
2. Create a file called something.ini
Add This into the ini file
```ini
[application]
username = exampleUsername
password = exmaplePassword
```

3. Access the ini vars in a script
```php
$ini = parse_ini_file($_SERVER['DOCUMENT_ROOT'] . '/../configexample/something.ini');
$un = $ini['username'];  
$pw = $ini['password'];  
```

## Change Default Include Directory for Assets
```php
//Set Server Directory - Set Home Path for Resources
ini_set("include_path",'/home/username/sitename.com/foldername/Assets/');
```
Then you can access includes from a different directory by default like this
```php
include("scripts/mpdf/mpdf.php");
```
where this file is in sitename.com/foldername/Assets/scripts/mpdf/mpdf.php