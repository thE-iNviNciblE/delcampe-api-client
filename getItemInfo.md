To check if you have access to this function, call [getAuthorizedActions](getAuthorizedActions.md).

Call this function to get data on a specified item


### Call ###

  * syntax : getItemInfo(string token, integer idItem)

  * parameter 1 : _string_ : secret token
  * parameter 2 : _integer_ : id of the item

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
<SOAP-ENV:getItemInfo>
  <token xsi:type="xsd:string">0b829004b44c206d44b43f1976fcd667</token>
  <id_item xsi:type="xsd:int">99664630</id_item>
</SOAP-ENV:getItemInfo>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response ###

  * ResponseItem, giving you complete data of the specified item

  * SOAP envelope
```
<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
<SOAP-ENV:getItemInfoResponse>
  <getItemInfoReturn xsi:type="ns1:ResponseItem">
  <data SOAP-ENC:arrayType="ns1:Item[1]" xsi:type="ns1:ArrayOfItem">
    <item xsi:type="ns1:Item">
      <id_item xsi:type="xsd:int">99664630</id_item>
      <id_country xsi:type="xsd:int">0</id_country>
      <id_category xsi:type="xsd:int">80</id_category>
      <title xsi:type="xsd:string">API TEST</title>
      <subtitle xsi:type="xsd:string"/>
      <personal_reference xsi:type="xsd:string">MyPersRef</personal_reference>
      <description xsi:type="xsd:string"/>
      <price_starting xsi:type="xsd:float">10</price_starting>
      <fixed_price xsi:nil="true"/>
      <price_increment xsi:type="xsd:float">0.01</price_increment>
      <currency xsi:type="xsd:string">EUR</currency>
      <date_end xsi:type="xsd:string">2010-08-21 07:00:00</date_end>
      <duration xsi:type="xsd:int">7</duration>
      <prefered_end_day xsi:type="xsd:string">fri</prefered_end_day>
      <prefered_end_hour xsi:type="xsd:string">13:00</prefered_end_hour>
      <qty xsi:nil="true"/>
      <renew xsi:type="xsd:int">0</renew>
      <option_boldtitle xsi:type="xsd:boolean">false</option_boldtitle>
      <option_coloredborder xsi:type="xsd:boolean">false</option_coloredborder>
      <option_highlight xsi:type="xsd:boolean">false</option_highlight>
      <option_keepoptionsonrenewal xsi:type="xsd:boolean">false</option_keepoptionsonrenewal>
      <option_lastminutebidding xsi:type="xsd:boolean">false</option_lastminutebidding>
      <option_privatebidding xsi:type="xsd:boolean">false</option_privatebidding>
      <option_subtitle xsi:type="xsd:boolean">false</option_subtitle>
      <option_topcategory xsi:type="xsd:boolean">false</option_topcategory>
      <option_toplisting xsi:type="xsd:boolean">false</option_toplisting>
      <option_topmain xsi:type="xsd:boolean">false</option_topmain>
    </item>
  </data>
  <status xsi:type="xsd:boolean">true</status>
  <errorMsg xsi:nil="true"/>
  <personal_reference xsi:nil="true"/>
  </getItemInfoReturn>
</SOAP-ENV:getItemInfoResponse>
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
  $return = $objSoapClient->getItemInfo($return->data, 85846154);

  if ($return->status === true) {
    $objItem = $return->data[0]
    var_export($objItem, 1);
  } else {
    var_export($return->errorMsg, 1);
  } 
}
```