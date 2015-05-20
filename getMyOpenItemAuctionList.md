To check if you have access to this function, call [getAuthorizedActions](getAuthorizedActions.md).

Call this function to get the list of open auction items.

If you want, you can pass, after your token, two more parameters. Those 2 parameters will be used, on our side, in a `LIMIT x,y` SQL statement. The third optional parameter is used to change the order of the returned items.

### Call ###

  * syntax : getMyOpenItemAuctionList(string token, int startingItem, int numberOfItems)

  * parameter : _string_ : secret token
  * parameter : _int_ : (optional) the starting item you want to be returned
  * parameter : _int_ : (optional) the number of items you want to be returned
  * parameter : _string_ : (optional) 'ASC' : returns the items in ascending order; 'DESC' : returns the items in descending order

  * examples :
    * getMyOpenItemAuctionList(yourToken, 0, 100) : returns the first 100 items.
    * getMyOpenItemAuctionList(yourToken, 100, 500) : returns 500 items, beginning at the hundredth item.

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
<SOAP-ENV:getMyOpenItemAuctionList>
  <token xsi:type="xsd:string">4c8cd860773354e580926c7081bdac6f</token>
  <startingItem xsi:type="xsd:int">0</startingItem>
  <numberOfItems xsi:type="xsd:int">2</numberOfItems>
</SOAP-ENV:getMyOpenItemAuctionList>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response ###

  * ResponseItem, giving you a list of open auction items

  * SOAP envelope
```
<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
<SOAP-ENV:getMyOpenItemAuctionListResponse>
  <getMyOpenItemAuctionListReturn xsi:type="ns1:ResponseItem">
  <data SOAP-ENC:arrayType="ns1:Item[2]" xsi:type="ns1:ArrayOfItem">
    <item xsi:type="ns1:Item">
      <id_item xsi:type="xsd:int">101585435</id_item>
      <id_country xsi:type="xsd:int">0</id_country>
      <id_category xsi:type="xsd:int">80</id_category>
      <title xsi:type="xsd:string">ApiBulkImgObject</title>
      <subtitle xsi:type="xsd:string"/>
      <personal_reference xsi:type="xsd:string">MyPersonalRef</personal_reference>
      <description xsi:type="xsd:string">My description</description>
      <price_starting xsi:type="xsd:float">0.01</price_starting>
      <fixed_price xsi:nil="true"/>
      <price_present xsi:type="xsd:float">0.01</price_present>
      <price_increment xsi:type="xsd:float">0.01</price_increment>
      <currency xsi:type="xsd:string">EUR</currency>
      <date_end xsi:type="xsd:string">2010-09-07 20:25:00</date_end>
      <duration xsi:type="xsd:int">7</duration>
      <prefered_end_day xsi:nil="true"/>
      <prefered_end_hour xsi:nil="true"/>
      <qty xsi:nil="true"/>
      <renew xsi:type="xsd:int">0</renew>
      <bids xsi:type="xsd:int">0</bids>
      <option_boldtitle xsi:type="xsd:boolean">false</option_boldtitle>
      <option_coloredborder xsi:type="xsd:boolean">false</option_coloredborder>
      <option_highlight xsi:type="xsd:boolean">false</option_highlight>
      <option_keepoptionsonrenewal       xsi:type="xsd:boolean">false</option_keepoptionsonrenewal>
      <option_lastminutebidding xsi:type="xsd:boolean">false</option_lastminutebidding>
      <option_privatebidding xsi:type="xsd:boolean">false</option_privatebidding>
      <option_subtitle xsi:type="xsd:boolean">false</option_subtitle>
      <option_topcategory xsi:type="xsd:boolean">false</option_topcategory>
      <option_toplisting xsi:type="xsd:boolean">false</option_toplisting>
      <option_topmain xsi:type="xsd:boolean">false</option_topmain>    
    </item>
    <item xsi:type="ns1:Item">
      <id_item xsi:type="xsd:int">101585438</id_item>
      <id_country xsi:type="xsd:int">0</id_country>
      <id_category xsi:type="xsd:int">80</id_category>
      <title xsi:type="xsd:string">ApiBulkImgObject</title>
      <subtitle xsi:type="xsd:string"/>
      <personal_reference xsi:type="xsd:string">MyPErsRef</personal_reference>
      <description xsi:type="xsd:string">My description</description>
      <price_starting xsi:type="xsd:float">0.01</price_starting>
      <fixed_price xsi:nil="true"/>
      <price_present xsi:type="xsd:float">0.01</price_present>
      <price_increment xsi:type="xsd:float">0.01</price_increment>
      <currency xsi:type="xsd:string">EUR</currency>
      <date_end xsi:type="xsd:string">2010-09-07 20:25:00</date_end>
      <duration xsi:type="xsd:int">7</duration>
      <prefered_end_day xsi:nil="true"/>
      <prefered_end_hour xsi:nil="true"/>
      <qty xsi:nil="true"/>
      <renew xsi:type="xsd:int">0</renew>
      <bids xsi:type="xsd:int">1</bids>
      <option_boldtitle xsi:type="xsd:boolean">false</option_boldtitle>
      <option_coloredborder xsi:type="xsd:boolean">false</option_coloredborder>
      <option_highlight xsi:type="xsd:boolean">false</option_highlight>
      <option_keepoptionsonrenewal       xsi:type="xsd:boolean">false</option_keepoptionsonrenewal>
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
  </getMyOpenItemAuctionListReturn>
</SOAP-ENV:getMyOpenItemAuctionListResponse>
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
  $return = $objSoapClient->getMyOpenItemAuctionList($return->data);

  if ($return->status === true) {
    foreach ($return->data as $objItem) {     
      var_export($objItem->id_item, 1);
    }
  } else {
    var_export($return->errorMsg, 1);
  } 
}
```