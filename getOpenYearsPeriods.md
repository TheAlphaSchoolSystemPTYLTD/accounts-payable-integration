**getOpenYearsPeriods**
----
  Returns an array of structured periods data comprising year and period in JSON format.

* **Version:**

  2

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
   `ap [boolean]` - Must be true.

   **Optional:**

   none

   **Conditional:**

   none

* **Success Response:**

    ```javascript
    "openyearsperiods": [
      {
        "year": 2017,
        "period": 1
      },
      {
        "year": 2017,
        "period": 2
      },
      {
        "year": 2017,
        "period": 3
      },
      {
        "year": 2017,
        "period": 4
      },
      {
        "year": 2017,
        "period": 5
      },
      {
        "year": 2017,
        "period": 6
      }
    ]
    ```
 
* **Error Response:**

    `ap` not supplied
    ```javascript
    __invalid: {
      "ap": "field is required"
    }
    ```
    
    `ap` not a valid boolean
    ```javascript
    __invalid: {
      "ap": "Value is not a valid boolean."
    }
    ```
    
    `ap` not true
    ```javascript
    __invalid: {
      "ap": "ap must be true"
    }
    ```
    
* **Sample Parameters:**

  ```javascript
    { 
      "ap":"true"
    }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=GetOpenYearsPeriods&appcode=DEMOAP&company=10&v=2&token=XSupOb2KjEdcEwuunl4Q0A%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/api/">
       <input type="hidden" name="method" value="getOpenYearsPeriods">
       <input type="hidden" name="appcode" value="DEMOAP">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="2">
       <textarea name="token">XSupOb2KjEdcEwuunl4Q0A==</textarea>
    </form>
  ```
