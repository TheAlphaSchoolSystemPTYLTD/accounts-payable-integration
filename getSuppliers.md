**getSuppliers**
----
  Returns an array of structured Supplier data in JSON format.

* **Version:**

  2

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**

   none
   
   **Optional:**
   
   none

   **Conditional:**

   `code [string]` - Supplier code

   `search [string]` - Text search for supplier code or supplier name or ABN
 
   `active [boolean]` - Required if no code, ignored if code provided. 
                        True of false for whether returning active or inactive suppliers.

* **Success Response:**

    ```javascript
    "suppliers": [
      {
        // Default GL Distribution Account 1
        "acct1_percent": 100,
        "usual_acct_code": "01-2270-00-00",
        "usual_acct_desc1": "Water, Sewerage & Council Charges",
        "usual_acct_taxcode1": "AO",
        
        // Default GL Distribution Account 2
        "acct2_percent": "",
        "usual_acct_code2": "",
        "usual_acct_desc2": "",
        "usual_acct_taxcode2": "",
        
        // Default GL Distribution Account 3
        "acct3_percent": "",
        "usual_acct_code3": "",
        "usual_acct_desc3": "",
        "usual_acct_taxcode3": "",
        
        // Default GL Distribution Account 4
        "acct4_percent": "",
        "usual_acct_code4": "",
        "usual_acct_desc4": "",
        "usual_acct_taxcode4": "",
        
        // Default GL Distribution Account 5
        "acct5_percent": "",
        "usual_acct_code5": "",
        "usual_acct_desc5": "",
        "usual_acct_taxcode5": "",
        
        // Default GL Distribution Account 6
        "acct6_percent": "",
        "usual_acct_code6": "",
        "usual_acct_desc6": "",
        "usual_acct_taxcode6": "",
        
        // Default GL Distribution Account 7
        "acct7_percent": "",
        "usual_acct_code7": "",
        "usual_acct_desc7": "",
        "usual_acct_taxcode7": "",
        
        // Default GL Distribution Account 8
        "acct8_percent": "",
        "usual_acct_code8": "",
        "usual_acct_desc8": "",
        "usual_acct_taxcode8": "",
        
        // Default GL Distribution Account 9
        "acct9_percent": "",
        "usual_acct_code9": "",
        "usual_acct_desc9": "",
        "usual_acct_taxcode9": "",
        
        // Total percentage of Default GL Distribution Accounts (<= 100)
        "acct_percent_total": 100,
        
        "contact_text": "John Adam",
        "pay_type": "EP",
        "name_text": "Brisbane City Council",
        "misc_flg": false,
        "withold_tax_ind": false,
        "name_text2": "",
        "hold_code": "NO",
        "post_code": 4000,
        "type_code": "GVT",
        "pu_fax": "",
        "pu_email": "accounts@bccetc.com.au",
        "limit_amt": 500000,
        "tkiosk_flg": true,
        "addr3_text": "",
        "setup_date": "17/10/1992",
        "pu_extension": "",
        "fax_text": "07 3229 2928",
        "tele_text": "07 3229 2929",
        "bank_acct_code": 123131333,
        "extension_text": "",
        "term_code": 28,
        "last_payment_date": "29/02/2016",
        "addr1_text": "81 George",
        "web_address": "",
        "active_flg": true,
        "bank_bsb_code": "212-444",
        "bank_code": "COM",
        "abn_text": "53 004 085 616",
        "addr2_text": "",
        "pu_phone": "",
        "mobile_text": "",
        "available_amt": 499300,
        "country_text": "",
        "last_vouc_date": "01/03/2016",
        "pu_mobile": "",
        "our_acct_code": "alphasc-00-00",
        "city_text": "BRISBANE",
        "e_mail": "",
        "state_code": "QLD",
        "bank_acct_name": "Brisbane City Council",
        "bal_amt": 700,
        "pu_contact": "",
        "last_debit_date": "24/10/2007",
        "last_po_date": "24/08/2005",
        "tax_code": "AO",
        "vend_code": "BCC"
      }
    ]
    ```
 
* **Error Response:**

    `active` not supplied
    ```javascript
    __invalid: {
      "active": "field is required"
    }
    ```
    
    `active` not a valid boolean
    ```javascript
    __invalid: {
      "active": "Value is not a valid boolean."
    }
    ```
    
* **Sample Parameters:**

  ```javascript
    { 
      "active":"true"
    }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=GetSuppliers&appcode=DEMOAP&company=10&v=2&token=SCpxAeg8YeBS20KW%2Bjr%2BqGxFcFUU2xGwW8DZkaR21m4%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getSuppliers">
       <input type="hidden" name="appcode" value="DEMOAP">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="2">
       <textarea name="token">SCpxAeg8YeBS20KW+jr+qGxFcFUU2xGwW8DZkaR21m4=</textarea>
    </form>
  ```
