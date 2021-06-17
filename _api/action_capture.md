---
title: /Capture
position: 1.3
type: 
description: Capture an Auth
right_code: |
  ~~~ json
  {
    "result":"success",
    "merchantId":1111111,
    "token":"abcde12345abcde12345",
    "resultId":"fghij67890fghij67890",
    "processingTime": 2
  }
  ~~~
  {: title="Response" }

  ~~~ json
  {
    "result":"failure",
    "merchantId":1111111,
    "errors":
    [ 
    { "messageCode": "This field is required in [REQUEST]",
    "fieldName": "password" 
    } 
    ],
    "processingTime": 4
  }
  ~~~
  {: title="Error" }
---

merchantId 
: Merchant ID that identifies the merchant in the BOIPA Gateway. **Integer (18)**

token 
: Session Token received in the Session Token Request. **String (64)**

action 
: Must be "CAPTURE". **String (enum)**

allowOriginUrl 
: The merchant's URL that will make the Capture Request. **String (253)**

originalTxId 
: The Gateway transaction Id of the transaction being captured,returned in the txId field of the Auth Response. **String (18)**

Update an existing book in your collection.

~~~ javascript
$.ajax({
  "url": "http://api.myapp.com/books/3",
  "type": "PUT",
  "data": {
    "token": "YOUR_APP_KEY",
    "score": 5.0,
    "title": "The Book Stealer"
  },
  "success": function(data) {
    alert(data);
  }
});
~~~
{: title="jQuery" }
