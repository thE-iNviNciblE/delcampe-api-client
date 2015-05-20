To check if you have access to this function, call [getAuthorizedActions](getAuthorizedActions.md).

Call this function to set a default URL on wich all xml notifications will be send.

For more informations about Delcampe's notifications, see [Notifications](Notifications.md).

### Call ###

  * syntax : setDefaultNotificationUrl(string token, string destination)

  * parameter 1 : _string_ : secret token
  * parameter 2 : _string_ : valid url on wich xml notifications will be send

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
<SOAP-ENV:setDefaultNotificationUrl>
  <token xsi:type="xsd:string">6f842a455ac77fd1fc176794ae43a972</token>
  <destination xsi:type="xsd:string">http://www.mysite.net/feedback_api.php?token=bob</destination>
</SOAP-ENV:setDefaultNotificationUrl>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response ###

  * ResponseSimple, giving you more information on the function call result

  * SOAP envelope
```
<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
<SOAP-ENV:setDefaultNotificationUrlResponse>
  <setDefaultNotificationUrlReturn xsi:type="ns1:ResponseSimple">
    <status xsi:type="xsd:boolean">true</status>
    <errorMsg xsi:nil="true"/>
    <data xsi:type="xsd:string">Your default notification url has been saved!</data>
    <personal_reference xsi:nil="true"/>
  </setDefaultNotificationUrlReturn>
</SOAP-ENV:setDefaultNotificationUrlResponse>
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
  $return = $objSoapClient->setDefaultNotificationUrl($return->data, 'http://www.mysite.net/feedback_api.php?token=bob');

  if ($return->status === true) {
    var_export($return->data, 1);
  } else {
    var_export($return->errorMsg, 1);
  } 
}
```