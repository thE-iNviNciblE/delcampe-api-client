The purpose of the thirdparty authentication is to provide, to an application (your application), an api key to represent a member on Delcampe, without the need to store the Delcampe credential of this member on the application.
It's not a standardized oAuth. But it's a simplified model like oAuth.

#### Legend ####
  * application : the third party tool wich implement the api client
  * customer : the user having an account on Delcampe and an account on your application

### Step 1 ###
Your website proposes to the customer to manage his Delcampe account, and so, to make a link with our API.

### Step 2 ###
Your website calls the following API function : [getAccessKey](getAccessKey.md)

You need to provide
  * your Application Key (aka Api Key of your application)
  * the  list of API methods/rights you need to use in your application
  * the url where to return the customer, on your website, at the end of the process

This function will return a ResponseAccessKey object, containing an Access key (a temporary linker Token needed for the step 5), and an URL pointing on Delcampe website so the customer can accept or reject your resquest.

### Step 3 ###
Your application redirects the customer to the Delcampe website using the URL received above.

### Step 4 ###
Delcampe displays a page of rights you need to manage the customer account. The customer accepts or rejects your request, and is then redirected to your application (using the URL you provided in step 2).

### Step 5 ###
Your application can now call [getApiKey](getApiKey.md) with the Access key. Depending on the decision of the customer, you'll receive the API key or not : see ResponseApiKey for more details.
<a href='Hidden comment: 
=== Schema ===
* [https://docs.google.com/drawings/pub?id=1m1q_mze1xZqOkzgwZ5eSFK0f9bm3yCfCr0OB5dBcqb8&w=1010&h=1073 See last version]
'></a>