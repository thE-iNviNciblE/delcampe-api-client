To check if you have access to this function, call [getAuthorizedActions](getAuthorizedActions.md).

Call this function to get the list of unsold closed fixed price items

If you want, you can pass, after your token, two more parameters. Those 2 parameters will be used, on our side, in a `LIMIT x,y` SQL statement. The third optional parameter is used to change the order of the returned items.

### Call ###

  * syntax : getMyClosedUnsoldItemAuctionList(string token)

  * parameter : _string_ : secret token
  * parameter : _int_ : (optional) the starting item you want to be returned
  * parameter : _int_ : (optional) the number of items you want to be returned
  * parameter : _string_ : (optional) 'ASC' : returns the items in ascending order; 'DESC' : returns the items in descending order

  * examples :
    * getMyClosedUnsoldItemFixedPriceList(yourToken, 0, 100) : returns the first 100 items.
    * getMyClosedUnsoldItemFixedPriceList(yourToken, 100, 500) : returns 500 items, beginning at the hundredth item.

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
<SOAP-ENV:getMyClosedUnsoldItemFixedPriceList>
  <token xsi:type="xsd:string">9bcb6aa4c9c623807f24525fc7680430</token>
  <startingItem xsi:type="xsd:int">0</startingItem>
  <numberOfItems xsi:type="xsd:int">2</numberOfItems>
</SOAP-ENV:getMyClosedUnsoldItemFixedPriceList>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response ###

  * ResponseItem, giving you a list of unsold closed fixed price items

  * SOAP envelope
```
<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
<SOAP-ENV:getMyClosedUnsoldItemFixedPriceListResponse>
  <getMyClosedUnsoldItemFixedPriceListReturn xsi:type="ns1:ResponseItem">
  <data SOAP-ENC:arrayType="ns1:Item[2]" xsi:type="ns1:ArrayOfItem">
    <item xsi:type="ns1:Item">
      <id_item xsi:type="xsd:int">91828478</id_item>
      <id_country xsi:type="xsd:int">0</id_country>
      <id_category xsi:type="xsd:int">80</id_category>
      <title xsi:type="xsd:string">My title</title>
      <subtitle xsi:type="xsd:string">My subtitle</subtitle>
      <personal_reference xsi:type="xsd:string">PersRef</personal_reference>
      <description xsi:type="xsd:string">MyDesc</description>
      <price_starting xsi:nil="true"/>
      <fixed_price xsi:type="xsd:float">11</fixed_price>
      <price_present xsi:nil="true"/>
      <price_increment xsi:nil="true"/>
      <currency xsi:type="xsd:string">EUR</currency>
      <date_end xsi:type="xsd:string">2010-08-12 16:22:39</date_end>
      <duration xsi:type="xsd:int">10</duration>
      <prefered_end_day xsi:nil="true"/>
      <prefered_end_hour xsi:nil="true"/>
      <qty xsi:type="xsd:int">1</qty>
      <renew xsi:type="xsd:int">0</renew>
      <option_boldtitle xsi:type="xsd:boolean">false</option_boldtitle>
      <option_coloredborder xsi:type="xsd:boolean">false</option_coloredborder>
      <option_highlight xsi:type="xsd:boolean">false</option_highlight>
      <option_keepoptionsonrenewal xsi:type="xsd:boolean">false</option_keepoptionsonrenewal>
      <option_lastminutebidding xsi:type="xsd:boolean">false</option_lastminutebidding>
      <option_privatebidding xsi:type="xsd:boolean">false</option_privatebidding>
      <option_subtitle xsi:type="xsd:boolean">true</option_subtitle>
      <option_topcategory xsi:type="xsd:boolean">false</option_topcategory>
      <option_toplisting xsi:type="xsd:boolean">false</option_toplisting>
      <option_topmain xsi:type="xsd:boolean">false</option_topmain>    
    </item>
    <item xsi:type="ns1:Item">
      <id_item xsi:type="xsd:int">91828478</id_item>
      <id_country xsi:type="xsd:int">0</id_country>
      <id_category xsi:type="xsd:int">80</id_category>
      <title xsi:type="xsd:string">My title2</title>
      <subtitle xsi:type="xsd:string">My subtitle</subtitle>
      <personal_reference xsi:type="xsd:string">PersRef2</personal_reference>
      <description xsi:type="xsd:string">MyDesc2</description>
      <price_starting xsi:nil="true"/>
      <fixed_price xsi:type="xsd:float">11</fixed_price>
      <price_present xsi:nil="true"/>
      <price_increment xsi:nil="true"/>
      <currency xsi:type="xsd:string">EUR</currency>
      <date_end xsi:type="xsd:string">2010-08-12 16:22:39</date_end>
      <duration xsi:type="xsd:int">10</duration>
      <prefered_end_day xsi:nil="true"/>
      <prefered_end_hour xsi:nil="true"/>
      <qty xsi:type="xsd:int">1</qty>
      <renew xsi:type="xsd:int">0</renew>
      <option_boldtitle xsi:type="xsd:boolean">false</option_boldtitle>
      <option_coloredborder xsi:type="xsd:boolean">false</option_coloredborder>
      <option_highlight xsi:type="xsd:boolean">false</option_highlight>
      <option_keepoptionsonrenewal xsi:type="xsd:boolean">false</option_keepoptionsonrenewal>
      <option_lastminutebidding xsi:type="xsd:boolean">false</option_lastminutebidding>
      <option_privatebidding xsi:type="xsd:boolean">false</option_privatebidding>
      <option_subtitle xsi:type="xsd:boolean">true</option_subtitle>
      <option_topcategory xsi:type="xsd:boolean">false</option_topcategory>
      <option_toplisting xsi:type="xsd:boolean">false</option_toplisting>
      <option_topmain xsi:type="xsd:boolean">false</option_topmain>    
    </item>      
  </data>
  <status xsi:type="xsd:boolean">true</status>
  <errorMsg xsi:nil="true"/>
  <personal_reference xsi:nil="true"/>
  </getMyClosedUnsoldItemFixedPriceListReturn>
</SOAP-ENV:getMyClosedUnsoldItemFixedPriceListResponse>
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
  $return = $objSoapClient->getMyClosedUnsoldItemFixedPriceList($return->data);

  if ($return->status === true) {
    foreach ($return->data as $objItem) {     
      var_export($objItem->id_item, 1);
    }
  } else {
    var_export($return->errorMsg, 1);
  } 
}
```

### Notes ###
Use [getItemInfo()](getItemInfo.md) to get data for each returned ID.