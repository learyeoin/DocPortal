---
title: Authentication
position: 2
right_code: |
  ~~~ javascript
  $.get("http://api.myapp.com/books/", { "token": "YOUR_APP_KEY"}, function(data) {
    alert(data);
  });
  ~~~
  {: title="jQuery" }

  ~~~ php
  <?php
      $url = "https://apiuat.test.boipapaymentgateway.com/token";
        $data = array(
        merchantId => "YOUR_MERCHANTID",
        password => "YOUR_API_PASSWORD",
        brandId => "YOUR_BRANDID",
        action =>"AUTH/PURCHASE/VERIFY",
        timestamp => "TIMESTAMP_IN_MILLISECONDS",
        channel => "ECOM",
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
  ~~~ bash
  curl http://api.myapp.com/books?token=YOUR_APP_KEY
  ~~~
  {: title="Curl" }
---

You need to be authenticated for all API requests. You can generate an API key in your developer dashboard.

Add the API key to all requests as a GET parameter.

Nothing will work unless you include this API key
{: .error }
