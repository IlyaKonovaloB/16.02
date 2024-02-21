# 16.02
if(isset($_SESSION['name'])) {
        $userphone = $_SESSION['phone'];
        $useremail = $_SESSION['email'];
    }

    // } else {
    //     header("location: login.php");
    // }

    if(isset($_POST['send'])) {
        if(isset($_POST['check']) && $_POST['check'] == 'Yes') {
            if(!empty($_POST['phone']) && !empty($_POST['email']) && !empty($_POST['animal']) && !empty($_POST['animal_photo']) && !empty($_POST['message']) && !empty($_POST['adress']) && !empty($_POST['date'])){
                if(filter_var($_POST['email'], FILTER_VALIDATE_EMAIL)) {
                    $useremail = $_POST['email'];
                    $userphone = $_POST['phone'];
                    $animal_type = $_POST['animal'];
                    $animal_photo = $_POST['animal_photo'];
                    $message = $_POST['message'];
                    $stamp = $_POST['stamp'];
                    $adress = $_POST['adress'];
                    $date = $_POST['date'];
                    $mysqli->query("INSERT INTO animal_register (user_email, anima_type, animal_stamp, animal_adress, animal_date, animal_desc, animal_photo) 
                                     VALUES ('$useremail', '$animal_type', '$stamp', '$adress', '$date', '$message', '$animal_photo')");
                    header ("location: profile.php");
                } $error_message = "Формат почты неверный";
            } else {
                $error_message = "Не все поля заполненны";
            }
        } echo $error_message = "Примите согласие на обработку персональных данных";
    } 


    $mysqli->close();
