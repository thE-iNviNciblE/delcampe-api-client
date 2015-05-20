To check if you have access to this function, call [getAuthorizedActions](getAuthorizedActions.md).

Call this function to add multiple fixed price items on Delcampe website at once.

You can place a maximum of 99 pictures for each item.

You can send a **maximum of 1000 items at once**.

The new items will be placed in a queue and processed later.

Note : There is no need to put the description, even with HTML tags, in a CDATA.

**Attention: there's no sandbox to make your tests**. The items you'll send will be seen by every Delcampe member.
We encourage you thus to send your Test items in small quantity and to immediately close them when your test is done.

### Call ###

  * syntax : addItemFixedPriceBulk(string token, object ItemFixedPriceParamBulk)

  * parameter 1 : _string_ : secret token
  * parameter 2 : _object_ ItemFixedPriceParamBulk  : containing several ItemFixedPriceParam objects

  * note : for parameter 2, php developers can use an array instead of an object. See [PHP code example](addItemFixedPriceBulk#Code_example_(PHP).md)

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
<SOAP-ENV:addItemFixedPriceBulk>
  <token xsi:type="xsd:string">9c71088fe39d71f1da0e6ee6fef308f8</token>
  <data xsi:type="ns1:ItemFixedPriceParamBulk">
    <data SOAP-ENC:arrayType="ns1:ItemFixedPriceParam[2]" xsi:type="ns1:ArrayOfItemFixedPriceParam">
      <item xsi:type="ns1:ItemFixedPriceParam">
        <id_country xsi:type="xsd:int">0</id_country>
        <id_category xsi:type="xsd:int">80</id_category>
        <title xsi:type="xsd:string">MyTitle</title>
        <subtitle xsi:nil="true"/>
        <personal_reference xsi:type="xsd:string">MyPersRef1</personal_reference>
        <description xsi:type="xsd:string">My description</description>
        <fixed_price xsi:type="xsd:float">1.2</fixed_price>
        <currency xsi:type="xsd:string">EUR</currency>
        <date_end xsi:nil="true"/>
        <duration xsi:nil="true"/>
        <prefered_end_day xsi:nil="true"/>
        <prefered_end_hour xsi:nil="true"/>
        <qty xsi:nil="true"/>
        <renew xsi:nil="true"/>
        <option_boldtitle xsi:type="xsd:boolean">false</option_boldtitle>
        <option_coloredborder xsi:type="xsd:boolean">true</option_coloredborder>
        <option_highlight xsi:type="xsd:boolean">false</option_highlight>
        <option_keepoptionsonrenewal xsi:type="xsd:boolean">false</option_keepoptionsonrenewal>
        <option_lastminutebidding xsi:type="xsd:boolean">false</option_lastminutebidding>
        <option_privatebidding xsi:type="xsd:boolean">false</option_privatebidding>
        <option_subtitle xsi:type="xsd:boolean">false</option_subtitle>
        <option_topcategory xsi:type="xsd:boolean">false</option_topcategory>
        <option_toplisting xsi:type="xsd:boolean">false</option_toplisting>
        <option_topmain xsi:type="xsd:boolean">false</option_topmain>
        <images SOAP-ENC:arrayType="xsd:string[2]" xsi:type="ns1:String[]">
        <item xsi:type="xsd:string">http://www.mypics.net/pictures/testPicsApi_1.jpg</item>
        <item xsi:type="xsd:string">http://www.mypics.net/pictures/testPicsApi_2.jpg</item>        
        <images SOAP-ENC:arrayType="xsd:string[2]" xsi:type="ns1:String[]">
          <item xsi:type="xsd:string">http://www.mypics.net/pictures/testPicsApi_1.jpg</item>
          <item xsi:type="xsd:string">http://www.mypics.net/pictures/testPicsApi_2.jpg</item>
        </images>
      </item>
      <item xsi:type="ns1:ItemFixedPriceParam">
        <id_country xsi:type="xsd:int">0</id_country>
        <id_category xsi:type="xsd:int">80</id_category>
        <title xsi:type="xsd:string">MyTitle</title>
        <subtitle xsi:nil="true"/>
        <personal_reference xsi:type="xsd:string">MyPersRef2</personal_reference>
        <description xsi:type="xsd:string">My description</description>
        <fixed_price xsi:type="xsd:float">1.2</fixed_price>
        <currency xsi:type="xsd:string">EUR</currency>
        <date_end xsi:nil="true"/>
        <duration xsi:nil="true"/>
        <prefered_end_day xsi:nil="true"/>
        <prefered_end_hour xsi:nil="true"/>
        <qty xsi:nil="true"/>
        <renew xsi:nil="true"/>
        <option_boldtitle xsi:type="xsd:boolean">false</option_boldtitle>
        <option_coloredborder xsi:type="xsd:boolean">true</option_coloredborder>
        <option_highlight xsi:type="xsd:boolean">false</option_highlight>
        <option_keepoptionsonrenewal xsi:type="xsd:boolean">false</option_keepoptionsonrenewal>
        <option_lastminutebidding xsi:type="xsd:boolean">false</option_lastminutebidding>
        <option_privatebidding xsi:type="xsd:boolean">false</option_privatebidding>
        <option_subtitle xsi:type="xsd:boolean">false</option_subtitle>
        <option_topcategory xsi:type="xsd:boolean">false</option_topcategory>
        <option_toplisting xsi:type="xsd:boolean">false</option_toplisting>
        <option_topmain xsi:type="xsd:boolean">false</option_topmain>
        <images SOAP-ENC:arrayType="xsd:string[2]" xsi:type="ns1:String[]">
          <item xsi:type="xsd:string">http://www.mypics.net/pictures/testPicsApi_1.jpg</item>
          <item xsi:type="xsd:string">http://www.mypics.net/pictures/testPicsApi_2.jpg</item>
        </images>
      </item>
    </data>
  </data>
</SOAP-ENV:addItemFixedPriceBulk>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response ###

  * ResponseSimpleBulk, giving you more information on the function call result

  * SOAP envelope
```
<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
<SOAP-ENV:addItemFixedPriceBulkResponse>
  <addItemFixedPriceBulkReturn xsi:type="ns1:ResponseSimpleBulk">
  <data SOAP-ENC:arrayType="ns1:ResponseSimple[2]" xsi:type="ns1:ArrayOfResponseSimple">
    <item xsi:type="ns1:ResponseSimple">
      <status xsi:type="xsd:boolean">true</status>
      <errorMsg xsi:nil="true"/>
      <data xsi:type="xsd:string">Your request was taken into account!</data>
      <personal_reference xsi:type="xsd:string">MyPersRef1</personal_reference>
    </item>
    <item xsi:type="ns1:ResponseSimple">
      <status xsi:type="xsd:boolean">true</status>
      <errorMsg xsi:nil="true"/>
      <data xsi:type="xsd:string">Your request was taken into account!</data>
      <personal_reference xsi:type="xsd:string">MyPersRef2</personal_reference>
    </item>
    </data>
  <status xsi:type="xsd:boolean">true</status>
  <errorMsg xsi:nil="true"/>
  <personal_reference xsi:nil="true"/>
  </addItemFixedPriceBulkReturn>
</SOAP-ENV:addItemFixedPriceBulkResponse>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Notification ###
  * [Seller\_Item\_Add](Notifications#Seller_Item_Add.md)

### Code example (PHP) ###
```
for ($i = 0; $i < 100; $i++) {
  // MANDATORY DATA
  $data['id_country']                  = 0;
  $data['id_category']                 = 80;
  $data['fixed_price']                 = '0.01';
  $data['currency']                    = 'EUR';
  $data['title']                       = 'My title';
  $data['personal_reference']          = 'My personal ref';

  //OPTIONAL DATA
  $data['price_reserve']               = '5.00';
  $data['date_end']                    = '2010-07-01 10:00:00';
  $data['duration']                    = 10;
  $data['description']                 = 'My description';
  $data['renew']                       = 2;
  $data['option_lastminutebidding']    = true;
  $data['option_privatebidding']       = false;
  $data['option_subtitle']             = true;
  $data['subtitle']                    = 'My subtitle';
  $data['option_boldtitle']            = true;
  $data['option_highlight']            = false;
  $data['option_coloredborder']        = true;
  $data['option_toplisting']           = false;
  $data['option_topcategory']          = false;
  $data['option_topmain']              = false;
  $data['option_keepoptionsonrenewal'] = true;
  $data['prefered_end_day']            = 'mon';
  $data['prefered_end_hour']           = '15:00';

  //OPTIONAL IMAGES
  $data['images']                      = array('http://www.mypictures.com/pic1.jpg',
                                               'http://www.mypictures.com/pic2.jpg',
	                                       'http://www.mypictures.com/pic3.jpg'
                                              );

  $dataBulk['data'][] = $data; //Updated syntax !
}

//FUNCTION CALL
ini_set('default_socket_timeout', '100'); //to avoid timeout problems

$objSoapClient = new SoapClient('http://api.delcampe.net/soap.php?wsdl');
$return = $objSoapClient->authenticateUser('MyPersonalApiKey');

if ($return->status === true) {
  $return = $objSoapClient->addItemFixedPriceBulk($return->data, $dataBulk);

    if (false === $return->status) {
        //Insert KO 
        if (!is_null($return->data)) {    
            //To list items in error, based on the personal reference of each item
            foreach ($return->data as $data) {
                if (false === $data->status) {
                    var_export($data->errorMsg . ' for Item :' . $data->persRef, 1);
                }                    
            }
        } else {
            //General error (not authorized to call this method, too much items to insert, ...)
            var_export($return->errorMsg, 1);
        }     
    } else {
        //Insert OK
        var_export($return->data[0]->data, 1);
    }
}
```