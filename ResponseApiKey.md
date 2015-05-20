  * ResponseApiKey is an object, returned by [getApiKey](getApiKey.md) function, with 4 datafields :
    * **status** : _boolean_ : true (if call ok) or false (if call not ok)
    * **errorMsg** : _string_ : message giving you more information on the function call failure
    * **apiKey** : _string_ : the api key you asked
    * **accepted** : _boolean_ : tells you if the user accepted to give you access on his account (true) or not (false).

  * If **status** is _true_
    * If **accepted** is _true_
      * **apiKey** will be filled with relevant information
      * **errorMsg** will be empty
    * If **accepted** is _false_
      * **apiKey** will be empty
      * **errorMsg** will be empty
  * If **status** is _false_
    * **data** will be empty
    * **errorMsg** will be filled with relevant information