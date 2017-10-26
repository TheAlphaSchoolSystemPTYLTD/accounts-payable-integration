**getSegments**
----
  Returns an array of structured segment data comprising segment start position, segment name, segment code and segment description in JSON format.

* **Version:**

  2

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
   `startnum [integer or "all"]` - Start position. Must be a number or "all".

   **Optional:**

   none

   **Conditional:**

   none

* **Success Response:**

    ```javascript
    "segments": [
      {
        "desc_text": "School Section",
        "segment_codes": {
          "1": {
            "flex_code": "00",
            "desc_text": "Default"
          },
          "2": {
            "flex_code": "01",
            "desc_text": "Junior School"
          },
          "3": {
            "flex_code": "02",
            "desc_text": "Senior School"
          }
        },
        "start_num": 1
      },
      {
        "desc_text": "Department",
        "segment_codes": {
          "1": {
            "flex_code": "00",
            "desc_text": "Default"
          },
          "2": {
            "flex_code": 10,
            "desc_text": "English Dept"
          },
          "3": {
            "flex_code": 20,
            "desc_text": "Science Dept"
          },
          "4": {
            "flex_code": 30,
            "desc_text": "Languages Dept"
          },
          "5": {
            "flex_code": 40,
            "desc_text": "Humanities"
          },
          "6": {
            "flex_code": 50,
            "desc_text": "IT Dept"
          }
        },
        "start_num": 9
      }
    ]
    ```
 
* **Error Response:**

    `startnum` not supplied
    ```javascript
    __invalid: {
      "start_num": "field is required"
    }
    ```
    
    `startnum` not a valid number or "all"
    ```javascript
    __invalid: {
      "start_num": "startnum must be number or 'all'"
    }
    ```
    
* **Sample Parameters:**

  ```javascript
    { 
      "start_num":"all"
    }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=GetSegments&appcode=DEMOAP&company=10&v=2&token=8M2qTSqRPRZRFr%2FbgarkWB3zIJ2HCh2EfjBqFQZd6%2B0%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/api/">
       <input type="hidden" name="method" value="getSegments">
       <input type="hidden" name="appcode" value="DEMOAP">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="2">
       <textarea name="token">8M2qTSqRPRZRFr/bgarkWB3zIJ2HCh2EfjBqFQZd6+0=</textarea>
    </form>
  ```
