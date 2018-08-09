**getTaxCodes**
----
  Returns an array of structured tax code data comprising tax code, tax description, tax percentage and calculation method in JSON format.

* **Version:**

  2

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
   `ap [boolean]` - Must be true.

   **Optional:**

   `includeall [boolean]` - Return all tax codes.

   **Conditional:**

   none

* **Success Response:**

    ```javascript
    "taxcodes": [
      {
        "desc_text": "Cred. Acquisition - Capital",
        "calc_method_flag": "T",
        "tax_per": 10,
        "tax_code": "AC"
      },
      {
        "desc_text": "Cred. Acquisition - Other",
        "calc_method_flag": "T",
        "tax_per": 10,
        "tax_code": "AO"
      },
      {
        "desc_text": "GST Free",
        "calc_method_flag": "T",
        "tax_per": 0,
        "tax_code": "EX"
      },
      {
        "desc_text": "Withholding Tax",
        "calc_method_flag": "W",
        "tax_per": 0,
        "tax_code": "WHT"
      }
    ]
    ```
 
* **Error Response:**

    `ap` not supplied
    ```javascript
    __invalid: {
      "ap": "field is required"
    }
    ```
    
    `ap` not a valid boolean
    ```javascript
    __invalid: {
      "ap": "Value is not a valid boolean."
    }
    ```
    
    `ap` not true
    ```javascript
    __invalid: {
      "ap": "ap must be true"
    }
    ```

    `includeall` not a valid boolean
    ```javascript
    __invalid: {
      "includeall": "Value is not a valid boolean."
    }
    ```
    
* **Sample Parameters:**

  ```javascript
    { 
      "ap":"true"
    }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=GetTaxCodes&appcode=DEMOAP&company=10&v=2&token=XSupOb2KjEdcEwuunl4Q0A%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getTaxCodes">
       <input type="hidden" name="appcode" value="DEMOAP">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="2">
       <textarea name="token">XSupOb2KjEdcEwuunl4Q0A==</textarea>
    </form>
  ```