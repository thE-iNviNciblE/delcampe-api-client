To check if you have access to this function, call [getAuthorizedActions](getAuthorizedActions.md).

Call this function to restart a closed item


### Call ###

  * syntax : restartItem(string token, integer idItem)

  * parameter 1 : _string_ : secret token
  * parameter 2 : _integer_ : id of the not sold item you want to restart

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
<SOAP-ENV:restartItem>
  <token xsi:type="xsd:string">12128f93649dc6c35cdea35f9b64809b</token>
  <id_item xsi:type="xsd:int">249603902</id_item>
</SOAP-ENV:restartItem>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response ###

  * ResponseSimple, giving you more information on the function call result

  * SOAP envelope
```
<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
<SOAP-ENV:restartItemResponse>
  <restartItemReturn xsi:type="ns1:ResponseSimple">
  <status xsi:type="xsd:boolean">true</status>
  <errorMsg xsi:nil="true"/>
  <data xsi:type="xsd:string">Your request was taken into account!</data>
  <personal_reference xsi:nil="true"/>
</restartItemReturn>
</SOAP-ENV:restartItemResponse>
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
  $return = $objSoapClient->restartItem($return->data, 249604504);

  if ($return->status === true) {
    $objItem = $return->data[0]
    var_export($objItem, 1);
  } else {
    var_export($return->errorMsg, 1);
  } 
}
```