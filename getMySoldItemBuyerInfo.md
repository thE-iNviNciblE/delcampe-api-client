To check if you have access to this function, call [getAuthorizedActions](getAuthorizedActions.md).

Call this function to get the data of one of your buyers.


### Call ###

  * syntax : getMySoldItemBuyerInfo(string token, integer idItem)

  * parameter : _string_ : secret token
  * parameter : _int_ : id of the item you want buyer's infos

  * example :
    * getMySoldItemBuyerInfo(yourToken, 123456789) : returns the buyer's data for item 123456789

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
<SOAP-ENV:getMySoldItemBuyerInfo>
  <token xsi:type="xsd:string">d9b28fbc5c3a24bf6ee7bee6f6f11090</token>
  <id_item xsi:type="xsd:int">110981143</id_item>
</SOAP-ENV:getMySoldItemBuyerInfo>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response ###

  * ResponseBuyer, giving you buyer's data

  * SOAP envelope
```
<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
<SOAP-ENV:getMySoldItemBuyerInfoResponse>
  <getMySoldItemBuyerInfoReturn xsi:type="ns1:ResponseBuyer">
  <data xsi:type="ns1:Buyer">
    <buyer_id xsi:type="xsd:int">445523</buyer_id>
	<buyer_nickname xsi:type="xsd:string">Test_member</buyer_nickname>
	<buyer_email xsi:type="xsd:string">member@test.com</buyer_email>
	<buyer_spoken_languages xsi:type="xsd:string"/>
	<buyer_language xsi:type="xsd:string">French</buyer_language>
	<buyer_firstname xsi:type="xsd:string">Delcampe</buyer_firstname>
	<buyer_surname xsi:type="xsd:string">Team</buyer_surname>
	<buyer_address xsi:type="xsd:string">Sesame street</buyer_address>
	<buyer_zipcode xsi:type="xsd:string">5554</buyer_zipcode>
	<buyer_city xsi:type="xsd:string">Paris</buyer_city>
	<buyer_country xsi:type="xsd:string">FR</buyer_country>
	<buyer_phone xsi:type="xsd:string">02/555.22.67</buyer_phone>
	<buyer_rating_nbr xsi:type="xsd:int">192</buyer_rating_nbr>
	<buyer_rating_percentage xsi:type="xsd:float">92</buyer_rating_percentage>
  </data>
  <status xsi:type="xsd:boolean">true</status>
  <errorMsg xsi:nil="true"/>
  <personal_reference xsi:nil="true"/>
  </getMySoldItemBuyerInfoReturn>
</SOAP-ENV:getMySoldItemBuyerInfoResponse>
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
  $return = $objSoapClient->getMySoldItemBuyerInfo($return->data, 249706669);

  if ($return->status === true) {
    echo "<pre>".print_r($return->data, true)."</pre>";
  } 
}
```