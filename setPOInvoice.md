**setPOInvoice**
----
  Returns "Success" and document number "vouch_code" if the invoice successfully created, or a structure of invalid validations "__invalid" if the invoice is unsuccessfully created.

* **Version:**

  2

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
   `supplier_code [string]` - Supplier Code

   `invoice_number [string]` - Invoice Number

   `invoice_date [date dd/mm/yyyy]` - Invoice Date

   `invoice_amount [decimal]` - Invoice Amount

   `id [string]` - Unique Identity of PO Line

   `ponum [number]` - PO Number of PO Line

   `linenum [number]` - Line Number of PO Line

   `quantity [decimal]` - Quantity of PO Line

   **Optional:**
   
   `year [integer]` - Year

   `period [integer]` - Period

   `term_code [string]` - Term Code

   `due_date [date dd/mm/yyyy]` - Due Date 

   `hold_code [string]` - Hold Payment Code

   `comment_1 [string]` - Comment 1

   `comment_2 [string]` - Comment 2

   `polines [array]` - Array of PO Lines

   **Conditional:**

   none

* **Success Response:**

    ```javascript
    "success": "Invoice created successfully.",
    "vouch_code": 673
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

    Number `[field_name]` not a valid number
    ```javascript
    __invalid: {
      "[field_name]": "Value is not a valid number."
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

    `invoice_number` not unique
    ```javascript
    __invalid: {
      "invoice_number": "Invoice Number already used."
    }
    ```

    `invoice_number` exceed 20 characters
    ```javascript
    __invalid: {
      "invoice_number": "Value exceeds 20 characters."
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

    `invoice_amount` less than or equal 0.00
    ```javascript
    __invalid: {
      "invoice_amount": "Invoice Amount is invalid."
    }
    ```

    `invoice_amount` has more than 2 decimal points
    ```javascript
    __invalid: {
      "invoice_amount": "Value has more than 2 decimal points."
    }
    ```

    `invoice_amount` greater than Available Credit from "vendor" table 
    ```javascript
    __invalid: {
      "invoice_amount": "Invoice Amount exceeds Credit Limit."
    }
    ```

    `term_code` not a valid term code in "terms" table when supplied 
    ```javascript
    __invalid: {
      "term_code": "Term Code is invalid."
    }
    ```

    `due_date` less than `invoice_date` when supplied 
    ```javascript
    __invalid: {
      "due_date": "Due Date is less than Invoice Date."
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

    `ponum` not a valid PO Number
    ```javascript
    __invalid: {
      "ponum": "PO Number is invalid."
    }
    ```

    `ponum` not a valid PO Number for that Supplier Code
    ```javascript
    __invalid: {
      "ponum": "PO Number does not match Supplier Code."
    }
    ```

    `linenum` not a line number that has an outstanding quantity greater than 0.00 for this `ponum`
    ```javascript
    __invalid: {
      "linenum": "Line Number is invalid."
    }
    ```

    `quantity` less than or equal 0.00
    ```javascript
    __invalid: {
      "quantity": "Quantity is invalid."
    }
    ```

    `quantity` has more than 2 decimal points
    ```javascript
    __invalid: {
      "quantity": "Value has more than 2 decimal points."
    }
    ```

    `quantity` greater than Outstanding Quantity for that line
    ```javascript
    __invalid: {
      "quantity": "Quantity exceeds Outstanding Quantity."
    }
    
* **Sample Parameters:**

  ```javascript
  {
    "supplier_code":"GOLF02"
    ,"invoice_number":"testPO1"
    ,"invoice_date":"31/08/2017"
    ,"invoice_amount":"16.47"
    ,"polines":[
      {
        "id":"1"
        ,"ponum":"404"
        ,"linenum":"1"
        ,"quantity":"1"
      },{
        "id":"2"
        ,"ponum":"404"
        ,"linenum":"2"
        ,"quantity":"2"
      }
    ]
  }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=SetPOInvoice&appcode=DEMOAP&company=10&v=2&token=kcUOlOdvmnSHUU%2BjwVtflKZL6G9SGyuymxRhJtXlXlDFwU%2F5Ik%2FXw5ntBA45Hnuikem7iU%2BQ9bha9u3UF73AsaQgJCEsB6Lhsiei2v4MYMbPSL0793g5K3s7XF4vn5CjCAH25YXiwaNet7La1eI91LomNJaLAA52j8ybQTOTe6T0LlW7l4B6%2BKQkgFZJXluQwmkmbZJvqkxUfJ1My%2BaAkL0V5b%2BV%2F2yaOzS2ZAagpDuE%2BU%2BCkVqZZiA5QddaviWa0qh6F9JlOFl7Mwn5QIzlf7%2FzastBaOVIBPPA8NrPOI5xm5A27Qxb4t9nv4HRNHm2JXpG5HnyIiClU5UOd0731SrZ6Cl%2B5N99tDreN7xJgCQ%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/api/">
       <input type="hidden" name="method" value="setPOInvoice">
       <input type="hidden" name="appcode" value="DEMOAP">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="2">
       <textarea name="token">kcUOlOdvmnSHUU+jwVtflKZL6G9SGyuymxRhJtXlXlDFwU/5Ik/Xw5ntBA45Hnuikem7iU+Q9bha9u3UF73AsaQgJCEsB6Lhsiei2v4MYMbPSL0793g5K3s7XF4vn5CjCAH25YXiwaNet7La1eI91LomNJaLAA52j8ybQTOTe6T0LlW7l4B6+KQkgFZJXluQwmkmbZJvqkxUfJ1My+aAkL0V5b+V/2yaOzS2ZAagpDuE+U+CkVqZZiA5QddaviWa0qh6F9JlOFl7Mwn5QIzlf7/zastBaOVIBPPA8NrPOI5xm5A27Qxb4t9nv4HRNHm2JXpG5HnyIiClU5UOd0731SrZ6Cl+5N99tDreN7xJgCQ=</textarea>
    </form>
  ```
