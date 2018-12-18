**getCOA**
----
  Returns an array of structured general ledger account data comprising account code, account description, account type, tax code, start year number, end year number, start period number, end period number, account responsibility data and account annual budget data in JSON format.

* **Version:**

  2

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
   `date [date dd/mm/yyyy]`

   **Optional:**

   `responsibility [string]` - valid options are "All", "Approvers" and "Raisers". Used to return account responsibility data.

   `year [integer]` - used to return account annual budget data

   **Conditional:**

   `start_num [integer]` - `start_num` required if `flex_code` supplied

   `flex_code [string]` - `flex_code` required if `start_num` supplied

* **Success Response:**

    ```javascript
    "accounts": [
      {
        "end_year_num": 2099,
        "budget1_title": "Board Approved",
        "desc_text": "Gross Tuition Fees",
        "start_period_num": 1,
        "budget1_amt": 0,
        "budget2_title": "Revised",
        "end_period_num": 12,
        "budget3_amt": 0,
        "def_tax_code": "EX",
        "type_ind": "I",
        "start_year_num": 1992,
        "budget3_title": "Half Year Reviewed",
        "responsibilities": [
          {
            "initials": "",
            "limit_amount": 100000,
            "surname": "",
            "salutation": "",
            "responsibility_level": 3,
            "preferred_name": "",
            "email": "",
            "given_names": ""
          }
        ],
        "acct_code": "01-0110-00-00",
        "budget2_amt": 0
        }
    ]
    ```
 
* **Error Response:**

    `start_num` not supplied when `flex_code` supplied
    ```javascript
    __invalid: {
      "start_num": "field is required"
    }
    ```

    `start_num` not a valid integer
    ```javascript
    __invalid: {
      "start_num": "Value is not a valid integer."
    }
    ```

    `start_num` not greater than 0
    ```javascript
    __invalid: {
      "start_num": "start_num must be greater than 0"
    }
    ```

    `flex_code` not supplied when `start_num` supplied
    ```javascript
    __invalid: {
      "flex_code": "field is required"
    }
    ```

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

    `responsibility` not a valid responsibility
    ```javascript
    __invalid: {
      "responsibility": "Value is not a valid responsibility."
    }
    ```

    `year` not a valid number
    ```javascript
    __invalid: {
      "year": "Value is not a valid number."
    }
    
* **Sample Parameters:**

  ```javascript
    { 
      "date":"01/01/2018"
      ,"responsibility":"Approvers"
      ,"year":"2018"
    }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=GetCOA&appcode=DEMOAP&company=10&v=2&token=IBzPtFbCrfnUtDJ3HQCN1rog9756syITU5czlRz1pog%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getCOA">
       <input type="hidden" name="appcode" value="DEMOAP">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="2">
       <textarea name="token">IBzPtFbCrfnUtDJ3HQCN1rog9756syITU5czlRz1pog=</textarea>
    </form>
  ```
