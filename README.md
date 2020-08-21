# PHPMySqlConnection
 Easy control of mysql database
 
 
[Visit my website](http://www.abolfazlalz.ir/)
 
**Abolfazl Alizadeh**

# Documentation
## Simple connection
### Run a simple query
 ```PHP
 use MySqlConnection\Connection;
 use MySqlConnection\Server;
 
 $server = new Server(HOST_NAME, DB_USERNAME, DB_PASSWORD);
 $con = new Connection($server, DB_NAME);
 $result = $con->run_query("INSERT INTO `table_name` (col1, col2, col3) VALUES (val1, val2, val3)");
 echo 'is success: ' . $result;
 ```
 The result of code
 ```
 is success: true
 ```
 ### Run a simple query
 ```PHP
 use MySqlConnection\Connection;
 use MySqlConnection\Server;
 
 $server = new Server(HOST_NAME, DB_USERNAME, DB_PASSWORD);
 $con = new Connection($server, DB_NAME);
 $values = $con->run_select_query("SELECT * FROM `table_name`");
 var_dump($values);
 ```
 The result of code:
 ```
 [
  1: {
   col1: val1,
   col2: val2,
   col3: val3
  }
 ]
 ```
 ## Query Creator
 for creating a query we can use [QueryCreator](/QueryCreator.php) class
 ### Create Insert Query:
 ```PHP
 use MySqlConnection\QueryCreator;
 //make a list of values for adding to table
 $data = ['name' => 'Abolfazl', 'lastname' => 'Alizadeh']
 //the table we want to add the data
 $tbl_name = "users";
 $queryResult = QueryCreator::insert_query($tbl_name, $data)
 echo $queryResult;
 ```
 The result of code:
 ```MySql
 INSERT INTO `users` (`name`, `lastname`) VALUES ('Abolfazl', 'Alizadeh');
 ```
 ### Create Update Query:
 ```PHP
 use MySqlConnection\Connection;
 //make a list for set new values:
 $data = ['name' => 'Armin'];
 //set condition for update query:
 $condition = ['id' = 2];
 //the table we want to update data where id equals by 2
 $tbl_name = "users";
 $queryResult = QueryCreator::update_query($tbl_name, $data, $condition);
 echo $queryResult;
 ```
 The result of code:
 ```MySql
 UPDATE users SET `name`='Armin' WHERE `id`=2
 ```
 ### Create Delete Query:
 ```PHP
 use MySqlConnection\Connection;
 //set condition for delete:
 $condition = ['id' = 2];
 //the data we want to delete at id = 2
 $tbl_name = "users";
 $queryResult = QueryCreator::delete_query($tbl_name, $condition);
 echo $queryResult;
 ```
 The result of code:
 ```MySql
 DELETE FROM users WHERE id=2
 ```
