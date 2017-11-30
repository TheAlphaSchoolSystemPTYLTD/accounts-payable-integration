**setGLInvoice**
----
	Returns "Success" and document number "vouch_code" if the invoice successfully created, or a structure of invalid validations "__invalid" if the invoice is unsuccessfully created.

* **Version:**

	2

* **Method:**

	`GET | POST`
	
*  **Params:**

	**Required:**
 
	`supplier_code [string]` - Supplier Code

	`invoice_number [string]` - Invoice Number

	`invoice_date [date dd/mm/yyyy]` - Invoice Date

	`invoice_amount [decimal]` - Invoice Amount

	`comment_1 [string]` - Comment 1

	`id [string]` - Unique Identity of GL Distribution

	`account_code [string]` - GL Account of GL Distribution

	`desc_text [string]` - Description Text of GL Distribution

	`dist_amount [decimal]` - Distribution Amount of GL Distribution

	`tax_amount [decimal]` - Tax Amount of GL Distribution

	`tax_code [string]` - Tax Code of GL Distribution

	**Optional:**
	
	`year [integer]` - Year

	`period [integer]` - Period

	`term_code [string]` - Term Code

	`due_date [date dd/mm/yyyy]` - Due Date 

	`hold_code [string]` - Hold Payment Code

	`comment_2 [string]` - Comment 2

	`gldistributions [array]` - Array of GL Distributions

	**Conditional:**

	`attachment_file [string]` - Base64 Encoded PDF File. Required where `attachment_file_name` supplied

	`attachment_file_name [string]` - Name of PDF attachment. Required where `attachment_file` supplied. If supplied, length must be between 1 and 255 Characters

* **Success Response:**

	```javascript
	"success": "Invoice created successfully.",
	"vouch_code": 672
	```
 
* **Error Response:**

	Required `[field_name]` not supplied
	```javascript
	__invalid: {
		"[field_name]": "field is required"
	}
	```
	
	Date `[field_name]` not a valid date
	```javascript
	__invalid: {
		"[field_name]": "Value is not a valid date."
	}
	```
	
	Integer `[field_name]` not a valid integer
	```javascript
	__invalid: {
		"[field_name]": "Value is not a valid integer."
	}
	```

	Decimal `[field_name]` not a valid decimal
	```javascript
	__invalid: {
		"[field_name]": "Value is not a valid decimal."
	}
	```

	`supplier_code` not a valid supplier code in the "vendor" table
	```javascript
	__invalid: {
		"supplier_code": "Supplier Code is invalid."
	}
	```

	`supplier_code` not active
	```javascript
	__invalid: {
		"supplier_code": "Supplier Code is not Active."
	}
	```

	`supplier_code` not non-misc type
	```javascript
	__invalid: {
		"supplier_code": "Supplier Code is a Misc Supplier."
	}
	```

	`invoice_number` not unique
	```javascript
	__invalid: {
		"invoice_number": "Invoice Number already used."
	}
	```

	`invoice_number` exceed 20 characters
	```javascript
	__invalid: {
		"invoice_number": "Value exceeds 20 characters."
	}
	```

	`year` not a valid year in the "period" table that is "open" for AP entry
	```javascript
	__invalid: {
		"year": "Year / Period is invalid or not open."
	}
	```

	`period` not a valid period in the "period" table that is "open" for AP entry
	```javascript
	__invalid: {
		"period": "Year / Period is invalid or not open."
	}
	```

	`invoice_amount` less than or equal 0.00
	```javascript
	__invalid: {
		"invoice_amount": "Invoice Amount is invalid."
	}
	```

	`invoice_amount` has more than 2 decimal points
	```javascript
	__invalid: {
		"invoice_amount": "Value has more than 2 decimal points."
	}
	```

	`invoice_amount` greater than Available Credit from "vendor" table 
	```javascript
	__invalid: {
		"invoice_amount": "Invoice Amount exceeds Credit Limit."
	}
	```

	`term_code` not a valid term code in "terms" table when supplied 
	```javascript
	__invalid: {
		"term_code": "Term Code is invalid."
	}
	```

	`due_date` less than `invoice_date` when supplied 
	```javascript
	__invalid: {
		"due_date": "Due Date is less than Invoice Date."
	}
	```

	`hold_code` different from "NO" when supplied 
	```javascript
	__invalid: {
		"hold_code": "Hold Payment Code is invalid."
	}
	```

	`comment_1` exceed 30 characters
	```javascript
	__invalid: {
		"comment_1": "Value exceeds 30 characters."
	}
	```

	`comment_2` exceed 30 characters
	```javascript
	__invalid: {
		"comment_2": "Value exceeds 30 characters."
	}
	```

	`id` not supplied
	```javascript
	__invalid: {
		"id": "Id is required for all rows."
	}
	```

	`id` not unique
	```javascript
	__invalid: {
		"id": "Id must be unique for all rows."
	}
	```

	`account_code` must be a valid GL Account and not a Bank or Control Account
	```javascript
	__invalid: {
		"account_code": "GL Account is invalid."
	}
	```

	`account_code` not an "open" account
	```javascript
	__invalid: {
		"account_code": "GL Account must be open."
	}
	```

	`desc_text` exceed 4000 characters
	```javascript
	__invalid: {
		"desc_text": "Value exceeds 4000 characters."
	}
	```

	`dist_amount` equal 0.00
	```javascript
	__invalid: {
		"dist_amount": "Distribution Amount is invalid."
	}
	```

	`dist_amount` has more than 2 decimal points
	```javascript
	__invalid: {
		"dist_amount": "Value has more than 2 decimal points."
	}
	```

	`tax_amount` has more than 2 decimal points
	```javascript
	__invalid: {
		"tax_amount": "Value has more than 2 decimal points."
	}
	```

	`tax_amount` must be >= 0.00 if `dist_amount` > 0.00, or must be <= 0.00 if `dist_amount` < 0.00
	```javascript
	__invalid: {
		"tax_amount": "Tax Amount is invalid."
	}
	```

	`tax_amount` must be <= `dist_amount` if `dist_amount` > 0.00, or must be >= `dist_amount` if `dist_amount` < 0.00
	```javascript
	__invalid: {
		"tax_amount": "Tax Amount is greater than Distribution Amount."
	}
	```

	`tax_code` not a valid tax code in "tax" table
	```javascript
	__invalid: {
		"tax_code": "Tax Code is invalid."
	}
	```

	`attachment_file_name` not supplied where `attachment_file` is supplied
	```javascript
	__invalid: {
		"attachment_file_name": "attachment_file_name field is required where 'attachment_file' is supplied."
	}
	```

	`attachment_file_name` not supplied where `attachment_file` is supplied
	```javascript
	__invalid: {
		"attachment_file_name": "attachment_file_name field is required where 'attachment_file' is supplied."
	}
	```

	`attachment_file_name` length less than 1 or greater than 255 characters
	```javascript
	__invalid: {
		"attachment_file_name": "attachment_file_name must be between 1 and 255 characters."
	}
	```

	`attachment_file` not supplied where `attachment_file_name` is supplied
	```javascript
	__invalid: {
		"attachment_file": "attachment_file field is required where 'attachment_file_name' is supplied."
	}
	```

	`attachment_file` is not a valid Base64 Encoded string representation of a PDF file
	```javascript
	__invalid: {
		"attachment_file": "attachment_file must be a Base 64 encoded string representation of a PDF file."
	}
	```
	
* **Sample Parameters:**

	```javascript
	{
		"supplier_code":"ABCSTAT"
		,"invoice_number":"test1"
		,"invoice_date":"27/07/2017"
		,"invoice_amount":"2"
		,"comment_1":"test creating invoices"
		,"gldistributions":[
			{
				"id":"1"
				,"account_code":"01-1330-00-00"
				,"desc_text":"first distribution"
				,"dist_amount":"1.24"
				,"tax_amount":"0.04"
				,"tax_code":"AO"
			},{ 
				"id":"2"
				,"account_code":"01-1330-00-00"
				,"desc_text":"second distribution"
				,"dist_amount":"0.76"
				,"tax_amount":"0.02"
				,"tax_code":"WHT"
			}
		]
	}
	```

* **Sample GET:** (With URL Encoded `token`)

	```HTML
	http://api.tasscloud.com.au/tassweb/api/?method=SetGLInvoice&appcode=DEMOAP&company=10&v=2&token=BJVvYXC0We4Dtvp6Q49RqhBeAi6uqpTQ9t%2FKI9ZAFpCMeVXIFlDU5yNQIeYME%2BYLXgYA69RTUjXjLeVBetN6CaFMdPCKMWBXD%2Bkkt0%2Fuht0suYrSDONP6mx%2Fbt4WGgNOD5YoIYRNiIVDw2Qn2Oi5YodaEUgtGJohUJMzy3tqsX%2BraZk3j7d77okDCjb7MeFJ0DcupqUoRiGjE39415HTfPgNc6R6BY9wt7SJsj4yOPBrIxHQVS8Yy6gZ3nZgsJ5rhcdkB6eCI6b3FJ31s6vsVcbVu5NBY8AF1qqjWLMazduISzEBwRDsofXfJjo1KLX59R410bmbrF5Z7QZfEfE%2FlettTWOyb4EgdhBoC3v0aLOfF6Bt12AFXDo2VGbgryceeOLAscp%2FFr9ttH42hClBtWsxFU1N5dDENUsVHOwWcfCxd7aTtc0xjvaEYJWcZrRRZa1yrIvgeWaDk0LVxM5ePcT%2BltdrymgmxmZYgxdiYC1qQDcNXDx9hN7yKeZDUztwGA0yl2iXW8aBXAy5hRnztR0TrREyOba26mUHxUJO7tfpIyOrpPbE0nR18vtCZ%2BinbvyqN9adpZhQPByG2XD9M6MoYdmBCc3Duv9qb%2BIa0A8%3D
	```
	
* **Sample POST:**

	```HTML
	<form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
		 <input type="hidden" name="method" value="setGLInvoice">
		 <input type="hidden" name="appcode" value="DEMOAP">
		 <input type="hidden" name="company" value="10">
		 <input type="hidden" name="v" value="2">
		 <textarea name="token">BJVvYXC0We4Dtvp6Q49RqhBeAi6uqpTQ9t/KI9ZAFpCMeVXIFlDU5yNQIeYME+YLXgYA69RTUjXjLeVBetN6CaFMdPCKMWBXD+kkt0/uht0suYrSDONP6mx/bt4WGgNOD5YoIYRNiIVDw2Qn2Oi5YodaEUgtGJohUJMzy3tqsX+raZk3j7d77okDCjb7MeFJ0DcupqUoRiGjE39415HTfPgNc6R6BY9wt7SJsj4yOPBrIxHQVS8Yy6gZ3nZgsJ5rhcdkB6eCI6b3FJ31s6vsVcbVu5NBY8AF1qqjWLMazduISzEBwRDsofXfJjo1KLX59R410bmbrF5Z7QZfEfE/lettTWOyb4EgdhBoC3v0aLOfF6Bt12AFXDo2VGbgryceeOLAscp/Fr9ttH42hClBtWsxFU1N5dDENUsVHOwWcfCxd7aTtc0xjvaEYJWcZrRRZa1yrIvgeWaDk0LVxM5ePcT+ltdrymgmxmZYgxdiYC1qQDcNXDx9hN7yKeZDUztwGA0yl2iXW8aBXAy5hRnztR0TrREyOba26mUHxUJO7tfpIyOrpPbE0nR18vtCZ+inbvyqN9adpZhQPByG2XD9M6MoYdmBCc3Duv9qb+Ia0A8=</textarea>
	</form>
	```
