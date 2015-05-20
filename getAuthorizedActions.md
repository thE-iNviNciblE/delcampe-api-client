Call this function to get a list of API functions you are authorized to call


### Call ###

  * syntax : getAuthorizedActions(string token)

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
<SOAP-ENV:getAuthorizedActions>
  <token xsi:type="xsd:string">1c7f17c10173b1209a0457113f0cc6ff</token>
</SOAP-ENV:getAuthorizedActions>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response ###

  * ResponseComplex, giving you a list of API functions you are authorized to call

  * SOAP envelope
```
<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
<SOAP-ENV:getAuthorizedActionsResponse>
  <getAuthorizedActionsReturn xsi:type="ns1:ResponseComplex">
  <data SOAP-ENC:arrayType="ns1:String[21]" xsi:type="ns1:ArrayOfString">
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">getNotificationSettings</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">addNotificationSetting</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">setDefaultNotificationUrl</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">setDefaultNotificationEmail</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">setDefaultFailOverNotificationEmail</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">changeNotificationStatus</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">getMyOpenItemAuctionList</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">getMySoldItemAuctionList</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">getMyClosedUnsoldItemAuctionList</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">getMyOpenItemFixedPriceList</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">getMySoldItemFixedPriceList</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">getMyClosedUnsoldItemFixedPriceList</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">getItemInfo</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">addItemAuction</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">addItemFixedPrice</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">closeItem</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">updateItem</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">closeItemPriority</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">getItemInfoByPersonalReference</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">addItemAuctionBulk</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">addItemFixedPriceBulk</data>
    </item>
  </data>
  <status xsi:type="xsd:boolean">true</status>
  <errorMsg xsi:nil="true"/>
  <personal_reference xsi:nil="true"/>
  </getAuthorizedActionsReturn>
</SOAP-ENV:getAuthorizedActionsResponse>
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
  $return = $objSoapClient->getAuthorizedActions($return->data);

  if ($return->status === true) {
    foreach ($return->data as $objValue) {     
      var_export($objValue->data, 1);
    }
  } else {
    var_export($return->errorMsg, 1);
  } 
}
```