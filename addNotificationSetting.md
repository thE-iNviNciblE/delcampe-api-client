To check if you have access to this function, call [getAuthorizedActions](getAuthorizedActions.md).

Call this function to add a new notification destination for a specific notification type.

  * Email notifications begins with 'Email'
  * XML notifications begins with 'Curl'

For more informations about Delcampe's notifications, see [Notifications](Notifications.md).

### Call ###

  * syntax : addNotificationSetting(string token, string type, string destination)

  * parameter 1 : _string_ : secret token
  * parameter 2 : _string_ : notification type. Call [getAvailableNotifications](getAvailableNotifications.md)() to get a list of notification types
  * parameter 3 : _string_ : destination where we have to send the notification

  * SOAP envelope
```
<SOAP-ENV:Envelope 
    xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'
    xmlns:xsd='http://www.w3.org/2001/XMLSchema'
    xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' 
    xmlns:ns1='http://xml.apache.org/xml-soap' 
    xmlns:SOAP-ENC='http://schemas.xmlsoap.org/soap/encoding/' 
    SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
<SOAP-ENV:Body>
<SOAP-ENV:addNotificationSetting>
  <token xsi:type="xsd:string">9bc7332dae767049d0a8d0153651bae3</token>
  <notificationType xsi:type="xsd:string">Curl_Seller_Item_Add</notificationType>
  <destination xsi:type="xsd:string">http://www.mysite.net/feedback_api.php?token=bob</destination>
</SOAP-ENV:addNotificationSetting>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response ###

  * ResponseSimple, giving you more information on the function call result

  * SOAP envelope
```
<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
<SOAP-ENV:addNotificationSettingResponse>
  <addNotificationSettingReturn xsi:type="ns1:ResponseSimple">
    <status xsi:type="xsd:boolean">true</status>
    <errorMsg xsi:nil="true"/>
    <data xsi:type="xsd:string">Your new notification setting has been saved!</data>
    <persRef xsi:nil="true"/>
  </addNotificationSettingReturn>
</SOAP-ENV:addNotificationSettingResponse>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Notification ###
  * None

### Code example (PHP) ###
```
//FUNCTION CALL
$objSoapClient = new SoapClient('http://api.delcampe.net/soap.php?wsdl');

$return = $objSoapClient->authenticateUser('MyPersonalApiKey');

if ($return->status === true) {
  $return = $objSoapClient->addNotificationSetting($return->data, 'Curl_Seller_Item_Add', 'http://www.mysite.net/feedback_api.php?token=bob');

  if (return->status === true) {
    var_export($return->data, 1);
  } else {
    var_export($return->errorMsg, 1);
  } 
}
```