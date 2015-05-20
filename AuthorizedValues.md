On this page, you'll find information on values you can set on different fields when adding a new Auction item ([addItemAuction](addItemAuction.md)()) or a new Fixed price item ([addItemFixedPrice](addItemFixedPrice.md)()).

Here is a list of fields name with their authorized fixed values.

#### id\_country ####

  * Country where to add the sale
  * Data type : integer
  * Accepted values and their meaning
    * **0** : .net only
    * **1** : .fr & .net
    * **2** : .de & .net
    * **3** : .nl & .net
    * **4** : .it & .net
    * **5** : .es & .net
    * **6** : .co.uk & .net
    * **7** : .com & .net
    * **8** : .ch & .net
    * **9** : .be & .net
    * **10** : .at & .net
    * **11** : .ca  & .net
    * **12** : .com.au & .net


#### id\_category ####

  * This is the matching category on Delcampe Marketplace Website
  * Data type : integer
  * Accepted values and their meaning : call [getCategoryList](getCategoryList.md)()
  * You can use the following links to get ready-to-use printable list: [ALL Categories](http://www.delcampe.net/categories_print.php?language=E&site=0)


#### currency ####

  * Currency of the price
  * Data type : string
  * Accepted values and their meanings
    * **EUR** : Euro
    * **USD** : United States dollar
    * **GBP** : Pound sterling
    * **CAD** : Canadian dollar
    * **CHF** : Swiss franc


#### duration ####

  * Duration of the sale
  * Data type : integer
  * Accepted values and their meanings
    * **7** :  sale duration of 7 days
    * **10** : sale duration of 10 days
    * **14** : sale duration of 14 days
    * **21** : sale duration of 21 days
    * **28** : sale duration of 28 days


#### renew ####

  * Number of times the sale should be renewed if the item is not sold
  * Data type : integer
  * Accepted values and their meanings
    * **0** : the sale will not be renewed
    * **1** : renew the sale 1 time
    * **2** : renew the sale 2 times
    * **3** : renew the sale 3 times
    * **4** : renew the sale 4 times
    * **5** : renew the sale 5 times
    * **10** : renew the sale 10 times
    * **99** : renew the sale 99 times


#### prefered\_end\_day ####

  * The day you want the sale to be closed
  * Data type : string
  * Accepted values and their meanings
    * **mon** : Monday
    * **tue** : Tuesday
    * **wed** : Wednesday
    * **thu** : Thursday
    * **fri** : Friday
    * **sat** : Saterday
    * **sun** : Sunday