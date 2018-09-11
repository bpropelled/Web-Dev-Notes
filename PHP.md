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

## Error Reporting
use this script to use error reporting in a simple tenary operator

```php

define('DEBUG', true);

error_reporting(E_ALL);
ini_set('display_errors', DEBUG ? 'On' : 'Off');

```

## Simple MySQL connection
### Make sure to use "mysqli_escape_string" to escape the user input!
```php
$con=mysqli_connect("enterURLhere*","databaseNameHere","passwordGoesHere","yourUsername");

/*Check connection*/
if (mysqli_connect_errno()){
  echo "Failed to connect to MySQL: " . mysqli_connect_error();
}

//Save Vars from $_GET['']
$name=mysqli_real_escape_string($con,$_GET["name"]);
$text=mysqli_real_escape_string($con,$_GET["text"]);
$time=substr(str_replace("+",":",str_replace("T"," ",date(DATE_ATOM))),0,18);

// Insert them into the DB
$sql="INSERT INTO chat (time, name, text)
  VALUES
  ('$time','$name','$text')";

  if (!mysqli_query($con,$sql)){
    die('Error: ' . mysqli_error($con));
  } else{

  echo "$name wrote '$text'";
}

mysqli_close($con);


// Get info from DB
$data = "SELECT * FROM databaseName ORDER BY Time ASC";
$result = mysqli_query($con, $data);

while($row = mysqli_fetch_array($result,MYSQLI_ASSOC)){

echo "

<div class="chatPost">

";
echo $row['Username'];
echo "

[";
$row['Time'] = substr($row['Time'], 11, strpos($row['Time'], ' '));
echo $row['Time'];
echo "]: 

";
echo "

";
echo $row['Content'];
echo "

</div>

";
}

mysqli_free_result($result);
mysqli_close($con);

```
### Reading the data with JS
```javascript
function updateChat() {
  $.get("read.php", function(data) {
    $("#chatOutput").html(data);
  });
}


    $("#chatSend").click(function(){

        /*Get User Input*/
        var text=$("#chatText").val();
        var username=$("#username").val();

          if(text!=undefined&&username!=undefined){

          /*Send Stuff*/
          var url = "write.php?username=" +
              decodeURI(username) +
              "&text=" +
              decodeURI(text));
          $.post(url);

        }

      });

  setTimeout(
    function() {updateChat();},
     1000);

  function updateChat() {
    $.get("read.php", function(data) {
      $("#chatOutput").html(data);
    });
  }

});
```

## Do I need a closing php tag "?>"
You don't need a closing PHP tag if you code is PHP only in the file

## Magic Constants
php offers a wide range of magic constants to use like '__DIR__'

In the PHP constants chapter we've learned how to define and use constants in PHP script.
PHP moreover also provide a set of special predefined constants that change depending on where they are used. These constants are called magic constants. For example, the value of __LINE__ depends on the line that it's used on in your script.
Magic constants begin with two underscores and end with two underscores. The following section describes some of the most useful magical PHP constants.

### Reference of Magic Constants

__LINE__
The __LINE__ constant returns the current line number of the file, like this:

__FILE__
The __FILE__ constant returns full path and name of the PHP file that's being executed. If used inside an include, the name of the included file is returned.

__DIR__
The __DIR__ constant returns the directory of the file. If used inside an include, the directory of the included file is returned. 

__FUNCTION__
The __FUNCTION__ constant returns the name of the current function.

__CLASS__
The __CLASS__ constant returns the name of the current class. Here's an example:

__METHOD__
The __METHOD__ constant returns the name of the current class method.

__NAMESPACE__
The __NAMESPACE__ constant returns the name of the current namespace.

[link to reference and exmaples]('https://www.tutorialrepublic.com/php-tutorial/php-magic-constants.php')

## Fire Up a PHP Server from the command line
```cmd
php -S localhost:8000
```

## Echo out the directory path of the current working directory
```php
echo getcwd();
//var/www/example.com/httpdocs
```

## Quickly show all PHP errors
The quickest way to display all php errors and warnings is to add these lines to your PHP code file:
```php
ini_set('display_errors', 1);
ini_set('display_startup_errors', 1);
error_reporting(E_ALL);
```

**What do these lines of code do exactly?**
The ini_set function will try to override the configuration found in your PHP ini file.

The display_errors and display_startup_errors are just two of the directives that are available. The display_errors directive will determine if the errors will be displayed or hidden to the user. Usually, the dispay_errors directive should be turned off after development.

The display_startup_errors, however, is a separate directive because the display_errors doesn’t handle the errors that will be encountered during PHP’s startup sequence. The list of the directives that can be overridden by the ini_set function is found in the official documentation.

Unfortunately, these two directives won’t be able to display parse errors such as missing semicolons or missing curly braces. In this case, the PHP ini configuration must be modified.

## Simple PHP try-catch example
Here is an example of a basic PHP try-catch statement.
```php
try {
    // run your code here
}
catch (exception $e) {
    //code to handle the exception
}
finally {
    //optional code that always runs
}
```
### PHP error handling keywords
The following keywords are used for PHP exception handling.

**Try:** The try block contains the code that may potentially throw an exception. All of the code within the try block is executed until an exception is potentially thrown.

**Throw:** The throw keyword is used to signal the occurrence of a PHP exception. The PHP runtime will then try to find a catch statement to handle the exception.

**Catch:** This block of code will be called only if an exception occurs within the try code block. The code within your catch statement must handle the exception that was thrown.

**Finally:** In PHP 5.5, the finally statement is introduced. The finally block may also be specified after or instead of catch blocks. Code within the finally block will always be executed after the try and catch blocks, regardless of whether an exception has been thrown, and before normal execution resumes. This is useful for scenarios like closing a database connection regardless if an exception occurred or not.

