**getPO**
----
  Returns an array of structured purchase order data comprising PO number, line number, GL account, line description, outstanding quantity, tax code, line total, unit tax, unit cost excluding tax, unit cost including tax, array of approvers and structure of the raiser in JSON format.

* **Version History:**

    TASS v50.1 - Returned `requisition_approvers` and `requisition_raiser` as well as added `status` parameter

    TASS v49.7 - Returned `authority` and `entered_by`

    TASS v49.1 - Added more details including `order_quantity` and `outstanding_amount`

    TASS v48.0 - Method Added

* **Version:**

  2

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
   
   `code [string]` - Supplier code

   **Optional:**

   `ponum [integer]` - Purchase order number. Must be a number.

   `status [string]` - Status of Purchase Order. Must be "All" or "Incomplete".

   **Conditional:**

   none

* **Success Response:**

    ```javascript
    "purchaseorders": [
      {
        "outstanding_quantity": 27,
        "item_reference": "",
        "unit_cost_include_tax": 4.49,
        "line_total": 134.7,
        "line_number": 1,
        "line_description": "Medicine Balls",
        "unit_cost_exclude_tax": 4.0818,
        "order_quantity": 30,
        "gl_account": "02-1400-00-00",
        "outstanding_amount": 121.23,
        "po_number": 404,
        "entered_by": "peterr",
        "unit_tax": 0.4082,
        "tax_code": "AO",
        "supplier_reference": "",
        "authority": "AJ",
        "requisition_approvers": [
          {
            "initials": "A",
            "surname": "O'Johnstonex",
            "salutation": "Mr",
            "responsibility_level": 3,
            "preferred_name": "Alanx",
            "email": "aj@tassweb.com.au",
            "given_names": "Alan Pierre"
          }
        ],
         "requisition_raiser": {
            "initials": "G",
            "surname": "Battersby",
            "salutation": "Mrs",
            "preferred_name": "Gwenith",
            "email": "gb@tassweb.com.au",
            "given_names": "Gwenderlain Peta"
        }
      }
    ]
    ```
 
* **Error Response:**

    `code` not supplied
    ```javascript
    __invalid: {
      "code": "field is required"
    }
    ```
    
    `ponum` not a valid number
    ```javascript
    __invalid: {
      "ponum": "Value is not a valid number."
    }
    ```

    `status` not a valid status
    ```javascript
    __invalid: {
      "status": "Value is not a valid status."
    }
    ```
    
* **Sample Parameters:**

  ```javascript
    { 
      "ponum":"404"
      ,"code":"GOLF02"
      ,"status":"Incomplete"
    }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=GetPO&appcode=DEMOAP&company=10&v=2&token=2D%2FZvGOLAyAI7UBjQqfgIpucGdi0%2B7CMOf0uBMLsPPQ%3D
  ```
  
* **Sample POST:**

  ```HTML
  <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/tassweb/api/">
     <input type="hidden" name="method" value="getPO">
     <input type="hidden" name="appcode" value="DEMOAP">
     <input type="hidden" name="company" value="10">
     <input type="hidden" name="v" value="2">
     <textarea name="token">2D/ZvGOLAyAI7UBjQqfgIpucGdi0+7CMOf0uBMLsPPQ=</textarea>
  </form>
  ```
