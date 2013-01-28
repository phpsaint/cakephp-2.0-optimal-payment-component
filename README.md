#Cake PHP Optimal Payment Component with ccPurchase, ccAuthorize, ccVerification, ccSettlement, ccStoredDataPurchase and ccStoredDataAuthorize

The main features implmented are, 

* Purchase with credit card info .
* Purchase Authorization with credit card info  : [for those who not aware about Auth:, This is process of getting a permission to get a money(Called Capture) in future based on users permission gained in Approval(Authorization) part. ]
* Verify/Validate the credit card Information.
* Ability to purchase new item/product based on  users  previous purchase data(Does not means  we are saving an credit card info).

 	
##Minimum Requirements

* Cake PHP 1.3 or later
* cURL support
* SimpleXml

##Main Modules includes

* ccPurchase
* ccAuthorize
* ccVerification
* ccSettlement,
* ccStoredDataPurchase
* ccStoredDataAuthorize

##Implementation


### Models

Add models for logs and necessary change to save info

### Controller

Add Optimal Payment component in the components array( Sorry Cake gurus. It is intented for all from freshers to gurus ;) ).

<pre>
public $components = array(
        'All',
        'YourExisting',
        'Components ',
        'OptimalPayment',
    );

</pre>

### Views
Necessary Codes to get user inputs, like amount and credit card info


##Sample Implementation

<pre class="php">// This is sample code to show how it works
// Please add necessary code for get input from user, validation,.. 

$merchant_info = array(
	'accountNum' =&gt;'MERCHANT_ACC_NUMBER',
	'storeID' =&gt;'test',
	'storePwd' =&gt;'test',
	'is_test' =&gt; true,
);
$payment_info= array(
	'user_id' =&gt; '1111111111111',
	'amount' =&gt; 22,
	'card_deatils' =&gt;array(
		'cardNum' =&gt;'1111111111111111',
		'cardExpiry' =&gt;array(
			'month' =&gt; '12',
			'year' =&gt;  '12'
		),
		'cardType' =&gt; 'VI',
		'cvdIndicator' =&gt;1, // Do we need CVV
		'cvd' =&gt;'111'
	),
	'billing_info' =&gt; array(
		"firstName"	=&gt; 'Test',
		"lastName"	=&gt; 'Test',
		"street"	=&gt;  '1130 test',
		"street2"	=&gt;  '',
		"city"		=&gt;  'Laval',
		"state"		=&gt;  'QC',
		"country"	=&gt;  'CA',
		"zip"		=&gt;  'H7V 1A2',
		"phone"		=&gt;  '123-973-2227',
		"email"		=&gt;  'email@example.com',
	)
);

$this-&gt;OptimalPayment-&gt;intiatePayment($merchant_info);
// Authorization
$result = $this-&gt;OptimalPayment-&gt;doAuthorize($payment_info);

$reversal_info = array(
	'user_id' =&gt; '1111111111111',
	'amount'  =&gt; 22,
	'confirmation_number' =&gt;'233444',
);

//$result = $this-&gt;OptimalPayment-&gt;doAuthReversal($reversal_info);

$cpature_info = array(
	'user_id' =&gt; '1111111111111',
	'amount'  =&gt; 22,
	'confirmation_number'=&gt;'1233',
);

$result = $this-&gt;OptimalPayment-&gt;doAuthSettlement($cpature_info);

</pre>