---
title: /Tokenize
position: 1.1
type: 
description: Create a Card Token
right_code: |
  ~~~ json
  {
    "result": "success",
    "country": "IE",
    "resultId": "e086f9ad-6a78-4c56-b4e7-059764246811",
    "merchantId": "111111",
    "cardType": "400",
    "customerId": "testTokenize",
    "additionalDetails": {},
    "cardToken": "5512732598811111",
    "processingTime": 1000,
    "cardIssuer": null
  }
  ~~~
  {: title="Response" }

  ~~~ json
  {
    "result": "failure",
    "resultId": "4e879e03-9ff1-481e-9611-b5155328a53f",
    "additionalDetails": {},
    "errors": [
  {
    "messageCode": "This field is required in [REQUEST]",
    "fieldName": "number"
  }
  ],
    "processingTime": 8
  }
  ~~~
  {: title="Error" }
---



A Tokenize request is only used with Direct API Integrations. <br>
The response provides a Token that represents a card stored in our Gateway. 
<br> This Card Token is then used in all subsequent API requests in place of the card details. 
<br> A Tokenize request is the only request that accepts real card data. <br>
The card details are provided to the Gateway in a Tokenize request and stored in the Gateway’s own PCI Level 1 compliant environment, where the card details are encrypted.
{: .success }


merchantId 
: Merchant ID that identifies the merchant in the BOIPA Gateway. **Integer (18)**

token 
: Session Token received in the Session Token Request. **String (64)**

number 
: Card number - Used to determine the card type. **String (100)**

nameOnCard 
: Cardholder name. **String (150)**

expiryMonth 
: Card expiration month, e.g. “04”. **String (2)**

expiryYear 
: Card expiration year, e.g. “2025”. **String (4)**

cardDescription 
: Free form text field for the merchant’s use that is used for reconciliation. **String (50)**


{: .success }

Generate a Tokenize Request.

~~~ php
<pre>
    <?php
    include_once '../../payments.php';
    include_once '../example_data.php';

    use Payments\Payments;

try {
        $payments = (new Payments())->testEnvironment(array(
            "merchantId" => $merchantId,
            "password" => $password,
        ));
        $tokenize = $payments->tokenize();
        $tokenize->allowOriginUrl("http://google.com/")->
                number("5454545454545454")->
                nameOnCard("John Doe")->
                expiryMonth("12")->
                expiryYear("2025");
        $token = $tokenize->execute();
        var_dump($token);
    } 
	catch (Exception $e) 
	{
        var_dump("Exception");
        var_dump($e->getMessage());
        var_dump($e->getCode());
        var_dump($e->getFile());
        var_dump($e->getLine());
    }
    ?>
</pre>
~~~
{: title="PHP" }
~~~ php

	public void reqParExExpTestCall() {

		try {

			final Map<String, String> inputParams = new HashMap<>();
			inputParams.put("number", "5454545454545454");
			inputParams.put("nameOnCard", "John Doe");
			inputParams.put("expiryMonth", "12");
			inputParams.put("expiryYear", "2025"); 

			final TokenizeCall call = new TokenizeCall(config, inputParams, null);
			call.execute();

		} catch (RequiredParamException e) {

			Assert.assertEquals(new HashSet<>(Arrays.asList("expiryYear")), e.getMissingFields());
			throw e;

		}
	}

	
	
	public void actCallExExpTestCall() {

		final Map<String, String> inputParams = new HashMap<>();
		inputParams.put("number", "5454545454545454");
		inputParams.put("nameOnCard", "John Doe");
		inputParams.put("expiryMonth", "12");
		inputParams.put("expiryYear", "2025"); // past date

		final TokenizeCall call = new TokenizeCall(config, inputParams, null);
		call.execute();
	}
}
~~~
{: title="Java" }
~~~ javascript
import ActionType from './define/ActionType.js';
import BaseApiCall from './BaseApiCall.js';

/**
 * card tokenize for future use
 *

 */
export default class TokenizeCall extends BaseApiCall {
  constructor(inputParams, extraConfig = null) {
    super(inputParams, ActionType.TOKENIZE, extraConfig);
    //initialize the token request
    this.paramsConfig();
  }

  /**
   * init params for token request and action request
   */
  paramsConfig = () => {
    const {merchantId, password, allowOriginUrl, number, nameOnCard, expiryMonth, expiryYear} = this.inputParams;
    this.initTokenParams({
      'merchantId': merchantId,
      'password': password,
      'allowOriginUrl': allowOriginUrl,
      'action': this.actionType,
      'timestamp': Date.now(),
    }, false);
    this.initActionParams({
      'number': number,
      'nameOnCard': nameOnCard,
      'expiryMonth': expiryMonth,
      'expiryYear': expiryYear,
    });
    this.initMandatory([
      'number',
      'nameOnCard',
      'expiryMonth',
      'expiryYear',
    ]);
  };
}

~~~
{: title="Node.js" }