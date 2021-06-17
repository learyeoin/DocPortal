---
title: /Session Token
position: 1.0
type: 
description: Generate a Session Token.
right_code: |
  ~~~ json
  [
   {
        "result":"success",
       "resultId":"8b181452-d0fc-4758-bb7f-a6d5c24a3b22",
       "merchantId":"YOUR_MERCHANTID",
       "additionalDetails":{},
       "processingTime":15,
       "token":"52ab583d-e771-49e9-8931-36efd7a3603e"
      },
  ]
  ~~~
  {: title="Response" }

  ~~~ json
  {
        "result":"failure",
       "resultId":"53e7926b-9015-4430-983a-de0beea3ed3d",
       "additionalDetails":{},,
       "errors":[{"messageCode":"This field is required in [REQUEST]",
       "processingTime":15,
       "token":"52ab583d-e771-49e9-8931-36efd7a3603e",
       "fieldName":"",
       "processingTime":5
      }
  ~~~
  {: title="Error" }
---
merchantId 
: Merchant ID that identifies the merchant in the BOIPA Gateway. **Integer (18)**

password
: The merchant’s password for the Gateway. **String (64)**

action
: Must be "TOKENIZE", “AUTH”, “PURCHASE” or “VERIFY”. **String (enum)**

timestamp
: Milliseconds since 1970-01-01 00:00:00. **Integer (13)**

allowOriginUrl
: The merchant's URL that will make the Request, Cross-Origin Resource Sharing (CORS) headers will allow only this origin. **String (253)**

This call will return a maximum of 100 books
{: .info }

Lists all the photos you have access to. You can paginate by using the parameters listed above.
~~~ php
<?php
      $url = "https://apiuat.test.boipapaymentgateway.com/token";
        $data = array(
        merchantId => "YOUR_MERCHANTID",
        password => "YOUR_API_PASSWORD",
        brandId => "YOUR_BRANDID",
        action =>"TOKENIZE/AUTH/PURCHASE/VERIFY",
        timestamp => "TIMESTAMP_IN_MILLISECONDS",
        channel => "ECOM/MOTO",
        country => "COUNTRY_ISO_CODE",
        allowOriginUrl => "MERCHANT_URL_MAKING_REQUEST",
        language => "LANGUAGE_ISO_CODE",
        amount => "AMOUNT",
        currency => "CURRENCY",
        forceSecurePayment => "true",
      );
      echo"<pre>";
      print_r($data);
      echo"</pre>";
      // API call using cURL
      $resultTokenRequest = json_decode(makePOSTcURLHttpRequest($url,$data),true);
      echo"<pre>";
      print_r($resultTokenRequest);
      echo"</pre>";
      
      }
      ?>
~~~
{: title="PHP" }
~~~ javascript
$.get("http://api.myapp.com/books/", { "token": "YOUR_APP_KEY"}, function(data) {
  alert(data);
});
~~~
{: title="jQuery" }

~~~ python
r = requests.get("http://api.myapp.com/books/", token="YOUR_APP_KEY")
print r.text
~~~
{: title="Python" }

~~~ javascript
var request = require("request");
request("http://api.myapp.com/books?token=YOUR_APP_KEY", function (error, response, body) {
  if (!error && response.statusCode == 200) {
    console.log(body);
  }
});
~~~
{: title="Node.js" }

~~~ html
curl http://sampleapi.readme.com/orders?key=YOUR_APP_KEY
~~~
{: title="HTML POST" }

