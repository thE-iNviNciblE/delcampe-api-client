To check if you have access to this function, call [getAuthorizedActions](getAuthorizedActions.md).

Call this function to set a failover email address. This address will be used after
5 unsuccessfull sending trials of your notifications (xml or email) on the set destination.

For more information about Delcampe's notifications, see [Notifications](Notifications.md).

### Call ###

  * syntax : setDefaultNotificationEmail(string token, string destination)

  * parameter 1 : _string_ : secret token
  * parameter 2 : _string_ : valid email address

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
<SOAP-ENV:setDefaultFailOverNotificationEmail>
  <token xsi:type="xsd:string">6c0081b1efb421713e040a21f117c086</token>
  <destination xsi:type="xsd:string">my.email@gmail.com</destination>
</SOAP-ENV:setDefaultFailOverNotificationEmail>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response ###

  * ResponseSimple, giving you more information on the function call result

  * SOAP envelope
```
<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
<SOAP-ENV:setDefaultFailOverNotificationEmailResponse>
  <setDefaultFailOverNotificationEmailReturn xsi:type="ns1:ResponseSimple">
    <status xsi:type="xsd:boolean">true</status>
    <errorMsg xsi:nil="true"/>
    <data xsi:type="xsd:string">
      Your default failover notification email has been saved!
    </data>
    <personal_reference xsi:nil="true"/>
  </setDefaultFailOverNotificationEmailReturn>
</SOAP-ENV:setDefaultFailOverNotificationEmailResponse>
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
  $return = $objSoapClient->setDefaultFailOverNotificationEmail($return->data, 'john.doo@mysite.com');

  if (return->status === true) {
    var_export($return->data, 1);
  } else {
    var_export($return->errorMsg, 1);
  } 
}
```