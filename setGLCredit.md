**setGLCredit**
----
	Returns "Success" if the crdit successfully created, or a structure of invalid validations "__invalid" if the credit is unsuccessfully created.

* **Version:**

	2

* **Version History:**

    TASS v51.4.095 - Added support for URL Encoded value for the attachment_file field. (Recommended)

* **Method:**

	GET | POST
	
*  **Params:**

	**Required:**

 `supplier_code  [string]` - Supplier Code

 `credit_number [string]` - Credit Number

 `credit_date [string]` - Credit Date 

 `credit_amount [decimal]` - Credit Amount

 `comment_1 [string]` - Comment 1

 `gldistributions [array]` - Array of GL Distributions

 for each gldistributions these fields are required

`id [string]` - Unique Identity of GL Distribution

`account_code [string]` - GL Account of GL Distribution

`desc_text [string]` - Description Text of GL Distribution

`dist_amount [decimal]` - Distribution Amount of GL Distribution

`tax_amount [decimal]` - Tax Amount of GL Distribution

`tax_code [string]` - Tax Code of GL Distribution
 
**Optional**

`year [integer]` - Year

`period [interger]` - Period

`comment_2 [string]` - Comment 2

`auto_apply_credit [boolean]` - default 'N', where set to Y credit will be applied to the oldest unpaid invoice for the supplier first. 

**Conditional**

`attachment_file [string]` - Base64 Encoded PDF File. 

`attachment_file_name [string]` - Name of PDF attachment. Length must be between 1 and 255 Characters. 

`external_url [string]`  - External Link location

`external_target [string]` - External Link title. Length must be between 1 and 50 characters.

* **Success Response:**
```javascript
{
  "success": "Credit created successfully.",
  "__tassversion": "01.000.043.0",
  "token": {
    "given_name": "Chit HOI",
    "credit_amount": 100,
    "sex": "M",
    "application_id": "TESTEST1556",
    "comment_1": "comment 123",
    "par_surname": "Namu-Sleeth",
    "credit_date": "2025-01-20",
    "stud_surname": "HSU",
    "f_p2_sex": "M",
    "entry_ygrp": 8,
    "credit_number": 98766,
    "batch_num": 612345684,
    "preferred_name": "Mr B Te Namu-Sleeth & Miss D Galvin",
    "dob": "1995-09-23",
    "par_name": "Mr Namu-Sleeth and this is bigger than 30 characters",
    "f_name": "Miss D Galvin",
    "boarder": "N",
    "doa": "2019-09-29",
    "m_p1_sex": "M",
    "timestamp": "{ts '2025-01-28 13:07:30'}",
    "m_name": "Mr B Te Namu-Sleeth",
    "entry_yr": 2024,
    "supplier_code": "00012"
  }
 }
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

	`credit_number` not unique
	```javascript
	__invalid: {
		"credit_number": "Credit Number already used."
	}
	```

	`credit_number` exceed 20 characters
	```javascript
	__invalid: {
		"credit_number": "Value exceeds 20 characters."
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

	`credit_number` less than or equal 0.00
	```javascript
	__invalid: {
		"credit_amount": "Credit Amount is invalid."
	}
	```

	`credit_number` has more than 2 decimal points
	```javascript
	__invalid: {
		"credit_amount": "Value has more than 2 decimal points."
	}
	```

	`credit_number` greater than Available Credit from "vendor" table 
	```javascript
	__invalid: {
		"credit_amount": "Credit Amount exceeds Credit Limit."
	}
	```

	`term_code` not a valid term code in "terms" table when supplied 
	```javascript
	__invalid: {
		"term_code": "Term Code is invalid."
	}
	```

	`due_date` less than `credit_date` when supplied 
	```javascript
	__invalid: {
		"due_date": "Due Date is less than credit Date."
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

	`attachment_file_name` length greater than 255 characters
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

	`external_url` not supplied where `external_target` is supplied
    ```javascript
    __invalid: {
      "external_url": "external_url field is required where 'external_target' is supplied."
    }
    ```

    `external_target` not supplied where `external_url` is supplied
    ```javascript
    __invalid: {
      "external_target": "external_target field is required where 'external_url' is supplied."
    }
    ```

    `external_target` length greater than 50 characters
    ```javascript
    __invalid: {
      "external_target": "external_target must be between 1 and 50 characters."
    }
    ```
	
* **Sample Parameters:**

```javascript
	{
    "application_id": "TESTEST1556",
    "stud_surname": "HSU",
    "given_name": "Chit HOI",
    "preferred_name": "Mr B Te Namu-Sleeth & Miss D Galvin",
    "dob": "1995-09-23",
    "sex": "M",
    "entry_yr": "2024",
    "entry_ygrp": 8,
    "boarder": "N",
    "doa": "2019-09-29",
    "credit_number": "98766",
    "credit_amount": "100.00", 
    "supplier_code": "00012",
    "credit_date": "2025-01-20",
    "comment_1": "comment 123"
    "par_surname": "Namu-Sleeth",
    "par_name": "Mr Namu-Sleeth and this is bigger than 30 characters",
    "m_name": "Mr B Te Namu-Sleeth",
    "f_name": "Miss D Galvin",
    "m_p1_sex": "M",
    "f_p2_sex": "M",
    "batch_num": "612345684"
}
```

* **Sample GET:** (With URL Encoded `token`)

```HTML
https://local.tassweb.net.au/tassweb/api/?method=setEnrolment&appcode=API04&company=10&v=3&token=JpMolK60d04X3gXkWi7E6KioctgGHlFoHtJdoUm%2bc1sJmWBz8jyjxSf1aSYZgY96Jm9pgQ3N4VQcVimTvaORwf80g1nt9tlDDvGrYPCTnrUVe4ZdTq5P%2bgzB4sv7eXHINcYEpHNNHd7ZHI%2f4etfuBeCVx7xxM%2flNvt7Ffjf4JsScyUPV8TOtw6KeAqmlYzPEY%2fyxwyuJhcpC1hD6U7HLnH%2byvTwB79WyNKeT9Yh0a33H2kp0vO4Buz710%2fwuMAyxGCTObTU3zBgy2AI1kmgTASgyUDtMP3lVqK0EDXVAOlC1Lb02BosI8aBZ09HtqtPHgs7j3SJQD3ugyPBnww8ZFyz00dA4uOMKKGTY3G%2b8tvNrpLAEUKO92aFhFsDetqq4MjyNVCcIlk1lDjNu9s5B2mVrYuQ1k9IohatN%2bjt6x4LBZ4jrGb3c%2foax%2fVWbIK63dIHk4xnMQ1y5VG5dQaLEIKezoYLzQJ2TYvrFERWx9OLT6ML5oLUJVzfCYbOJIA%2bmzV1ltf6pzQMObvqMttCib1IScHI8p9TxJ%2fGN4ZDj9g6Vjah0FQV6gCyaOND4MLhKLAku166uVqqeG%2f9pky1fthpLvPELzTwaf%2fRWu4KDxYK3NmsTSlxi2V%2bcv7pCYVdkXNzg3GEtrxKc2ZtqDop1V9ajou%2fcQeTlq3y7PxMWe2aju4s3sT9aYMnEsqhAp0Txa4oNy4EQJ15vtKxsf41D2w%3d%3d
```

**Sample POST:**

	```HTML
	<form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
		 <input type="hidden" name="method" value="setGLCredit">
		 <input type="hidden" name="appcode" value="DEMOAP">
		 <input type="hidden" name="company" value="10">
		 <input type="hidden" name="v" value="2">
		 <textarea name="token">BJVvYXC0We4Dtvp6Q49RqhBeAi6uqpTQ9t/KI9ZAFpCMeVXIFlDU5yNQIeYME+YLXgYA69RTUjXjLeVBetN6CaFMdPCKMWBXD+kkt0/uht0suYrSDONP6mx/bt4WGgNOD5YoIYRNiIVDw2Qn2Oi5YodaEUgtGJohUJMzy3tqsX+raZk3j7d77okDCjb7MeFJ0DcupqUoRiGjE39415HTfPgNc6R6BY9wt7SJsj4yOPBrIxHQVS8Yy6gZ3nZgsJ5rhcdkB6eCI6b3FJ31s6vsVcbVu5NBY8AF1qqjWLMazduISzEBwRDsofXfJjo1KLX59R410bmbrF5Z7QZfEfE/lettTWOyb4EgdhBoC3v0aLOfF6Bt12AFXDo2VGbgryceeOLAscp/Fr9ttH42hClBtWsxFU1N5dDENUsVHOwWcfCxd7aTtc0xjvaEYJWcZrRRZa1yrIvgeWaDk0LVxM5ePcT+ltdrymgmxmZYgxdiYC1qQDcNXDx9hN7yKeZDUztwGA0yl2iXW8aBXAy5hRnztR0TrREyOba26mUHxUJO7tfpIyOrpPbE0nR18vtCZ+inbvyqN9adpZhQPByG2XD9M6MoYdmBCc3Duv9qb+Ia0A8=</textarea>
	</form>
```
