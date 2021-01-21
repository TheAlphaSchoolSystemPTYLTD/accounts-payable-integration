**EditPOLine**
----
	Returns "success" message including the PO Number and Line Number, or a structure of invalid validations "__invalid" belonging to a Purchase Order Record.

* **Version History:**

    TASS v54.0 - Method Added

* **Version:**

	2
    
* **Method:**

	`GET | POST`
	
*  **Params:**

	**Required:**
 
	`id [string]` - Need to be integer 1.

	`order_num [integer]` - Purchse Order Number.

	`line_num [integer]` - Line Number.

	`vend_code [string]` - Supplier Code.

	`accept_budget_warning [string]` - Accept Budget Warning.

	**Optional:**

	`acct_code [string]` - General Ledger Account.

	`desc_text [string]` - Line Description.

	`order_qty [string]` - Order Quantity.

	`unit_cost_amt [string]` - Unit Cost.

	`cost_inc_tax_flg [string]` - Cost Include Tax Flag. (Default value = "N")

	`ref_text [string]` - Item Reference.

	`oem_text [string]` - Supplier Reference.

	`tax_code [string]` - Tax Code.

	`unit_tax_amt [string]` - Unit Tax.

	**Conditional:**

	None

* **Success Response:**

	```javascript
	{
		"success":"You successfully updated a PO Line (PO Number 367 and Line Number 4).",
		"__tassversion":"01.053.3.000",
		"token":{
			"poline":[
				{
					"order_num":367,
					"desc_text":"line text 4000 limit.",
					"order_qty":10.11,
					"acct_code":"01-1400-00-00",
					"line_num":4,
					"ref_text":"this is a reference.",
					"cost_inc_tax_flg":"Y",
					"id":1,
					"unit_cost_amt":10.1111,
					"accept_budget_warning":"Y",
					"vend_code":"00012"
				}
			],
			"timestamp":"{ts '2020-09-16 21:52:01'}"
		}
	}
	```
 
* **Error Response:**

	`poline` not supplied
	```javascript
	__invalid: {
		"poline": "'poline' is required."
	}
	```

	`[field_name]` is not valid
	```javascript
	__invalid: {
		"[field_name]": "'[field_name]' is not a valid field name"
	}
	```

	`poline` contains more than one record
	```javascript
	__invalid: {
		"poline": "Only one record can be inserted at a time."
	}
	```

	`id` not supplied
	```javascript
	__invalid: {
		"poline": "Id is required for all rows."
	}
	```

	`id` has a duplicate value
	```javascript
	__invalid: {
		"poline": "Id must be unique for all rows."
	}
	```

	`cost_inc_tax_flg` is not Y or N
	```javascript
	__invalid: {
		"cost_inc_tax_flg": "Value is invalid."
	}
	```

	`accept_budget_warning` is not Y or N
	```javascript
	__invalid: {
		"accept_budget_warning": "Value is invalid."
	}
	```

	`vend_code` exceeds 8 characters
	```javascript
	__invalid: {
		"vend_code": "exceeds 8 characters."
	}
	```

	`acct_code` exceeds 18 characters
	```javascript
	__invalid: {
		"acct_code": "exceeds 18 characters."
	}
	```

	`ref_text` exceeds 25 characters
	```javascript
	__invalid: {
		"ref_text": "exceeds 25 characters."
	}
	```

	`oem_text` exceeds 15 characters
	```javascript
	__invalid: {
		"oem_text": "exceeds 15 characters."
	}
	```

	`desc_text` exceeds 4000 characters
	```javascript
	__invalid: {
		"desc_text": "exceeds 4000 characters."
	}
	```

	`tax_code` exceeds 3 characters
	```javascript
	__invalid: {
		"tax_code": "exceeds 3 characters."
	}
	```

	`order_num` is not a valid code in purchdetl table
	```javascript
	__invalid: {
		"order_num": "PO Number is invalid."
	} 
	```

	`line_num` is not a valid code in purchdetl table
	```javascript
	__invalid: {
		"line_num": "Line Number is invalid."
	} 
	```

	`order_num` period for this PO is closed
	```javascript
	__invalid: {
		"order_date": "Period for PO Date is closed."
	} 
	```

	`acct_code` Account is over budget (When enhpuparms.warn_prevent = "P" OR accept_budget_warning = "N")
	```javascript
	__invalid: {
		"line_total_amt": "Account is over budget."
	} 
	```

	`order_num` Order Status is not "P" OR "O"
	```javascript
	__invalid: {
		"status_ind": "PO Status is invalid."
	} 
	```

	`vend_code` does not match the Supplier Code of the Purchase Order
	```javascript
	__invalid: {
		"vend_code": "PO Number is not valid for Supplier Code."
	} 
	```

	`vend_code` is not in vendor table
	```javascript
	__invalid: {
		"vend_code": "Supplier Code is invalid."
	} 
	```

	`vend_code` is not active
	```javascript
	__invalid: {
		"vend_code": "Supplier Code is not Active."
	} 
	```

	`acct_code` is not in coa table
	```javascript
	__invalid: {
		"acct_code": "GL Account is invalid."
	} 
	```

	`acct_code` is a bankAccount OR a controlAccount
	```javascript
	__invalid: {
		"acct_code": "GL Account is invalid."
	} 
	```

	`acct_code` is closed
	```javascript
	__invalid: {
		"acct_code": "GL Account must be open."
	} 
	```

	`order_qty` is less than 0.00
	```javascript
	__invalid: {
		"order_qty": "Must be greater than or equal to 0.00."
	} 
	```

	`order_qty` is greater than 99999.99
	```javascript
	__invalid: {
		"order_qty": "Must be less than or equal to 99,999.99."
	} 
	```

	`order_qty` has more than 2 decimal points
	```javascript
	__invalid: {
		"order_qty": "Value has more than 2 decimal points."
	} 
	```

	`unit_cost_amt` is less than 0.0000
	```javascript
	__invalid: {
		"unit_cost_amt": "Must be greater than or equal to 0.0000."
	} 
	```

	`unit_cost_amt` is greater than 9999999.9999
	```javascript
	__invalid: {
		"unit_cost_amt": "Must be less than or equal to 9,999,999.9999."
	} 
	```

	`unit_cost_amt` has more than 4 decimal points
	```javascript
	__invalid: {
		"unit_cost_amt": "Value has more than 4 decimal points."
	} 
	```

	`unit_tax_amt` is less than 0.0000
	```javascript
	__invalid: {
		"unit_tax_amt": "Must be greater than or equal to 0.0000."
	} 
	```

	`unit_tax_amt` is greater than 9999999.9999
	```javascript
	__invalid: {
		"unit_tax_amt": "Must be less than or equal to 9,999,999.9999."
	} 
	```

	`unit_tax_amt` has more than 4 decimal points
	```javascript
	__invalid: {
		"unit_tax_amt": "Value has more than 4 decimal points."
	} 
	```

	`unit_tax_amt` is greater than `unit_cost_amt`
	```javascript
	__invalid: {
		"unit_tax_amt": "Must be less than or equal to Unit Cost."
	} 
	```

	`tax_code` is not in tax table
	```javascript
	__invalid: {
		"tax_code": "Tax Code is invalid."
	} 
	```

* **Sample Parameters:**

	```javascript
	{
		"poline":[
			{
				"id":"1",
				"line_num":"4",
				"order_num":"367111",
				"vend_code":"00012",
				"acct_code":"01-1400-00-00",
				"ref_text":"this is a reference.",
				"desc_text":"line text 4000 limit.",
				"order_qty":10.11,
				"unit_cost_amt":10.1111,
				"cost_inc_tax_flg":"Y",
				"accept_budget_warning":"Y"
			}
		]
	}
	```

* **Sample GET:** (With URL Encoded `token`)

	```HTML
	http://api.tasscloud.com.au/tassweb/api/?method=editPOLine&appcode=DEMOOE&company=10&v=2&token=BJVvYXC0We4Dtvp6Q49RqhBeAi6uqpTQ9t%2FKI9ZAFpCMeVXIFlDU5yNQIeYME%2BYLXgYA69RTUjXjLeVBetN6CaFMdPCKMWBXD%2Bkkt0%2Fuht0suYrSDONP6mx%2Fbt4WGgNOD5YoIYRNiIVDw2Qn2Oi5YodaEUgtGJohUJMzy3tqsX%2BraZk3j7d77okDCjb7MeFJ0DcupqUoRiGjE39415HTfPgNc6R6BY9wt7SJsj4yOPBrIxHQVS8Yy6gZ3nZgsJ5rhcdkB6eCI6b3FJ31s6vsVcbVu5NBY8AF1qqjWLMazduISzEBwRDsofXfJjo1KLX59R410bmbrF5Z7QZfEfE%2FlettTWOyb4EgdhBoC3v0aLOfF6Bt12AFXDo2VGbgryceeOLAscp%2FFr9ttH42hClBtWsxFU1N5dDENUsVHOwWcfCxd7aTtc0xjvaEYJWcZrRRZa1yrIvgeWaDk0LVxM5ePcT%2BltdrymgmxmZYgxdiYC1qQDcNXDx9hN7yKeZDUztwGA0yl2iXW8aBXAy5hRnztR0TrREyOba26mUHxUJO7tfpIyOrpPbE0nR18vtCZ%2BinbvyqN9adpZhQPByG2XD9M6MoYdmBCc3Duv9qb%2BIa0A8%3D
	```
	
* **Sample POST:**

	```HTML
	<form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
		 <input type="hidden" name="method" value="editPOLine">
		 <input type="hidden" name="appcode" value="DEMOOE">
		 <input type="hidden" name="company" value="10">
		 <input type="hidden" name="v" value="2">
		 <textarea name="token">BJVvYXC0We4Dtvp6Q49RqhBeAi6uqpTQ9t/KI9ZAFpCMeVXIFlDU5yNQIeYME+YLXgYA69RTUjXjLeVBetN6CaFMdPCKMWBXD+kkt0/uht0suYrSDONP6mx/bt4WGgNOD5YoIYRNiIVDw2Qn2Oi5YodaEUgtGJohUJMzy3tqsX+raZk3j7d77okDCjb7MeFJ0DcupqUoRiGjE39415HTfPgNc6R6BY9wt7SJsj4yOPBrIxHQVS8Yy6gZ3nZgsJ5rhcdkB6eCI6b3FJ31s6vsVcbVu5NBY8AF1qqjWLMazduISzEBwRDsofXfJjo1KLX59R410bmbrF5Z7QZfEfE/lettTWOyb4EgdhBoC3v0aLOfF6Bt12AFXDo2VGbgryceeOLAscp/Fr9ttH42hClBtWsxFU1N5dDENUsVHOwWcfCxd7aTtc0xjvaEYJWcZrRRZa1yrIvgeWaDk0LVxM5ePcT+ltdrymgmxmZYgxdiYC1qQDcNXDx9hN7yKeZDUztwGA0yl2iXW8aBXAy5hRnztR0TrREyOba26mUHxUJO7tfpIyOrpPbE0nR18vtCZ+inbvyqN9adpZhQPByG2XD9M6MoYdmBCc3Duv9qb+Ia0A8=</textarea>
	</form>
	```