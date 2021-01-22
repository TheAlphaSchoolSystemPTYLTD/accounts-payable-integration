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
    {
      "openyearsperiods": [
        {
          "year": 2020,
          "period": 1
        },
        {
          "year": 2020,
          "period": 2
        },
        {
          "year": 2020,
          "period": 3
        },
        {
          "year": 2020,
          "period": 4
        },
        {
          "year": 2020,
          "period": 5
        },
        {
          "year": 2020,
          "period": 6
        },
        {
          "year": 2020,
          "period": 7
        },
        {
          "year": 2020,
          "period": 8
        },
        {
          "year": 2020,
          "period": 10
        },
        {
          "year": 2020,
          "period": 12
        }
      ],
      "__tassversion": "01.053.3.000",
      "token": {
        "timestamp": "{ts '2021-01-21 15:40:53'}",
        "ap": true
      }
    }
    ```
 
* **Error Response:**

    `ap` is not supplied
    ```javascript
    __invalid: {
      "ap": "field is required"
    }
    ```
    
    `ap` is not a valid boolean
    ```javascript
    __invalid: {
      "ap": "Value is not a valid boolean."
    }
    ```
    
    `ap` is not true
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
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getOpenYearsPeriods">
       <input type="hidden" name="appcode" value="DEMOAP">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="2">
       <textarea name="token">XSupOb2KjEdcEwuunl4Q0A==</textarea>
    </form>
  ```
