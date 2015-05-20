Call this function to get the ID of the seller linked to the given token


### Call ###

  * syntax : getMySellerId(string token)

  * parameter : _string_ : secret token

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
<SOAP-ENV:getMySellerId>
  <token xsi:type="xsd:string">529ba90354737ff6e08f610768db4648</token>
</SOAP-ENV:getMySellerId>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response ###

  * ResponseSimple, giving you the ID of the seller linked to the token

  * SOAP envelope
```
<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
<SOAP-ENV:getMySellerIdResponse>
  <getMySellerIdReturn xsi:type="ns1:ResponseSimple">
    <status xsi:type="xsd:boolean">true</status>
    <errorMsg xsi:nil="true"/>
    <data xsi:type="xsd:string">2820642</data>
    <personal_reference xsi:nil="true"/>
  </getMySellerIdReturn>
</SOAP-ENV:getMySellerIdResponse>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Notification ###
  * None

### Code example (PHP) ###//FUNCTION CALL
$objSoapClient = new SoapClient('http://api.delcampe.net/soap.php?wsdl');

$return = $objSoapClient->authenticateUser('MyPersonalApiKey');

if ($return->status === true) {
  $return = $objSoapClient->getMySellerId($return->data)

  if ($return->status === true) {
    var_export($return->data, 1);
  } else {
    var_export($return->errorMsg, 1);
  }
} 
}}}}```