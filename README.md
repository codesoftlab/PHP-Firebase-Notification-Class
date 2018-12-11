# PHP-Firebase-Notification-Class
Send push notification from php curl 

Initialze notification class and push builder
<?php
  define("GOOGLE_FCM_API_KEY","AAAAtXpvsYU:APXXX");
  require_once(__DIR__ . '/ini/FCMService.php'); 
  require_once(__DIR__ . '/FCMPush.php');
  $firebase = new UjahPeter\Firebase(GOOGLE_FCM_API_KEY);
  $push = new Push();
?>

Sending a message to a single user can be done like this
<?php
  $push->setNode("notification");
  $push->setTo("f-bbVq2uCgY:APA91bF0s7jk5lXXy");
  $push->setTitle("I code it here");
  $push->setMessage("Will you like to join us?");
  $push->setBody("Will you like to join us here?");
  $push->setImage("url-path-to-image/log.png");
  $push->setIsBackground(false);
  $json = $push->get();
  $response = $firebase->send($json);
  var_export($response);
 ?>
