# PHP-Firebase-Notification-Class
 This is a simple and powerful php class to end firebase push notification from php curl. It will allow you to push cloud messaging through firebase in 3 different way.
 
1. Send to a single device id
2. Send to a multiple device ids
3. Send to a specific topic  subscribers

To initialize notification class and push builder class, include both files in your autoload file or at the top of the page you want to use this class

    <?php
      define("GOOGLE_FCM_API_KEY","AAAAtXpvsYU:APXXX");
      require_once(__DIR__ . '/ini/FCMService.php'); 
      require_once(__DIR__ . '/FCMPush.php');
      $firebase = new UjahPeter\Firebase(GOOGLE_FCM_API_KEY);
      $push = new Push();
    ?>

Sending a message to a single device id can be done like this.

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
    
Sending a message to a multiple user IDs can be done like this

    <?php
      $push->setNode("notification");
      $push->setTo(array("User-A", "User-B", "User-C"));
      $push->setTitle("I code it here");
      $push->setMessage("Will you like to join us?");
      $push->setIsBackground(false);
      $json = $push->get();
      $response = $firebase->send($json, "multiple");
      var_export($response);
    ?>
    
 Sending a message by topic IDs/name can be done like this

    <?php
      $push->setIsTopic(true);
      $push->setNode("notification");
      $push->setTo("/topics/sendUsersInfo");
      $push->setTitle("I code it here");
      $push->setMessage("Will you like to join us?");
      $push->setIsBackground(false);
      $json = $push->get();
      $response = $firebase->send($json);
      var_export($response);
    ?>

Setup for push builder 

   * @ $objectnode The send node [data or notification]
   * @ $to  This could be either string or an array of device ids
   * @ $title The title of the message you are sending
   * @ $message Message content
   * @ $body Attentional body content
   * @ $image Set an Image 
   * @ $data Payload
   * @ $is_topic  For sending message to topic TRUR OR FALS
   * @ $vibrate Allow vibration 1 | 0
   * @ $sound  Notification sound 
   * @ $icon  App icon
   * @ $priority set notification priority
   * @ $is_background play in background without showing message
