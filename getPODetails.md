**getPODetails**
----
  Returns a structured purchase order data comprising po number, status index, po printed flag, supplier code, abn, term code and description, structured address details, po date, due date, authority, deliver to, structured deliver to address details, requisition number, contact, entered by and on, comment, structured ud fields, and array of po lines in JSON format.

* **Version History:**

    TASS v49.1 - Method Added

* **Version:**

  2

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
   
   `ponum [integer]` - Purchase order number. Must be a number.

   **Optional:**

   none

   **Conditional:**

   none

* **Success Response:**

    ```javascript
    {
      "purchaseorder": {
        "deliver_to_address": {
          "addr3_text": "Toowoomba",
          "country_text": "",
          "city_text": "QLD 4350",
          "post_code": "",
          "addr_name": "Alpha School Oval",
          "addr1_text": "Cnr Webster & James Streets",
          "addr2_text": "(side entrance)",
          "state_code": "",
          "country_code": ""
        },
        "terms_desc": "Payment due within 21 days",
        "contact": "",
        "due_date": "31/08/2017",
        "term_code": 21,
        "status_index": "P",
        "comment": "",
        "authority": "",
        "entered_by": "ale",
        "ud": {
          "pur1_desc": "Budget Checked",
          "pur4_desc": "Location",
          "pur4_text": "Brisbane",
          "pur2_desc": "Policy Followed",
          "pur1_flg": "",
          "pur2_flg": "Y"
        },
        "po_number": 404,
        "deliver_to": "OVA",
        "polines": [
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
            "unit_tax": 0.4082,
            "tax_code": "AO",
            "supplier_reference": ""
          },
          {
            "outstanding_quantity": 24,
            "item_reference": "",
            "unit_cost_include_tax": 5.9901,
            "line_total": 179.7,
            "line_number": 2,
            "line_description": "Baseballs",
            "unit_cost_exclude_tax": 5.4455,
            "order_quantity": 30,
            "gl_account": "02-1400-00-00",
            "outstanding_amount": 143.76,
            "po_number": 404,
            "unit_tax": 0.5446,
            "tax_code": "AO",
            "supplier_reference": ""
          }
        ],
        "po_date": "31/08/2017",
        "requisition_no": "",
        "address": {
          "addr3_text": "",
          "name_text2": "",
          "country_text": "",
          "name_text": "Golfing Goodies Shop",
          "city_text": "CAIRNS",
          "post_code": 4322,
          "addr1_text": "8876 Par Avenue",
          "addr2_text": "",
          "state_code": "QLD",
          "country_code": ""
        },
        "entered_on": "31/08/2017",
        "printed_flag": "Y",
        "abn_text": "53 004 085 616",
        "supplier_code": "GOLF02"
      },
      "__tassversion": "01.053.3.000",
      "token": {
        "timestamp": "{ts '2021-01-21 15:56:02'}",
        "ponum": 404
      }
    }
    ```
 
* **Error Response:**

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
    }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?appcode=DEMOAP&v=2&method=GetPODetails&token=pBR1ko0FeNwVPmGE7NTwWA%3D%3D&company=10
  ```
  
* **Sample POST:**

  ```HTML
  <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/tassweb/api/">
     <input type="hidden" name="method" value="GetPODetails">
     <input type="hidden" name="appcode" value="DEMOAP">
     <input type="hidden" name="company" value="10">
     <input type="hidden" name="v" value="2">
     <textarea name="token">pBR1ko0FeNwVPmGE7NTwWA==</textarea>
  </form>
  ```
