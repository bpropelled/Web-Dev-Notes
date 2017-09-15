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

## Use PHP to redirect to a different page
```php
header("Location: http://example.com/myOtherPage.php");
die();
```

## Remove empty elements from an array
```php
$array = ['apples', '', 'oranges'];
$array = array_filter($array);
// returns ['apples','oranges']
```

## Get Current Quarter Number
```php

    function CurrentQuarter(){
         $n = date('n');
         if($n < 4){
              return "1";
         } elseif($n > 3 && $n <7){
              return "2";
         } elseif($n >6 && $n < 10){
              return "3";
         } elseif($n >9){
              return "4";
         }
    }
    
    $what_is_the_qtr = CurrentQuarter();

echo $what_is_the_qtr;
```

## Redirect a User if IP does not meet credentials
```php
// -> use a proper ip $myip = "192.168.100.1"; <-
$myip = "::1";
//The above is used for local host
$location = "http://google.com";

if($_SERVER['REMOTE_ADDR'] != $myip)
    {
    header("Location: $location");
    }
else
    {
    echo ' ok go';
    }

```


## When to use Self Vs This

Use $this to refer to the current object. Use self to refer to the current class. In other words, use  $this->member for non-static members, use self::$member for static members.  But is is prefered to use static:: instead of self:: to refer to iteslf in a class
