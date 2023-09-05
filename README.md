# contact_form
<?php
$insert = false;
if(isset($_POST['name'])){
    
$server = "localhost";
$username = "root";
$password = "";

$con = mysqli_connect($server, $username, $password);

if(!$con){
    die("connection failed due to ".mysqli_connect_error());
}
//echo "Successfully connected"

$name = $_POST['name'];
$gender = $_POST['gender'];
$age = $_POST['age'];
$email = $_POST['email'];
$phone = $_POST['phone'];
$desc = $_POST['desc'];
$sql = "INSERT INTO `sub_form` . `sub` (`name`, `age`, `gender`, `email`, `phone`, `other`, `dt`)
 VALUES ('$name', '$age', '$gender', '$email', '$phone',
 '$desc', current_timestamp());";
 //echo $sql;

 if($con -> query($sql) == true){
    //echo "Details submitted successfully";
    $insert = true;
 }
 else{
    echo "ERROR: $sql <br> $con->error";
 }

 $con->close();

}

?>

<html lang="en">
<head>
    <link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Roboto&family=Sriracha&display=swap" rel="stylesheet">
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h1>Welcome</h1>
        <p>Enter your details</p>
        <?php
        if($insert == true)
        echo "<p class='submit'>Thanks for submitting your form has been submitted 
             successfully</p>"
        ?>
        <form action="index.php" method="post">
            <input type="text" name="name" id="name" placeholder="Enter your name">
            <input type="number" name="age" id="age" placeholder="Enter your age">
            <input type="text" name="gender" id="gender" placeholder="Enter your gender">
            <input type="email" name="email" id="email" placeholder="Enter your email">
            <input type="number" name="phone" id="phone" placeholder="Enter your phone number">
            <textarea name="desc" id="desc" cols="30" rows="10" placeholder="Enter description"></textarea>
            <button class="btn">Submit</button>
        </form>
    </div>
</body>
</html>
