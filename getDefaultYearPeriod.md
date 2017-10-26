**getDefaultYearPeriod**
----
  Returns a structured default data comprising year and period in JSON format.

* **Version:**

  2

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
   `date [date dd/mm/yyyy]` - Invoice date

* **Success Response:**

    ```javascript
    "default": {
      "year": 2017,
      "period": 7
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
    
    `date` not in any periods setup
    ```javascript
    __invalid: {
      "date": "No period setup for this date"
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
    http://api.tasscloud.com.au/tassweb/api/?method=GetDefaultYearPeriod&appcode=DEMOAP&company=10&v=2&token=vBBNEWUaSxcPM9fkqaqR66ctlf34IY0T8r%2B1T3xyY%2Fs%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/api/">
       <input type="hidden" name="method" value="getDefaultYearPeriod">
       <input type="hidden" name="appcode" value="DEMOAP">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="2">
       <textarea name="token">vBBNEWUaSxcPM9fkqaqR66ctlf34IY0T8r+1T3xyY/s=</textarea>
    </form>
  ```
