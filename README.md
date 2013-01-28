Cake PHP Optimal Payment Component with ccPurchase, ccAuthorize, ccVerification, ccSettlement, ccStoredDataPurchase and ccStoredDataAuthorize
==========================================
The main features implmented are, 

* Purchase with credit card info .
* Purchase Authorization with credit card info  : [for those who not aware about Auth:, This is process of getting a permission to get a money(Called Capture) in future based on users permission gained in Approval(Authorization) part. ]
* Verify/Validate the credit card Information.
* Ability to purchase new item/product based on  users  previous purchase data(Doesn’t means  we are saving an credit card info).

 	
== Minimum Requirements ==

* Cake PHP 1.3 or later
* cURL support
* SimpleXml

== Main Modules includes ==

* ccPurchase
* ccAuthorize
* ccVerification
* ccSettlement,
* ccStoredDataPurchase
* ccStoredDataAuthorize

== Implementation ==

=== Models === 

Add models for logs and necessary change to save info

=== Controller === 

Add Optimal Payment component in the components array( Sorry Cake gurus. It’s intented for all from freshers to gurus ;) ).

 <nowiki>public $components = array(
        'All',
        'YourExisting',
        'Components ',
        'OptimalPayment',
    );
 </nowiki>

=== Views === 
Necessary Codes to get user inputs, like amount and credit card info
