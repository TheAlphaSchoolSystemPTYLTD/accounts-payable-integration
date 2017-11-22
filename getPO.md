**getPO**
----
  Returns an array of structured purchase order data comprising PO number, line number, GL account, line description, outstanding quantity, tax code, line total, unit tax, unit cost excluding tax, and unit cost including tax in JSON format.

* **Version:**

  2

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
   `ponum [integer]` - Purchase order number. Must be a number.
   
   `code [string]` - Supplier code

   **Optional:**

   none

   **Conditional:**

   none

* **Success Response:**

    ```javascript
    "purchaseorders": [
      {
        "outstanding_quantity": 28,
        "po_number": 404,
        "item_reference": "",
        "unit_cost_include_tax": 4.49,
        "line_total": 134.7,
        "unit_tax": 0.4082,
        "line_number": 1,
        "line_description": "Line 1 details go here",
        "unit_cost_exclude_tax": 4.0818,
        "gl_account": "02-1400-00-00",
        "tax_code": "AO",
        "supplier_reference": ""
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
    
    `ponum` not supplied
    ```javascript
    __invalid: {
      "ponum": "field is required"
    }
    ```
    
    `ponum` not a valid number
    ```javascript
    __invalid: {
      "ponum": "Value is not a valid number."
    }
    ```
    
* **Sample Parameters:**

  ```javascript
    { 
      "ponum":"404"
      ,"code":"GOLF02"
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
