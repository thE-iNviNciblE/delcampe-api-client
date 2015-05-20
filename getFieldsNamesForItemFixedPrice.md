Call this function to get a list of fields name you can use to handle a fixed price item


### Call ###

  * syntax : getFieldsNamesForItemFixedPrice()

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
<SOAP-ENV:getFieldsNamesForItemFixedPrice/>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response ###

  * ResponseComplex, giving you a list of fields name you can use to handle a fixed price item

  * SOAP envelope
```
<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
<SOAP-ENV:getFieldsNamesForItemFixedPriceResponse>
  <getFieldsNamesForItemFixedPriceReturn xsi:type="ns1:ResponseComplex">
  <data SOAP-ENC:arrayType="ns1:String[25]" xsi:type="ns1:ArrayOfString">
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">id_country</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">id_category</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">date_end</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">duration</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">fixed_price</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">currency</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">qty</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">title</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">description</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">personal_reference</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">images</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">renew</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">option_lastminutebidding</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">subtitle</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">option_privatebidding</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">option_subtitle</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">option_boldtitle</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">option_highlight</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">option_coloredborder</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">option_toplisting</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">option_topcategory</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">option_topmain</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">option_keepoptionsonrenewal</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">prefered_end_day</data>
    </item>
    <item xsi:type="ns1:String">
      <data xsi:type="xsd:string">prefered_end_hour</data>
    </item>
  </data>
  <status xsi:type="xsd:boolean">true</status>
  <errorMsg xsi:nil="true"/>
  <personal_reference xsi:nil="true"/>
  </getFieldsNamesForItemFixedPriceReturn>
</SOAP-ENV:getFieldsNamesForItemFixedPriceResponse>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Notification ###
  * None

### Code example (PHP) ###
```
//FUNCTION CALL
$objSoapClient = new SoapClient('http://api.delcampe.net/soap.php?wsdl');
$return = $objSoapClient->getFieldsNamesForItemFixedPrice();

if ($return->status === true) {
  foreach ($return->data as $objValue) {     
    var_export($objValue->data, 1);
  }
} else {
  var_export($return->errorMsg, 1);
}
```