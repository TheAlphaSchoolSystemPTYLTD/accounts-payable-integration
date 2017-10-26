**getDepartments**
----
  Returns an array of structured department data comprising segment start position and segment name in JSON format.

* **Version:**

  2

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
   `deptconsol [boolean]` - Must be true for returning only departments being able to be consolidated.

   **Optional:**

   none

   **Conditional:**

   none

* **Success Response:**

    ```javascript
    "departments": [
      {
        "desc_text": "School Section",
        "start_num": 1
      },
      {
        "desc_text": "Department",
        "start_num": 9
      }
    ]
    ```
 
* **Error Response:**

    `deptconsol` not supplied
    ```javascript
    __invalid: {
      "deptconsol": "field is required"
    }
    ```
    
    `deptconsol` not a valid boolean
    ```javascript
    __invalid: {
      "deptconsol": "Value is not a valid boolean."
    }
    ```
    
    `deptconsol` not true
    ```javascript
    __invalid: {
      "deptconsol": "deptconsol must be true"
    }
    ```
    
* **Sample Parameters:**

  ```javascript
    { 
      "deptconsol":"true"
    }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=GetDepartments&appcode=DEMOAP&company=10&v=2&token=uU0X%2F4%2Fc9IpFhUBez4c%2FrGqOQil3xny9TGoGSaM%2BVkM%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/api/">
       <input type="hidden" name="method" value="getDepartments">
       <input type="hidden" name="appcode" value="DEMOAP">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="2">
       <textarea name="token">uU0X/4/c9IpFhUBez4c/rGqOQil3xny9TGoGSaM+VkM=</textarea>
    </form>
  ```
