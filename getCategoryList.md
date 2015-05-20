Call this function to get the list of Delcampe's categories you can set in [addItemAuction](addItemAuction.md)() or [addItemFixedPrice](addItemFixedPrice.md)().

### Call ###

  * syntax : getCategoryList(string token, string language, integer parentCategoryID, integer showOnlyLeaves)

  * parameter 1 : _string_ : secret token
  * parameter 2 : _character_ : Optional parameter. The language in which you want the categories to appear. Default value : 'E'. You can specify one of the following values :
    * 'E' : english
    * 'F' : français
    * 'I' : italiano
    * 'S' : español
    * 'G' : german
    * 'N' : nederlands
  * parameter 3 : _integer_ : Optional parameter. The parent category ID. If you don't specify a parent category ID, it returns all Delcampe's parent categories tree.
  * parameter 4 : _integer_ : Optional parameter. Default value : 0. Possible values : 0 or 1. If set to 1, this function returns only the categories in wich you can post items (leaves-categories, without child category under it). If set to 0, it returns all the parent categories.

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
<SOAP-ENV:getCategoryList>
   <token xsi:type="xsd:string">677558862ece442dfbe81b295441f72b</token>
   <lang xsi:type="xsd:string">E</lang>
   <idParent xsi:type="xsd:int">0</idParent>
</SOAP-ENV:getCategoryList>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response ###

  * ResponseCategory, giving you a list of Delcampe's categories (regarding parent ID set)

  * SOAP envelope
```
<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
<SOAP-ENV:getCategoryListResponse>
  <getCategoryListReturn xsi:type="ns1:ResponseCategory">
  <data SOAP-ENC:arrayType="ns1:Category[8]" xsi:type="ns1:ArrayOfCategory">
    <item xsi:type="ns1:Category">
      <id xsi:type="xsd:int">-8</id>
      <id_site xsi:type="xsd:int">8</id_site>
      <name xsi:type="xsd:string"> Old Paper</name>
      <id_parent xsi:type="xsd:int">0</id_parent>
      <child xsi:type="xsd:boolean">true</child>
      <selectable xsi:type="xsd:boolean">true</selectable>
    </item>
    <item xsi:type="ns1:Category">
      <id xsi:type="xsd:int">-7</id>
      <id_site xsi:type="xsd:int">7</id_site>
      <name xsi:type="xsd:string"> Badges</name>
      <id_parent xsi:type="xsd:int">0</id_parent>
      <child xsi:type="xsd:boolean">true</child>
      <selectable xsi:type="xsd:boolean">true</selectable>
    </item>
    <item xsi:type="ns1:Category">
      <id xsi:type="xsd:int">-6</id>
      <id_site xsi:type="xsd:int">6</id_site>
      <name xsi:type="xsd:string"> Phonecards</name>
      <id_parent xsi:type="xsd:int">0</id_parent>
      <child xsi:type="xsd:boolean">true</child>
      <selectable xsi:type="xsd:boolean">true</selectable>
    </item>
    <item xsi:type="ns1:Category">
      <id xsi:type="xsd:int">-5</id>
      <id_site xsi:type="xsd:int">5</id_site>
      <name xsi:type="xsd:string">Other collections</name>
      <id_parent xsi:type="xsd:int">0</id_parent>
      <child xsi:type="xsd:boolean">true</child>
      <selectable xsi:type="xsd:boolean">true</selectable>
    </item>
    <item xsi:type="ns1:Category">
      <id xsi:type="xsd:int">-4</id>
      <id_site xsi:type="xsd:int">4</id_site>
      <name xsi:type="xsd:string"> Books, Magazines, Comics</name>
      <id_parent xsi:type="xsd:int">0</id_parent>
      <child xsi:type="xsd:boolean">true</child>
      <selectable xsi:type="xsd:boolean">true</selectable>
    </item>
    <item xsi:type="ns1:Category">
      <id xsi:type="xsd:int">-3</id>
      <id_site xsi:type="xsd:int">3</id_site>
      <name xsi:type="xsd:string"> Coins & Banknotes</name>
      <id_parent xsi:type="xsd:int">0</id_parent>
      <child xsi:type="xsd:boolean">true</child>
      <selectable xsi:type="xsd:boolean">true</selectable>
    </item>
    <item xsi:type="ns1:Category">
      <id xsi:type="xsd:int">-2</id>
      <id_site xsi:type="xsd:int">2</id_site>
      <name xsi:type="xsd:string"> Postcards</name>
      <id_parent xsi:type="xsd:int">0</id_parent>
      <child xsi:type="xsd:boolean">true</child>
      <selectable xsi:type="xsd:boolean">true</selectable>
    </item>
    <item xsi:type="ns1:Category">
      <id xsi:type="xsd:int">-1</id>
      <id_site xsi:type="xsd:int">1</id_site>
      <name xsi:type="xsd:string"> Stamps</name>
      <id_parent xsi:type="xsd:int">0</id_parent>
      <child xsi:type="xsd:boolean">true</child>
      <selectable xsi:type="xsd:boolean">true</selectable>
    </item>
  </data>
  <status xsi:type="xsd:boolean">true</status>
  <errorMsg xsi:nil="true"/>
  <personal_reference xsi:nil="true"/>
  </getCategoryListReturn>
</SOAP-ENV:getCategoryListResponse>
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
  $return = $objSoapClient->getCategoryList($return->data, 'E', 0);

  if ($return->status === true) {
    foreach ($return->data as $objCategory) {     
      var_export($objCategory->name, 1);
    }
  } else {
    var_export($return->errorMsg, 1);
  } 
}
```

### Notes ###
You can use the following links to get ready-to-use printable lists:
  * [ALL Categories](http://www.delcampe.net/categories_print.php?language=E&site=0)
  * [Stamps Categories](http://www.delcampe.net/categories_print.php?language=E&site=1)
  * [Postcards Categories](http://www.delcampe.net/categories_print.php?language=E&site=2)
  * [Coins Categories](http://www.delcampe.net/categories_print.php?language=E&site=3)
  * [Books Categories](http://www.delcampe.net/categories_print.php?language=E&site=4)
  * [Other Collections Categories](http://www.delcampe.net/categories_print.php?language=E&site=5)
  * [Phonecards Categories](http://www.delcampe.net/categories_print.php?language=E&site=6)
  * [Pins Categories](http://www.delcampe.net/categories_print.php?language=E&site=7)
  * [Old Paper Categories](http://www.delcampe.net/categories_print.php?language=E&site=8)