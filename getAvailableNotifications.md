Call this function to get a list of available notifications.

For more informations about Delcampe's notifications, see [Notifications](Notifications.md).

### Call ###

  * syntax : getAvailableNotifications(string token)

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
<SOAP-ENV:getAvailableNotifications>
  <token xsi:type="xsd:string">1112f790632216429ad2d426bda67e30</token>
</SOAP-ENV:getAvailableNotifications>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response ###

  * ResponseComplex, giving you a list of available notifications

  * SOAP envelope
```
<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
<SOAP-ENV:getAvailableNotificationsResponse>
  <getAvailableNotificationsReturn xsi:type="ns1:ResponseComplex">
  <data SOAP-ENC:arrayType="ns1:String[13]" xsi:type="ns1:ArrayOfString">
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">Curl_Default</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">Curl_Seller_Item_Add</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">Curl_Seller_Item_Close_Manually</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">Curl_Seller_Item_Close_Sold</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">Curl_Seller_Item_Close_Unsold</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">Curl_Seller_Item_FirstBid</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">Curl_Seller_Item_Update</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">Email_Buyer_Item_Close_Unsold</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">Email_Default</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">Email_Error_LimitReached</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">Email_Seller_Item_Add</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">Email_Seller_Item_Close_Sold</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">Email_Seller_Item_Close_Unsold</data>
    </item>
  </data>
  <status xsi:type="xsd:boolean">true</status>
  <errorMsg xsi:nil="true"/>
  <personal_reference xsi:nil="true"/>
  </getAvailableNotificationsReturn>
</SOAP-ENV:getAvailableNotificationsResponse>
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
  $return = $objSoapClient->getAvailableNotifications($return->data);

  if ($return->status === true) {
    foreach ($return->data as $objValue) {     
      var_export($objValue->data, 1);
    }
  } else {
    var_export($return->errorMsg, 1);
  } 
}
```