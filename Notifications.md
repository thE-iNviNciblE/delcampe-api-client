Notifications is the mean used by Delcampe to update you about your API actions.

For common website members, notifications are sent via email and through the Internal website's messaging system. For Delcampe's API users, notifications in XML format have been added. This format will allow users to interact with feedback. Those notifications are sent by a _simple http call_ on a URL of your choice (_feedback url_) with the xml in the _POST data_.

To set the URL of your choice, you have two possibilities :
  * If you want to set one URL for all your XML notifications, call [setDefaultNotificationUrl](setDefaultNotificationUrl.md)()
  * If you want to set a specific destination for each notification, call [addNotificationSetting](addNotificationSetting.md)()

After 5 unsuccessful xml notification sending on your feedback url, the xml notification will be sent on an email address. Call [setDefaultFailOverNotificationEmail](setDefaultFailOverNotificationEmail.md)() to set this email address.

For more security, you can add, at the end of your URL, a token value of your choice. If you do so, this token will be set in each XML notification you'll receive from Delcampe,  ensuring you that the notification is sent by Delcampe and no other one.
  * Example of URL with a token : `http://www.mysite.net/feedback_api.php?token=bob`
  * This token is set in the notifications you'll receive : `<Notification_Token>Bob</Notification_Token>`


In concrete terms, after a call of an API function, you will often receive a notification when your request is actually processed by Delcampe. For example, when you call addItemAuction(), your request will first be put in a queue. Later, when your request is processed, you will automatically receive a notification giving you more information.
  * The notifications sent by call on your server are in **XML format**
  * The notifications are **encoded in UTF-8**
  * The different notifications are recognized by their type
  * You will receive the notifications in POST under the keyname **delcampeNotification**
  * To **update a notification** to the last version, you have to disable the older one (by calling [changeNotificationStatus](changeNotificationStatus.md)) and set the new one (by calling [addNotificationSetting](addNotificationSetting.md)). Doing so, you will have the newest version set automatically.

### Code example (PHP) showing you how to handle XML notifications ###
To log the notification
```
$logfileName = './log/feedbackFromDelcampeApi' . date('Ymd') . '.log';

if (isset($_POST['delcampeNotification'])) {
  $dataWrite = $_POST['delcampeNotification'];
}    
       
$logFileHandler = fopen($logfileName, 'a');
chmod ($logFileHandler, 0666);
fwrite($logFileHandler, date('H:i:s') . ' | ' . $dataWrite . "\n");
fclose($logFileHandler);
```

To handle the XML notification as an object
```
if (isset($_POST['delcampeNotification'])) {
  $dataWrite = $_POST['delcampeNotification'];
  $parsedXml = simplexml_load_string($dataWrite);
}    
```

## List of XML Notifications types you could receive from Delcampe on your feedback URL ##

### Seller\_Item\_Add ###

  * When is it send ?
    * after a call of [addItemAuction](addItemAuction.md)(), when the request is processed
    * after a call of [addItemFixedPrice](addItemFixedPrice.md)(), when the request is processed
    * when a fixed price item with quantity > 1 is sold

  * The reception of this notification can be tested by calling [testNotification](testNotification.md)()

  * When a fixed price item with quantity > 1 is sold, a new item (with a new id\_item) is created, with Quantity = quantity - quantity sold. The new version of this notification includes the tag `<id_parent>`, giving you the id\_item of the initial item.

#### Example (old version) ####
```
<?xml version="1.0" encoding="UTF-8"?>
  <Delcampe_Notification>
    <Notification_Token>MyNotificationToken</Notification_Token>
    <Notification_Datetime>2010-06-15T15:19:21+02:00</Notification_Datetime>
    <Notification_Type>Seller_Item_Add</Notification_Type>
    <Notification_Data>
      <id_item>8594429382</id_item>
      <personal_reference>MyPersonalReference</personal_reference>
    </Notification_Data>
  </Delcampe_Notification>
```

#### Example (new version, with `<id_parent>`) ####
```
<?xml version="1.0" encoding="UTF-8"?>
  <Delcampe_Notification>
    <Notification_Token>MyNotificationToken</Notification_Token>
    <Notification_Datetime>2010-06-15T15:19:21+02:00</Notification_Datetime>
    <Notification_Type>Seller_Item_Add</Notification_Type>
    <Notification_Data>
      <id_item>8594429382</id_item>
      <personal_reference>MyPersonalReference</personal_reference>
      <id_parent>5624142948</id_parent>
    </Notification_Data>
  </Delcampe_Notification>
```


### Seller\_Item\_Add\_Error\_Image ###

  * When is it send ?
    * after a call of [addItemAuction](addItemAuction.md)(), when the request is processed and there was an error in the processing of all the images of the item
    * after a call of [addItemFixedPrice](addItemFixedPrice.md)(), when the request is processed and there was an error in the processing of all the images of the item

  * There can be an error in the processing of your images when, for example, the url of the image is not correct

  * This notification is only sent when there is an error on ALL the images of the item. This item will never be published. You will have to re-send this item with the correct images

  * If you send an item with 3 images, and there is an error on one or two images, you will not receive the notification because your item will be published on the website with the non-error image(s)

#### Example ####
```
<?xml version="1.0" encoding="UTF-8"?>
  <Delcampe_Notification>
    <Notification_Token>MyNotificationToken</Notification_Token>
    <Notification_Datetime>2010-06-15T15:19:21+02:00</Notification_Datetime>
    <Notification_Type>Seller_Item_Add_Error_Image</Notification_Type>
    <Notification_Data>
      <personal_reference>MyPersonalReference</personal_reference>
    </Notification_Data>
  </Delcampe_Notification>
```


### Seller\_Item\_Update ###

  * When is it sent ?
    * after a call of [updateItem](updateItem.md)(), when the request is processed

  * The reception of this notification can be tested by calling [testNotification](testNotification.md)()

#### Example ####
```
<?xml version="1.0" encoding="UTF-8"?>
  <Delcampe_Notification>
    <Notification_Token>MyNotificationToken</Notification_Token>
    <Notification_Datetime>2010-05-27T14:23:23+02:00</Notification_Datetime>
    <Notification_Type>Seller_Item_Update</Notification_Type>
    <Notification_Data>
      <id_item>6592512738</id_item>
      <personal_reference>MyPersonalReference</personal_reference>
    </Notification_Data>
  </Delcampe_Notification>
```



### Seller\_Item\_FirstBid ###

  * When is it sent ?
    * immediately when there is a first bid on an item

  * The reception of this notification can be tested by calling [testNotification](testNotification.md)()

#### Example ####
```
<?xml version="1.0" encoding="UTF-8"?>
  <Delcampe_Notification>
    <Notification_Token>MyNotificationToken</Notification_Token>
    <Notification_Datetime>2010-06-15T15:19:21+02:00</Notification_Datetime>
    <Notification_Type>Seller_Item_FirstBid</Notification_Type>
    <Notification_Data>
      <id_item>8494348510</id_item>
      <personal_reference>MyPersonalReference</personal_reference>
    </Notification_Data>
  </Delcampe_Notification>
```


### Seller\_Item\_Close\_Sold ###

  * When is it sent ?
    * when an item is sold on the website

  * The reception of this notification can be tested by calling [testNotification](testNotification.md)()

  * The fields `<url_to_item>` and `<url_to_rating>` are URL-encoded according to RFC 1738

#### Example ####
```
<?xml version="1.0" encoding="UTF-8"?>
  <Delcampe_Notification>
    <Notification_Token>MyNotificationToken</Notification_Token>
    <Notification_Datetime>2010-06-15T15:19:21+02:00</Notification_Datetime>
    <Notification_Type>Seller_Item_Close_Sold</Notification_Type>
    <Notification_Data>
      <seller_nickname>test_seller</seller_nickname>
      <id_item>55943975</id_item>
      <item_title>Title of the item</item_title>
      <best_bid>12.00</best_bid>
      <best_bid_currency>Eur</best_bid_currency>
      <qty>1</qty>
      <personal_reference>MyPersonalReference</personal_reference>
      <url_to_item>http%3A%2F%2Fwww.delcampe.net%2Fitem.php%3Flanguage%3DF%26id%3D96798976</url_to_item>
      <bids_qty>1</bids_qty>
      <visits_counter>2</visits_counter>
      <buyer_id>57252065</buyer_id>
      <buyer_nickname>test_buyer</buyer_nickname>
      <buyer_email>buyer@hotmail.com</buyer_email>
      <buyer_spoken_languages>French</buyer_spoken_languages>
      <buyer_language>French</buyer_language>
      <buyer_firstname>John</buyer_firstname>
      <buyer_surname>Doo</buyer_surname>
      <buyer_address>buyer street</buyer_address>
      <buyer_zipcode>6542</buyer_zipcode>
      <buyer_city>Paris</buyer_city>
      <buyer_state></buyer_state>
      <buyer_country>FR</buyer_country>
      <buyer_phone></buyer_phone>
      <buyer_rating_nbr>20</buyer_rating_nbr>
      <buyer_rating_percentage>98</buyer_rating_percentage>
      <url_to_rating>http%3A%2F%2Fwww.delcampe.net%2Fitem.php%3Flanguage%3DF%26id%3D96798976%23rating</url_to_rating>
    </Notification_Data>
  </Delcampe_Notification>
```


### Seller\_Item\_Close\_Unsold ###

  * When is it sent ?
    * when the end time of an unsold item is reached

  * The reception of this notification can be tested by calling [testNotification](testNotification.md)()

#### Example ####
```
<?xml version="1.0" encoding="UTF-8"?>
  <Delcampe_Notification>
    <Notification_Token>MyNotificationToken</Notification_Token>
    <Notification_Datetime>2010-06-15T15:19:21+02:00</Notification_Datetime>
    <Notification_Type>Seller_Item_Close_Unsold</Notification_Type>
    <Notification_Data>
      <id_item>5894326975</id_item>
      <personal_reference>MyPersonalReference</personal_reference>
    </Notification_Data>
  </Delcampe_Notification>
```


### Seller\_Item\_Close\_Manually ###

  * When is it sent ?
    * after a call of [closeItem](closeItem.md)()

  * The reception of this notification can be tested by calling [testNotification](testNotification.md)()

#### Example ####
```
<?xml version="1.0" encoding="UTF-8"?>
  <Delcampe_Notification>
    <Notification_Token>MyNotificationToken</Notification_Token>
    <Notification_Datetime>2010-06-15T15:19:21+02:00</Notification_Datetime>
    <Notification_Type>Seller_Item_Close_Manually</Notification_Type>
    <Notification_Data>
      <id_item>0094326254</id_item>
      <personal_reference>MyPersonalReference</personal_reference>
    </Notification_Data>
  </Delcampe_Notification>
```


### Seller\_Item\_Move ###

  * When is it sent ?
    * when a moderator moves one of your items from a category to another one

#### Example ####
```
<?xml version="1.0" encoding="UTF-8"?>
  <Delcampe_Notification>
    <Notification_Token>MyNotificationToken</Notification_Token>
    <Notification_Datetime>2010-06-15T15:19:21+02:00</Notification_Datetime>
    <Notification_Type>Seller_Item_Move</Notification_Type>
    <Notification_Data>
      <id_item>8594429382</id_item>
      <id_category_from>9</id_category_from>
      <id_category_to>45</id_category_to>
    </Notification_Data>
  </Delcampe_Notification>
```