---
title: /Purchase
position: 1.5
type: 
description: Deletes a book
right_code: |
  ~~~ json
  {
    "result":"success",
    "merchantId":111111,
    "merchantTxId":"abc123",
    "txId":"123",
    "acquirerTxId":"0009312",
    "amount":12.50,
    "currency":"EUR",
    "customerId":"mgn456",
    "action":"PURCHASE",
    "pan":"45ae201ghy23498FjMj701",
    "brandId":111111000,
    "paymentSolutionId":500,
    "freeText":"Added+10%+discount+on+the+item",
    "language":"en",
    "acquirerAmount":12.50,
    "acquirerCurrency":"EUR",
    "paymentSolutionDetails":
        {
            "authCode":"1234"
        },
    "status":"SET_FOR_CAPTURE"
  }
  ~~~
  {: title="Response" }

  ~~~ json
  {
    "result": "failure",
    "resultId": "7433a8d6-caea-40e6-a6eb-90c11dad61be",
    "additionalDetails": {},
    "errors": [
    {
    "messageCode": "field.nonempty",
    "fieldName": "action"
  }
  ],
    "processingTime": 2
  }
  ~~~
  {: title="Error" }
---
Deletes a book in your collection.

~~~ javascript
$.ajax({
  "url": "http://api.myapp.com/books/3",
  "type": "DELETE",
  "data": {
    "token": "YOUR_APP_KEY"
  },
  "success": function(data) {
    alert(data);
  }
});
~~~
{: title="jQuery" }
