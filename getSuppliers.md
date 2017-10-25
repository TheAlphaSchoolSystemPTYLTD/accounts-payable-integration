**getSuppliers**
----
  Returns an array of structured Supplier data in JSON format.

* **Version:**

  2

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Conditional:**
 
   `active [boolean]` - Required if no code, ignored if code provided. 
                        True of false for whether returning active or inactive suppliers.
   
   **Optional:**
   
   `code [string]` - Supplier code

* **Success Response:**

    ```javascript
    {
      "suppliers": [
        {
          "contact_text": "John Adam",
          "usual_acct_desc8": "",
          "usual_acct_desc9": "",
          "pay_type": "EP",
          "name_text": "Brisbane City Council",
          "usual_acct_desc2": "",
          "usual_acct_desc3": "",
          "usual_acct_desc1": "Water, Sewerage & Council Charges",
          "usual_acct_desc6": "",
          "usual_acct_desc7": "",
          "misc_flg": false,
          "usual_acct_desc4": "",
          "usual_acct_desc5": "",
          "withold_tax_ind": false,
          "name_text2": "",
          "hold_code": "NO",
          "post_code": 4000,
          "type_code": "GVT",
          "acct2_percent": "",
          "pu_fax": "",
          "pu_email": "accounts@bccetc.com.au",
          "acct_percent_total": 100,
          "limit_amt": 500000,
          "tkiosk_flg": true,
          "addr3_text": "",
          "setup_date": "17/10/1992",
          "acct7_percent": "",
          "usual_acct_code2": "",
          "usual_acct_code3": "",
          "usual_acct_code4": "",
          "usual_acct_code5": "",
          "usual_acct_code6": "",
          "usual_acct_code7": "",
          "pu_extension": "",
          "usual_acct_code8": "",
          "acct5_percent": "",
          "usual_acct_code9": "",
          "usual_acct_code": "01-2270-00-00",
          "acct9_percent": "",
          "fax_text": "07 3229 2928",
          "tele_text": "07 3229 2929",
          "bank_acct_code": 123131333,
          "extension_text": "",
          "term_code": 28,
          "last_payment_date": "29/02/2016",
          "addr1_text": "81 George",
          "web_address": "",
          "acct1_percent": 100,
          "active_flg": true,
          "bank_bsb_code": "212-444",
          "acct3_percent": "",
          "bank_code": "COM",
          "abn_text": "53 004 085 616",
          "addr2_text": "",
          "acct6_percent": "",
          "pu_phone": "",
          "mobile_text": "",
          "usual_acct_taxcode9": "",
          "available_amt": 499300,
          "country_text": "",
          "last_vouc_date": "01/03/2016",
          "acct4_percent": "",
          "pu_mobile": "",
          "our_acct_code": "alphasc-00-00",
          "city_text": "BRISBANE",
          "e_mail": "",
          "state_code": "QLD",
          "bank_acct_name": "Brisbane City Council",
          "bal_amt": 700,
          "pu_contact": "",
          "usual_acct_taxcode4": "",
          "usual_acct_taxcode3": "",
          "acct8_percent": "",
          "usual_acct_taxcode2": "",
          "last_debit_date": "24/10/2007",
          "last_po_date": "24/08/2005",
          "usual_acct_taxcode1": "AO",
          "usual_acct_taxcode8": "",
          "tax_code": "AO",
          "usual_acct_taxcode7": "",
          "usual_acct_taxcode6": "",
          "vend_code": "BCC",
          "usual_acct_taxcode5": ""
        }
      ]
    }
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
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/api/">
       <input type="hidden" name="method" value="getSuppliers">
       <input type="hidden" name="appcode" value="DEMOAP">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="2">
       <textarea name="token">SCpxAeg8YeBS20KW+jr+qGxFcFUU2xGwW8DZkaR21m4=</textarea>
    </form>
  ```
