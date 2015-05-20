To check if you have access to this function, call [getAuthorizedActions](getAuthorizedActions.md).

Call this function to get your notifications settings.

For more information about Delcampe's notifications, see [Notifications](Notifications.md).

### Call ###

  * syntax : getNotificationSettings(string token)

  * parameter 1 : _string_ : secret token

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
<SOAP-ENV:getNotificationSettings>
  <token xsi:type="xsd:string">62a7bd57f6c94345fb5ef35b170aac9c</token>
</SOAP-ENV:getNotificationSettings>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response ###

  * ResponseNotificationSetting, giving you a list of your notifications settings

  * SOAP envelope
```
<SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
<SOAP-ENV:getNotificationSettingsResponse>
  <getNotificationSettingsReturn xsi:type="ns1:ResponseNotificationSetting">
    <data SOAP-ENC:arrayType="ns1:NotificationSetting[2]" xsi:type="ns1:ArrayOfNotificationSetting">
      <item xsi:type="ns1:NotificationSetting">
        <id_notification xsi:type="xsd:int">69</id_notification>
        <id_user xsi:type="xsd:int">252064</id_user>
        <channel xsi:type="xsd:string">Email</channel>
        <type xsi:type="xsd:string">Default</type>
        <destination xsi:type="xsd:string">info@mymail.com</destination>
        <active xsi:type="xsd:boolean">true</active>
      </item>
      <item xsi:type="ns1:NotificationSetting">
        <id_notification xsi:type="xsd:int">70</id_notification>
        <id_user xsi:type="xsd:int">252064</id_user>
        <channel xsi:type="xsd:string">Curl</channel>
        <type xsi:type="xsd:string">Default</type>
        <destination xsi:type="xsd:string">http://www.delcampe.net/feedback_get.php</destination>
        <active xsi:type="xsd:boolean">true</active>
      </item>
    </data>
    <status xsi:type="xsd:boolean">true</status>
    <errorMsg xsi:nil="true"/>
    <personal_reference xsi:nil="true"/>
  </getNotificationSettingsReturn>
</SOAP-ENV:getNotificationSettingsResponse>
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
  $return = $objSoapClient->getNotificationSettings($return->data);

  if ($return->status === true) {
    foreach ($return->data as $objNotificationSetting) {     
      var_dump($objNotificationSetting);
    }
  } else {
    var_export($return->errorMsg, 1);
  } 
}
```