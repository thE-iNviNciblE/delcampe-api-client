To check if you have access to this function, call [getAuthorizedActions](getAuthorizedActions.md).

Call this function to set a feedback to one of your buyers.


### Call ###

  * syntax : setFeedback(string token, integer idItem, integer feedback, string comment)

  * parameter : _string_ : secret token
  * parameter : _integer_ : id of the item you want to rate the buyer
  * parameter : _integer_ : feedback you want to give to your buyer
  * comment : _string_ : comment you want to add to your feedback

  * example :
    * setFeedBack(yourToken, 123456789, 100, 'Your comment') : gives a feedback of 100 on the buyer of the item with id 123456789

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
<SOAP-ENV:setFeedback>
  <token xsi:type="xsd:string">7d4fd2d8cfe662f8486370159ed246b0</token>
  <id_item xsi:type="xsd:int">249604504</id_item>
  <ratingValue xsi:type="xsd:int">100</ratingValue>
  <comment xsi:type="xsd:string">My comment</comment>
</SOAP-ENV:setFeedback>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response ###

  * ResponseSimple

  * SOAP envelope
```
<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
<SOAP-ENV:setFeedbackResponse>
<setFeedbackReturn xsi:type="ns1:ResponseSimple">
  <status xsi:type="xsd:boolean">true</status>
  <errorMsg xsi:nil="true"/>
  <data xsi:type="xsd:string">Your request was taken into account!</data>
  <personal_reference xsi:nil="true"/>
</setFeedbackReturn>
</SOAP-ENV:setFeedbackResponse>
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
  $return = $objSoapClient->setFeedback($return->data, 249333034 , 100, 'My comment');
  if ($return->status === true) {
    echo "<pre>".print_r($return->data, true)."</pre>";
  } 
}
```