# PHP
- PHP is an acronym for "PHP: Hypertext Preprocessor"
- server scripting language
  - interpreter excute source code without need to compiler
  - scripting language doesn't need compilation and is instead interpreted on line a time during runtime (so any change i make in web page i see it directly)
  - require a host
  - slower than compiler languages
  ## php files
  - can contain text,html,css,js and php code
  - PHP code is executed on the server, and the result is returned to the browser as plain HTML
  ## What Can PHP Do?
  - PHP can generate dynamic page content
  - PHP can create, open, read, write, delete, and close files on the server
  - PHP can collect form data
  - PHP can send and receive cookies
    cookies: count how many times user visit website 
             store information such as chopping cart contents
  - PHP can add, delete, modify data in your database
  - PHP can be used to control user-access
  - PHP can encrypt data
## php variables 
- there is no data type before name it know time by value you pass 
  - $txt="loma" //string
  - $n=5; // int 
  - $n=5.5 //double
   ```php
    $x="5"
    $y=15
    echo $x + $y //output 20
   ``` 
## Global and Local Scope
- A variable declared outside a function has a GLOBAL SCOPE and can only be accessed outside a function
- A variable declared within a function has a LOCAL SCOPE and can only be accessed within that function
## how to use global varaible inside function
- The global keyword is used to access a global variable from within a function.
```php
<?php
$x = 5;
$y = 10;

function myTest() {
  global $x, $y;
  $y = $x + $y;
}

myTest();
echo $y; // outputs 15
?>

```
- PHP also stores all global variables in an array called $GLOBALS[index]. The index holds the name of the variable. This array is also accessible from within functions and can be used to update global variables directly.
```php
<?php
$x = 5;
$y = 10;

function myTest() {
  $GLOBALS['y'] = $GLOBALS['x'] + $GLOBALS['y'];
}

myTest();
echo $y; // outputs 15
?>  
```
## static
- Normally, when a function is completed/executed, all of its variables are deleted. However, sometimes we want a local variable NOT to be deleted. We need it for a further job.
```php
<?php
function myTest() {
  static $x = 0;
  echo $x;
  $x++;
}

myTest();//0
myTest();//1
myTest();//2
?>
```
## diffrent between echo & print
- echo has no return value, can take multiple parameters, faster
- print has return value =1, can take only one parameter, slower
- there is an appreviation form to print
```php
<?php
echo "loma";
echo "<br>";
?>
<?="we love php short tag"; ?>
```
  
```php
echo "<h2>" . $txt1 . "</h2>";
echo "Study PHP at " . $txt2 . "<br>";

<?php
echo "<h2>PHP is Fun!</h2>";
echo "Hello world!<br>";
echo "I'm about to learn PHP!";
?>
// i can use print instead of echo
```
## var_dump
- return type and value 
```php
<?php
$x = 10.365;
var_dump($x);
?>
```
## array 
```php
$cars = array("Volvo","BMW","Toyota");
```
## PHP Casting Strings and Floats to Integers
- $int_cast = (int)$x;
## php constant
- it makes contant can be treated as language words(case insensitive)
- define(var_name,value,case) 
  - value may be array
```php
<?php
define("GREETING", "Welcome to W3Schools.com!", true);
echo greeting;
?>
```
## php operators
- <=> : - Spaceship	
        - $x <=> $y
        - Returns an integer less than, equal to, or greater than zero, depending on if $x is less than, equal to, or greater than $y.
- .:  - Concatenation
      - $txt1 . $txt2
      - Concatenation of $txt1 and $txt2
      - can be used as .= (connection assignment ans +=)
- ?? null coalescing (x is null or not)
## diffrent notes
- nan stands for not a number, it is used for impossible maths operations
## functions
- are not case sensitive
## strict requirement
- to pass int to int and string to string use key strict in the first of php line, that will give you an error if pass wrong
```php
<?php declare(strict_types=1); // strict requirement
// adding this line will force you to write type of all values
//The strict declaration forces things to be used in the intended way.

function addNumbers(int $a, int $b):int//return type 
{
  return $a + $b;
}
echo addNumbers(5, "5 days");
// since strict is enabled and "5 days" is not an integer, an error will be thrown
?>
```
## array
- count($cars);//return length of array
  ### Associative Arrays
  - same as maps in c++ 
  ```php
  $age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");
  echo $age['Peter'];
  ```
  - #### loop through it 
  ```php
  <?php
  $age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");

  foreach($age as $x => $x_value) {
    echo "Key=" . $x . ", Value=" . $x_value;
    echo "<br>";
  }
  ?>
  ```
  ### sorting
  - sort() - sort arrays in ascending order
  - rsort() - sort arrays in descending order
  - asort() - sort associative arrays in ascending order, according to the value
  - ksort() - sort associative arrays in ascending order, according to the key
  - arsort() - sort associative arrays in descending order, according to the value
  - krsort() - sort associative arrays in descending order, according to the key
# php superglobal
- built-in variables which can be used in all scopes
## PHP $GLOBALS
- it stores all global variables in an array called GLOBALS
- $GLOBALS[index] index: name of variable
```php
<?php
    $name = "loma";
    //global 
    function meral()
    {
      // local variables
      echo $GLOBALS['name'];
      // $age=21;  //error
      $GLOBALS['age'] = 21;

    }
    meral();
    echo $GLOBALS['age'];
    ?>
```
## PHP $_SERVER
- hold information about headers,baths and script locatons 
```php
<?php
echo $_SERVER['PHP_SELF'];//the same page you ara in 
echo "<br>";
echo $_SERVER['SERVER_NAME'];//ex:localhost
echo "<br>";
echo $_SERVER['HTTP_HOST'];
echo "<br>";
echo $_SERVER['HTTP_REFERER'];//where are you go from
echo "<br>";
echo $_SERVER['HTTP_USER_AGENT'];
echo "<br>";
echo $_SERVER['SCRIPT_NAME'];
echo "<br>";
echo $_SERVER['REQUEST_METHOD'];//post or get
echo "<br>";
echo $_SERVER['QUERY_STRING'];//return querey string (string after ?)
?>
```
## php request 
- collect data after submit
## php post 
- collect data after submit
- more secuire than get 
- it hide data
- has no limitation of data sent
## php get 
- use to select data after submit
- sent data to url
- limitation is about 2000 chars because of url
```php
//meral.php
<?php
    $users=["salma","nour","meral","menna","abeer","reda","sohaila"];
    if (filter_var($_POST['age'], FILTER_VALIDATE_INT) && in_array($_POST['name'], $users))
      echo "Welcome " . $_POST['name']."<br/>"."I LOve YoU <3";
    else
      echo "sorry ".$_POST['name'].", you can't see our page"."<br/>"."I HATE YoU \")";

?>
//loma.php
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="<?="UTF-8";?>">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title><?="My First PHP Page";?></title>
  </head>
  <body>
    <form method="post" action="meral.php";?>
      name: <input
      type="text"
      name="name"
      >
      <br/>
      passward:<input type="password" 
      name="password"
      >
      <br/>
      age:<input type="text"
      name="age";>
      <button>submit</button>
    </form>
    
    <div></div>
  </body>
</html>

```
## heredoc and now doc
- used to can write string with special chars in a very easy way
## error control operator
- i use it to prevent error from be show by user
- $b=@$a; //@ which prevent 
- or use die("write here any error message you want")
- die stop script from being worked, any thing you write after it will not be excuted
## diffrence between include and required
- include||recuire("filename.extintion");
- i use required when i have afile which my program can not run without it
## argument list 
- we use it if idon't know number of elements which i pass to function 
- func_get_args() is not prefered to be used always use ...$nums
- ...$nums must be the last thing you pass to function if it has multible params
- ... mean unpacking that split elemnts of array try : echo "...$nums"; to understand me
- 
```php
<?php
    // func_get_arg()
    // func_get_args()
    // func_num_args()
    
    // ...$nums works the same as func_get_args()
    function sum(...$nums)
    {
      $result=0;
      // foreach(func_get_args() as $args)
      // {
      //   $result += $args;
      // }
      // return $result;
      foreach($nums as $num)
      {
        $result += $num;
      }
      return $result;
       
    }
    echo sum(1, 2, 53);
?>
```
## array fill
- it is params are named params
- we use it to fill all array with the same value
```php
<?php
    $a=array_fill(value: 50, count: 100, start_index: 0);
    print_r($a);
    ?>
```
## function exist
- check if function is here or not
## anonymous function 
- function with no name
``` php
<?php
    $sum = function ($s1, $s2) {
      return ($s1 + $s2);
    };
    echo $sum(1,2);
    ?>
```
## to use global variable inside function
- use use
```php
<?php
    $num = 9;
    $sum = function ($s1, $s2) use($num) {
      return ($s1 + $s2+$num);
    };
    echo $sum(1,2);
    ?>
```
## to do specific task in array we use function (array_map)
```php
<?php
    $nums = [10,20,30,40];

  $add_five=fn($item) => $item+5;

    $array_after_add_five=array_map($add_five,$nums);
    print_r($array_after_add_five)
    ?>
```
## php filters
- validation = determine if data is in proper form
- sanitiing data = remove any illegal chars from data
- it is important for security 
- filter_var() 
  - we use it to validate and sentaize data
  - it takes to inputs 
               
                  1 - var you want to check
                  2 - type of check to use (validate || sanitaize)
                  3 - it can filter data in specific range 
## regular Expression 
- we use preg_match() to search for string in given string
- we use preg replace to replace string with another string
- we use function preg_match ()or preg_match_all()
- it has 3 parameters (/expr/, $var_you_search_inside,$array_you_return_data_inside) 
- we use i to be case_insentitive
- see that video [link](https://youtu.be/sa-TUpSx1JA)
![](./Screenshot%202023-01-14%20130333.jpg)
![](./s1.jpg)
## php form security
- Cross-site scripting (XSS) is a type of computer security vulnerability typically found in Web applications. XSS enables attackers to inject client-side script into Web pages viewed by other users.
## How To Avoid $_SERVER["PHP_SELF"] Exploits?
- $_SERVER["PHP_SELF"] exploits can be avoided by using the htmlspecialchars() function.
```php
<form method="post" action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]);?>">
```
- The htmlspecialchars() function converts special characters to HTML entities. Now if the user tries to exploit the PHP_SELF variable, it will result in the following output:
```php
<form method="post" action="test_form.php/&quot;&gt;&lt;script&gt;alert('hacked')&lt;/script&gt;">

```
- the exploit attempt fails, and no harm is done!
# Validate Form Data With PHP
- pass all variables through PHP's htmlspecialchars() function.
- We will also do two more things when the user submits the form:
  1 - Strip unnecessary characters (extra space, tab, newline) from the user input data (with the PHP trim() function)
  2 - Remove backslashes (\) from the user input data (with the PHP stripslashes() function)
  3 - create a function that will do all the checking for us (which is much more convenient than writing the same code over and over again).
  ```php
  function test_input($data) {
  $data = trim($data);
  $data = stripslashes($data);
  $data = htmlspecialchars($data);
  return $data;
  }
  ```

## htmlspecialchars() & form security
- we use it to convert java script to to text so that it will not be excuted 
- it prevent xss from being excuted 
- XSS enables attackers to inject client-side script into Web pages viewed by other users.

## date & time
- date(format,timestamp)
- date_default_timezone_set(): to set time to my timezone
- date('l') : to output today name
## require & include
- they are diffrent when error
  - require: produce fatal error and stop the script
  - include: produce warning and the script will continue
- Use require when the file is required by the application
- Use include when the file is not required and application should continue when file is not found.
## file open & close
- fopen(): open file take 2 paramters(as c++)
- fclose(): close file
- fgets(): read only one line from the file
```php
<?php
$myfile = fopen("webdictionary.txt", "r") or die("Unable to open file!");
echo fgets($myfile);
fclose($myfile);
?>
```
- After a call to the fgets() function, the file pointer has moved to the next line.
- feof(): check if i reach the end of file
- fgetc(): read single char
## fwrite
- with it you can write in file 
## explode
- split string by the string you pass and return array
```php
<?php
$str = "Hello world. It's a beautiful day.";
print_r (explode(".",$str)); //return array of three elements(Hello world,It's a beautiful day, )

?>
```
## upload file & picture
```php
<!DOCTYPE html>
//loma.php
<html lang="en">
  <head>
    <meta charset="<?="UTF-8";?>">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title><?="My First PHP Page";?></title>
  </head>
  <body>
    <form action="upload.php" method="POST" enctype="multipart/form-data"><!--enctype: define how data will be encoded when sent to sever-->
    <input type="file" name="file">
    <button type="submit" name="submit">upload</button>

    </form>
    
    
  </body>
</html>
//upload.php
<?php
if (isset($_POST['submit'])) {
    $file = $_FILES['file'];
    //print_r($file);// i made it to can know what file return
    $fileName = $file['name'];
    $fileFullPath = $file['full_path'];
    $fileType = $file['type'];
    $fileTEmpName = $file['tmp_name'];
    $fileError = $file['error'];
    $fileSize = $file['size'];

    $fileExt = explode(".", $fileName); //i want to take jpg from name of image(rooa.jpg);
    $fileActualExt = strtolower(end($fileExt));

    //size, ext allowed, error
    $allowedExt = array("jpg", "jpeg", "pdf", "png");
    if ($fileError === 0) {
        if (in_array($fileActualExt, $allowedExt)) {
            if ($fileSize < 100000) {
                $fileNewName = uniqid("", true) . $fileActualExt;
                $fileDistination = "uploads/" . $fileNewName;
                move_uploaded_file($fileTEmpName, $fileDistination);
                header("Location: loma.php?uploadsuccess");
            } else {
                echo "the size of your picture is too big";
            }
        } else {
            echo "this file extension is not allowed";
        }
    } else {
        echo "There is an error uploading that file";
    }
}

```
## connect two strings
- we connect them using .
- i can write time ans string like that: strtotime("+1 year") or using function time(): refer to currrent time +any time i want

## cookies
- store information in the user's computer
- it is created using set cookie()
- it is stored in array $_COOKIE[]
- setcookie() must be before html tag
- to modify cookie just set function setcookie again
- to delete it use time from the past
## session 
- store informaton in server and user's computer
- to start session use session_start():*it must be before html tag*
- session_unset(): remove data(session variables) but session is here
- session_destroy(): remove session 
- we must use unset before destroy
- i must start session to can destroy it 
## json
- encode convert code to string to can send to server
- decode convert string to array