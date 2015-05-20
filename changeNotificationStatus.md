To check if you have access to this function, call [getAuthorizedActions](getAuthorizedActions.md).

Call this function to change the status (on/off) of a specific notification. Calling this function switches the status of the notification from _on_ to _off_ or from _off_ to _on_, depending on the current status. You will no longerreceive the specified notification if it is set to _off_.

For more informations about Delcampe's notifications, see [Notifications](Notifications.md).

### Call ###

  * syntax : changeNotificationStatus(string token, integer notificationID)

  * parameter 1 : _string_ : secret token
  * parameter 2 : _integer_ : id of the notification you want to change. Call [getNotificationSettings](getNotificationSettings.md) to get the IDs of your notifications

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
<SOAP-ENV:changeNotificationStatus>
  <token xsi:type="xsd:string">95aca436325f4afe45442968973321e7</token>
  <idNotification xsi:type="xsd:int">79</idNotification>
</SOAP-ENV:changeNotificationStatus>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response ###

  * ResponseSimple, giving you more information on the function call result

  * SOAP envelope
```
<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
<SOAP-ENV:changeNotificationStatusResponse>
  <changeNotificationStatusReturn xsi:type="ns1:ResponseSimple">
    <status xsi:type="xsd:boolean">true</status>
    <errorMsg xsi:nil="true"/>
    <data xsi:type="xsd:string">The status of the notification is now: Active</data>
    <personal_reference xsi:nil="true"/>
  </changeNotificationStatusReturn>
</SOAP-ENV:changeNotificationStatusResponse>
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
  $return = $objSoapClient->changeNotificationStatus($return->data, 12);

  if ($return->status === true) {
    var_export($return->data, 1);
  } else {
    var_export($return->errorMsg, 1);
  } 
}
```