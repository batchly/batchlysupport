### Batchly REST API

Each customer of batchly gets their own customized URL for access. Using the web console, you can generate new set of API access keys.  You need to safe keep the keys.  Batchly API SDK doesn’t send the secret key in any request. Batchly supports two types of API authentication mechanisms -  HMAC which validates calls using request signature and ApiKey based.

Before making calls to the API, setup the base URI, access key and secret key in the configuration.

#### End Point
To call API requests to Batchly.net, please send HTTP(S) post requests to:

```
https://<customerdomain>.batchly.net/api/
```

#### Authentication
** ApiKey **

A user's unique authentication key string. This authentication key will be shared with your team when the system is configured for your usage. This key is mandatory and needs to be sent as part of every API call. The Key should be sent along in the Request Header as below.

```
Authorization: ApiKey AccessKey:SecretKey
```

#### Support
Please reach out to [support@batchy.net](mailto:support@batchly.net) to get your API Keys if you do not have the keys and/or receiving authentication errors.