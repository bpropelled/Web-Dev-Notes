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
``javascript
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

