  * ResponseNotificationSetting is an object, returned by getNotificationSettings function, with 4 datafields :
    * **status** : _boolean_ : true (if call ok) or false (if call not ok)
    * **errorMsg** : _string_ : message giving you more information on the function call failure
    * **data** : _array_ of [NotificationSetting](NotificationSetting.md) objects
    * **personal\_reference** : _string_ : always empty

  * If **status** is _true_
    * **data** will be filled with relevant information
    * **errorMsg** will be empty
  * If **status** is _false_
    * **data** will be empty
    * **errorMsg** will be filled with relevant information