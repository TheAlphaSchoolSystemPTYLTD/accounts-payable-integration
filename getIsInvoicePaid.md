**getIsInvoicePaid**
----
	Returns a structure with one property to indicate if the specified invoice for the specified supplier has been paid

* **Version:**

	2

* **Method:**

	`GET | POST`
	
*  **Params:**

	**Required:**
 
	`supplier_code [string]`

	`vouch_code [string]`

	**Optional:**

	none

	**Conditional:**

	none

* **Success Response:**
		
		ColdFusion 2011
		```javascript
		"invoice_paid": "Yes"
		```

		ColdFusion 2016
		```javascript
		"invoice_paid": true
		```
 
* **Error Response:**

		`supplier_code` not supplied
		```javascript
		__invalid: {
			"supplier_code": "field is required"
		}
		```
		
		`vouch_code` not supplied
		```javascript
		__invalid: {
			"vouch_code": "field is required"
		}
		```
		
* **Sample Parameters:**

	```javascript
		{ 
			"supplier_code":"ABC123"
			, "vouch_code":"12345"
		}
	```

* **Sample GET:** (With URL Encoded `token`)

	```HTML
		http://api.tasscloud.com.au/tassweb/api/?method=GetIsInvoicePaid&appcode=DEMOAP&company=10&v=2&token=IBzPtFbCrfnUtDJ3HQCN1rog9756syITU5czlRz1pog%3D
	```
	
* **Sample POST:**

	```HTML
		<form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
			<input type="hidden" name="method" value="GetIsInvoicePaid">
			<input type="hidden" name="appcode" value="DEMOAP">
			<input type="hidden" name="company" value="10">
			<input type="hidden" name="v" value="2">
			<textarea name="token">IBzPtFbCrfnUtDJ3HQCN1rog9756syITU5czlRz1pog=</textarea>
		</form>
	```
