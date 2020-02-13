**getDefaultDueDate**
----
  Returns a structured default data comprising term code and due date in JSON format.

* **Version:**

  2

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
   `date [date dd/mm/yyyy]` - Invoice date
   
   `code [string]` - Supplier code

   **Optional:**

   none

   **Conditional:**

   none

* **Success Response:**

    ```javascript
    "default": {
      "due_date": "06/01/2018",
      "term_code": 30
    }
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
    
    `code` not supplied
    ```javascript
    __invalid: {
      "code": "field is required"
    }
    ```
    
* **Sample Parameters:**

  ```javascript
    { 
      "code":"ABCSTAT"
      ,"date":"12/07/2017"
    }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=GetDefaultDueDate&appcode=DEMOAP&company=10&v=2&token=cXfCRZ09VfGuq7JZpaf7fGiKcMyDjRshXtd4MW8eChXMd93etG4yF7yFGt68WFzh
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getDefaultDueDate">
       <input type="hidden" name="appcode" value="DEMOAP">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="2">
       <textarea name="token">cXfCRZ09VfGuq7JZpaf7fGiKcMyDjRshXtd4MW8eChXMd93etG4yF7yFGt68WFzh</textarea>
    </form>
  ```
