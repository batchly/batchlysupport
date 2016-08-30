#### Batchly REST API ####

Each customer of batch.ly gets their own customized URL for access.  Using the web console, you can generate new set of API access keys.  You need to safe keep the keys.  Batchly API SDK doesn’t send the secret key in any request.  The authentication mechanism employed on the server side is HMAC which validates calls using request signature.  Server endpoint support both the JSON and XML data formats.  The SDK is configured to use the JSON data format.

Before making calls to the API, setup the base URI, access key and secret key in the configuration.

Each of the major endpoints are grouped based on the high level entities.  For each high level entity, a controller is available.  Initialize the controller and call the appropriate methods.  All the constant values are available as Enumerations so that magic values need not be remembered.

To call any of the methods, create a new instance of the appropriate controller. Call the respective methods by creating the appropriate request objects. The following example shows the basic usage of the API to get list of accounts.

    Language : ruby
 
    require 'batchly_api'
 
    BatchlyApi::Configuration . BASE_URI = 'YOUR CUSTOMIZED ENDPOINT URL'
    BatchlyApi::Configuration . API_KEY =   'YOUR ACCESS KEY'
    BatchlyApi::Configuration . API_SECRET =   'YOUR SECRET KEY'
 
    ctrl =   BatchlyApi::AccountsController . new
    response = ctrl. list_accounts