To check if you have access to this function, call [getAuthorizedActions](getAuthorizedActions.md).

Call this function to update an existing item.
If you update the images of an item, all existing images of this item will be lost and replaced by the new ones.


### Call ###

  * syntax : updateItem(string token, integer idItem, array data)

  * parameter 1 : _string_ : secret token
  * parameter 2 : _int_    : id of the item you want to update
  * parameter 3 : _array_  : containing the data you want to update

  * SOAP envelope
```
<?xml version="1.0" encoding="UTF-8"?> 
<SOAP-ENV:Envelope 
    xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" 
    xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
    xmlns:ns1="http://xml.apache.org/xml-soap" 
    xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/" 
    SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
<SOAP-ENV:updateItem>
    <token xsi:type="xsd:string">c94e7a65294996ad3915cefe7bfb0540</token>
    <id_item xsi:type="xsd:int">99696430</id_item>
    <arrData xsi:type="ns1:Map">
    	<item>
            <key xsi:type="xsd:string">title</key>
	    <value xsi:type="xsd:string">My updated title</value>
	</item>
	<item>
            <key xsi:type="xsd:string">description</key>
	    <value xsi:type="xsd:string">My updated description</value>
	</item>
	<item>
	    <key xsi:type="xsd:string">personal_reference</key>
	    <value xsi:type="xsd:string">MyPersRef</value>
	</item>
        <item>
            <key xsi:type="xsd:string">option_topcategory</key>
            <value xsi:type="xsd:boolean">false</value>
        </item>
	<item>
	    <key xsi:type="xsd:string">images</key>
	    <value SOAP-ENC:arrayType="xsd:string[2]" xsi:type="SOAP-ENC:Array">
	        <item xsi:type="xsd:string">http://www.exemple.com/pictures/exemple_1.jpg</item>
	        <item xsi:type="xsd:string">http://www.exemple.com/pictures/exemple_2.jpg</item>
	    </value>
	</item>
	</arrData>
</SOAP-ENV:updateItem>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response ###

  * ResponseSimple, giving you more information on the function call result

  * SOAP envelope
```
<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
<SOAP-ENV:updateItemResponse>
  <updateItemReturn xsi:type="ns1:ResponseSimple">
    <status xsi:type="xsd:boolean">true</status>
    <errorMsg xsi:nil="true"/>
    <data xsi:type="xsd:string">Your request was taken into account!</data>
    <personal_reference xsi:nil="true"/>
  </updateItemReturn>
</SOAP-ENV:updateItemResponse>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Notification ###
  * [Seller\_Item\_Update](Notifications#Seller_Item_Update.md)

### Code example (PHP) ###
```
//DATA TO UPDATE
$data['personal_reference'] = 'MyPersRef';
$data['title']              = 'My updated title';
$data['description']        = 'My updated description'

//FUNCTION CALL
$objSoapClient = new SoapClient('http://api.delcampe.net/soap.php?wsdl');
$return = $objSoapClient->authenticateUser('MyPersonalApiKey');

if ($return->status === true) {
  $return = $objSoapClient->updateItem($return->data, 99999999 ,$data);

  if ($return->status === true) {
    var_export($return->data, 1);
  } else {
    var_export($return->errorMsg, 1);
  } 
}
```