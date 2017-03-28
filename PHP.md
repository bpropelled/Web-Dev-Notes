## PHP 

### SQL Inection Prevention
#### Mysqli
Using mysqli

The MySQL Improved extension handles bound parameters.

```php
$stmt = $db->prepare('update people set name = ? where id = ?');
$stmt->bind_param('si',$name,$id);
$stmt->execute();
```

Using the PDO layer

Here's the long way to do bind parameters.
```php
$dbh = new PDO('mysql:dbname=testdb;host=127.0.0.1', $user, $password);
$stmt = $dbh->prepare('INSERT INTO REGISTRY (name, value) VALUES (:name, :value)');
$stmt->bindParam(':name', $name);
$stmt->bindParam(':value', $value);

// insert one row
$name = 'one';
$value = 1;
$stmt->execute();
```
And a shorter way to pass things in.
```php
$dbh = new PDO('mysql:dbname=testdb;host=127.0.0.1', $user, $password);
$stmt = $dbh->prepare('UPDATE people SET name = :new_name WHERE id = :id');
$stmt->execute( array('new_name' => $name, 'id' => $id) );
Here's a great tutorial on migrating to PDO for MySQL developers.Using the PDO layer
```
