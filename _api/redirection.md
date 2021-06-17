---
title: /Redirection
position: 1.6
type: 
description: 3DS Redirection Response
right_code: |
  ~~~ json
  {
    "result":"redirection",
    "merchantId":111111,
    "merchantTxId":"abc123",
    "txId":123,
    "redirectionUrl":"https://mpi.bank.com/123123123-abc-123123123"
  }
  ~~~
  {: title="Response" }

  ~~~ json
  {
    "error": true,
    "message": "Book doesn't exist"
  }
  ~~~
  {: title="Error" }
---

The 3DS Redirection Response is used by a merchant’s system to open a 3DS challenge window in a customer’s browser, for the customer to enter their security information and authenticate the transaction

result 
: Will always be “redirection”. **String (enum)**

merchantId 
: The merchantId value received in the Session Token Request. **Integer (18)**

merchantTxId 
: The merchant’s reference for the transaction provided in the Session Token Request. **String (50)**

txId 
: The unique identifier for a transaction in the BOIPA Gateway. **String (18)**

redirectionUrl 
: The URL to which the customer’s browser must be redirected after the 3D Secure processing is completed. **String (URL)**



{: .success }


