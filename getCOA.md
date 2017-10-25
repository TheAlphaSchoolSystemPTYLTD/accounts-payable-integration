**getCOA**
----
  Returns array of structured general ledger account data comprising account code, account description, account type, tax code in JSON format.

* **Version:**

  2

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
   `date [date dd/mm/yyyy]`

* **Success Response:**

    ```javascript
    "accounts": [
      {
        "desc_text": "Gross Tuition Fees",
        "def_tax_code": "EX",
        "type_ind": "I",
        "acct_code": "01-0110-00-00"
      }
    ]
    ```
 
* **Error Response:**

    `date` not supplied
    ```javascript
    __invalid: {
      "date": "field is required"
    }
    ```
    
    `date` not a valid date
    ```javascript
    __invalid: {
      "date": "Value is not a valid date."
    }
    ```
    
* **Sample Parameters:**

  ```javascript
    { 
      "date":"12/7/2017"
    }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=GetCOA&appcode=DEMOAP&company=10&v=2&token=IBzPtFbCrfnUtDJ3HQCN1rog9756syITU5czlRz1pog%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/api/">
       <input type="hidden" name="method" value="getCOA">
       <input type="hidden" name="appcode" value="DEMOAP">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="2">
       <textarea name="token">IBzPtFbCrfnUtDJ3HQCN1rog9756syITU5czlRz1pog=</textarea>
    </form>
  ```
