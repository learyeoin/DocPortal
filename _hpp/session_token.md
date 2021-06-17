---
title: /Session Token
position: 1.0
type: post
description: Get a Session Token
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
offset
: Offset the results by this amount

limit
: Limit the number of books returned

This call will return a maximum of 100 books
{: .info }

Lists all the photos you have access to. You can paginate by using the parameters listed above.

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

~~~ java
<!DOCTYPE html>
<html>
<head>

<meta charset="UTF-8">
<title>Simple Javascript integration example</title>

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/3.3.7/css/bootstrap.min.css" />
<style>
#ipgCashierDiv {
	width: 600px;
	height: 400px;
	border: 1px solid gray;
	margin: 10px;
}

body {
	width: 620px;
	margin: 10px auto 10px auto;
}
</style>

<script src="https://code.jquery.com/jquery-3.2.1.min.js" integrity="sha256-hwg4gsxgFZhOsEEamdOYGBf13FyQuiTwlAQgxVSNgt4=" crossorigin="anonymous"></script>
<script src="https://cashier-apiuat.test.boipapaymentgateway.com/js/api.js"></script>

</head>
<body>

	<div>
		<form id="form">
			<div class="form-group">
				<label for="country">customerId:</label><input name="customerId" value="" class="form-control"/>
			</div>
			<div class="form-group">
				<label for="country">country:</label><input name="country" value="PL" class="form-control"/>
			</div>
			<div class="form-group">
				<label for="currency">currency:</label><input name="currency" value="PLN" class="form-control"/>
			</div>
			<div class="form-group">
				<label for="amount">amount:</label><input name="amount" value="20.0" class="form-control"/>
			</div>
			<div class="form-group">
				<label for="channel">channel:</label><input name="channel" value="ECOM" class="form-control" />
			</div>
			<div class="form-group">
				<label for="paymentSolutionId">paymentSolutionId:</label><input name="paymentSolutionId" value="500" class="form-control"/>
			</div>
		</form>
		<button onclick="pay()">Pay</button>
	</div>
	<div id="ipgCashierDiv"></div>
	<script>
		var cashier = com.myriadpayments.api.cashier();
		cashier.init({
			baseUrl : "https://cashier-apiuat.test.boipapaymentgateway.com/ui/cashier"
		});
		function handleResult(result, data) {
			alert(JSON.stringify(result));
			console.log(JSON.stringify(data));
		}
		function pay() {
			
			// get token
			// note: jQuery is not required for Turnkey JS (only used for the token request etc.)!
			var merchantId = "";
			var token = "";
			$.post("../../tokenforpurchase", {
				paymentSolutionId : $("[name='paymentSolutionId']", $("#form")).val(),
				channel : $("[name='channel']", $("#form")).val(),
				amount : $("[name='amount']", $("#form")).val(),
				currency : $("[name='currency']", $("#form")).val(),
				country : $("[name='country']", $("#form")).val(),
				customerId : $("[name='customerId']", $("#form")).val()
			}).done(function(data) {
				var p = JSON.parse(data);
				token = p.token;
				merchantId = p.merchantId;
				
				console.log("merchantId: " + merchantId);
				console.log("token: " + token);
				
				cashier.show({
					containerId : "ipgCashierDiv",
					merchantId : merchantId,
					token : token,
					successCallback : handleResult,
					failureCallback : handleResult,
					cancelCallback : handleResult
				});
				
			}).fail(function() {
				
				console.log("token error");
				
			});
		};
	</script>

</body>
</html>
~~~
{: title="Java" }
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

~~~ html
<form method="POST" action="https://api.boipapaymentgateway.com/token" target="iframe">
<!-- Required Fields-->
<label>merchantId:</label><input name="merchantId" value="111111"/><br/>
<label>password:</label><input name="password" value="u16q9rZ02bW0jqTjxH8t"/><br/>
<label>action:</label><input name="action" value="PURCHASE"/><br/>
<label>timestamp:</label><input name="timestamp" id="timestamp" value="1622119453239"/><br/>
<label>currency:</label><input name="currency" value="EUR"/><br/>
<label>country:</label><input name="country" value="IE"/><br/>
<label>merchantNotificationUrl:</label><input name="merchantNotificationUrl" value="https://ServerURL");"/>
<label>allowOriginUrl:</label><input name="allowOriginUrl" value="*"/><br/><br/>
<label>channel:</label><input name="channel" value="ECOM"/><br/>
<!-- Optional Fields-->
<label>amount:</label><input name="amount" value="25.00"/><br/>	
<label>customerId:</label><input name="customerId" value="BOIPATest"/><br/>	
<label>merchantTxId:</label><input name="merchantTxId" value="BOIPATest1"/><br/>	
<label>merchantFreeText:</label><input name="merchantFreeText" value="Some Free Text"/><br/>	
<label>language:</label><input name="language" value="Some Free Text"/><br/>	
<label>merchantLandingPageUrl:</label><input name="merchantLandingPageUrl" value="https://mLandingPageURL");"/><br/>
<label>paymentSolutionId:</label><input name="paymentSolutionId" value="500"/><br/>

<!-- Conditional Fields-->


 <!-- 3D Secure 2 Mandatory and Conditional Fields -->

<label>merchantChallengeInd:</label><input name="merchantChallengeInd" value=""/><br/>
<label>merchantDecReqInd:</label><input name="merchantDecReqInd" value=""/><br/>
<label>merchantDecMaxTime:</label><input name="merchantDecMaxTime" value=""/><br/>
<label>userDevice:</label><input name="userDevice" value=""/><br/>
<label>userAgent:</label><input name="userAgent" value=""/><br/>
<label>customerIPAddress:</label><input name="customerIPAddress" value=""/><br/>
<label>customerFirstName:</label><input name="customerFirstName" value=""/><br/>
<label>customerLastName:</label><input name="customerLastName" value=""/><br/>
<label>payerCustomerId:</label><input name="payerCustomerId" value=""/><br/>
<label>merchantReference:</label><input name="merchantReference" value=""/><br/>
<label>customerAddressHouseName:</label><input name="customerAddressHouseName" value=""/><br/>
<label>customerAddressHouseNumber:</label><input name="customerAddressHouseNumber" value=""/><br/>
<label>customerAddressFlat:</label><input name="customerAddressFlat" value=""/><br/>
<label>customerAddressStreet:</label><input name="customerAddressStreet" value=""/><br/>
<label>customerAddressCity:</label><input name="customerAddressCity" value=""/><br/>
<label>customerAddressPostalCode:</label><input name="customerAddressPostalCode" value=""/><br/>
<label>customerAddressCountry:</label><input name="customerAddressCountry" value=""/><br/>
<label>customerAddressState:</label><input name="customerAddressState" value=""/><br/>
<label>freeText:</label><input name="freeText" value="freeText"/><br/>
<label>channel:</label><input name="channel" value="ECOM"/><br/>
<label>postCode (CIP):</label><input name="customerAddressPostalCode" value="123456"/><br/>

<button type="submit" >Simulate</button>
</form>
~~~
{: title="HTML POST" }