**getPODetails**
----
  Returns a structured purchase order data comprising po number, status index, po printed flag, supplier code, abn, term code and description, structured address details, po date, due date, authority, deliver to, structured deliver to address details, requisition number, contact, entered by and on, comment, structured ud fields, and array of po lines in JSON format.

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
    "purchaseorder": {
      "deliver_to_address": {
        "addr3_text": "BOWEN HILLS QLD 4006",
        "country_text": "",
        "city_text": "",
        "post_code": "",
        "addr_name": "Alpha Demonstration School",
        "addr1_text": "Boarding House",
        "addr2_text": "31 Thompson St",
        "state_code": "",
        "country_code": ""
      },
      "terms_desc": "Payment due within 30 days",
      "contact": "",
      "due_date": "20/03/2013",
      "term_code": 30,
      "status_index": "O",
      "comment": "",
      "authority": "AJ",
      "entered_by": "AJ",
      "ud": {
        "pur3_flg": "Y",
        "pur1_desc": "Budget Checked",
        "pur6_desc": "",
        "pur4_desc": "",
        "pur4_text": "Oval",
        "pur2_desc": "Manager Approval",
        "pur5_desc": "",
        "pur5_text": "Yes",
        "pur1_flg": "Y",
        "pur3_desc": "Process Observed",
        "pur2_flg": "Y",
        "pur6_text": ""
      },
      "po_number": 372,
      "deliver_to": "BRI",
      "polines": [
        {
          "outstanding_quantity": 1,
          "item_reference": "",
          "unit_cost_include_tax": 24.5,
          "line_total": 24.5,
          "line_number": 1,
          "line_description": "Hop Scotch court",
          "unit_cost_exclude_tax": 22.2727,
          "order_quantity": 1,
          "gl_account": "01-0190-00-01",
          "outstanding_amount": 24.5,
          "po_number": 372,
          "unit_tax": 2.2273,
          "tax_code": "TS",
          "supplier_reference": ""
        }
      ],
      "po_date": "20/03/2013",
      "requisition_no": 208,
      "address": {
        "addr3_text": "Next to the Train Station",
        "name_text2": "Supply Specialists",
        "country_text": "AUSTRALIA",
        "name_text": "The ABC Stationers & Office",
        "city_text": "SOUTH BRISBANE",
        "post_code": 4101,
        "addr1_text": "1234 Marshall Road",
        "addr2_text": "Behind JB HiFi & Coles",
        "state_code": "QLD",
        "country_code": "AUS"
      },
      "entered_on": "20/03/2013",
      "printed_flag": "Y",
      "abn_text": "53 004 085 616",
      "supplier_code": "ABCSTAT"
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
      "ponum":"372"
    }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://localhost/tassweb/api/?appcode=DEMOAP&v=2&method=GetPODetails&token=3blF%2FEI%2F8qLtX5ufgUMFzg%3D%3D&company=10
  ```
  
* **Sample POST:**

  ```HTML
  <form id="postForm" name="postForm" method="POST" action="http://localhost/tassweb/tassweb/api/">
     <input type="hidden" name="method" value="GetPODetails">
     <input type="hidden" name="appcode" value="DEMOAP">
     <input type="hidden" name="company" value="10">
     <input type="hidden" name="v" value="2">
     <textarea name="token">3blF\/EI\/8qLtX5ufgUMFzg==</textarea>
  </form>
  ```