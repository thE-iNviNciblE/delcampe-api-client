To check if you have access to this function, call [getAuthorizedActions](getAuthorizedActions.md).

Call this function to set a default email address to wich all email notifications will be send.

For more information about Delcampe's notifications, see [Notifications](Notifications.md).

### Call ###

  * syntax : setDefaultNotificationEmail(string token, string destination)

  * parameter 1 : _string_ : secret token
  * parameter 2 : _string_ : valid email address on wich email notifications will be send

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
<SOAP-ENV:setDefaultNotificationEmail>
  <token xsi:type="xsd:string">e44f2e4bf91b4b2b5d7784c57f6475a7</token>
  <destination xsi:type="xsd:string">my.email@gmail.com</destination>
</SOAP-ENV:setDefaultNotificationEmail>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response ###

  * ResponseSimple, giving you more information on the function call result

  * SOAP envelope
```
<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
<SOAP-ENV:setDefaultNotificationEmailResponse>
  <setDefaultNotificationEmailReturn xsi:type="ns1:ResponseSimple">
    <status xsi:type="xsd:boolean">true</status>
    <errorMsg xsi:nil="true"/>
    <data xsi:type="xsd:string">Your default notification email has been saved!</data>
    <personal_reference xsi:nil="true"/>
  </setDefaultNotificationEmailReturn>
</SOAP-ENV:setDefaultNotificationEmailResponse>
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
  $return = $objSoapClient->setDefaultNotificationEmail($return->data, 'john.doo@mysite.com');

  if (return->status === true) {
    var_export($return->data, 1);
  } else {
    var_export($return->errorMsg, 1);
  } 
}
```