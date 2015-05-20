To check if you have access to this function, call [getAuthorizedActions](getAuthorizedActions.md).

Call this function to get an access key, used only for third-party applications  : see ServiceAuthenticationProcess for more details.

### Call ###

  * syntax : getAccessKey(string token, object WantedActions, string callbackUrl)

  * parameter 1 : _string_ : secret token
  * parameter 2 : _object_ WantedActions : contains the API functions you want to have access on the member account
  * parameter 3 : _string_ :

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
<SOAP-ENV:getAccessKey>
  <token xsi:type="xsd:string">c7826778389069fe13845b085f1ac141</token>
  <wantedActions xsi:type="ns1:WantedActions">
    <data SOAP-ENC:arrayType="ns1:String[25]" xsi:type="ns1:ArrayOfString">
      <item xsi:type="ns1:String">
        <data xsi:type="xsd:string">addItemAuction</data>
      </item>
      <item xsi:type="ns1:String">
	<data xsi:type="xsd:string">closeItem</data>
      </item>
      <item xsi:type="ns1:String">
	<data xsi:type="xsd:string">getCategoryList</data>
      </item>
      <item xsi:type="ns1:String">
	<data xsi:type="xsd:string">getItemInfo</data>
      </item>
      <item xsi:type="ns1:String">
	<data xsi:type="xsd:string">getMyOpenItemAuctionList</data>
      </item>
      <item xsi:type="ns1:String">
	<data xsi:type="xsd:string">getMySoldItemAuctionList</data>
      </item>
    </data>
  </wantedActions>
  <callbackUrl xsi:type="xsd:string">http://www.thirdpartysite.com</callbackUrl>
</SOAP-ENV:getAccessKey>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response ###

  * ResponseAccessKey, giving you the wanted data

  * SOAP envelope

```
<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
<SOAP-ENV:getAccessKeyResponse>
  <getAccessKeyReturn xsi:type="ns1:ResponseAccessKey">
    <status xsi:type="xsd:boolean">true</status>
    <errorMsg xsi:nil="true"/>
    <accessKey xsi:type="xsd:string">e1dd99ffe20eaba41c08dd29780532ac</accessKey>
    <acceptanceUrl xsi:type="xsd:string">http://www.delcampe.net/status.php?page=accounts_external_validation&language=F&accessKey=e1dd99ffe20eaba41c08dd29780532ac</acceptanceUrl>
  </getAccessKeyReturn>
</SOAP-ENV:getAccessKeyResponse>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Notification ###
  * None

### Code example (PHP) ###
```
$objWantedAction1->data = 'addItemAuction';
$objWantedAction2->data = 'closeItem';
$objWantedAction3->data = 'getCategoryList';
$objWantedAction4->data = 'getItemInfo';
$objWantedAction5->data = 'getMyOpenItemAuctionList';
$objWantedAction6->data = 'getMySoldItemAuctionList';

$objWantedActions->data = array($objWantedAction1, $objWantedAction2, $objWantedAction3, $objWantedAction4, $objWantedAction5, $objWantedAction6);

//FUNCTION CALL
$objSoapClient = new SoapClient('http://api.delcampe.net/soap.php?wsdl');
$return = $objSoapClient->authenticateUser('MyPersonalApiKey');

if ($return->status === true) {
  $return = $objSoapClient->getAccessKey($return->data, $objWantedActions, 'http://www.thirdpartysite.com');

  if ($return->status === true) {
    var_export('Acceptance URL : ' . $return->acceptanceUrl, 1);
  } else {
    var_export($return->errorMsg, 1);
  } 
}
```