Sign in steps
=================

Register at our website to get the following credentials:
* Client code
* Client secret

Step 1: Sign in to generate access token
----------------------------------------------
Recommendation: Use postman to test your API first. If the test is successful, use postman's code snippet in your program. This helps you identify if there is a connection issue.
* URL: https://example.com/weatherAPI/login
* Method: POST
* Request headers:

  * ClientCode: <value>
  * ClientSecret: <value>
  * Format: JSON
  * Mobile: <enter your phone number along with country code>

* Request body: 
  
  * grantType: password 
  * userName: <enter your username>
  * password: <enter your password>

* Response: It can be either of the following:
  
  * Success

    +--------+--------------------------+
    | Status | Description              |
    +--------+--------------------------+
    | 200    | Access token is: <token> |
    +--------+--------------------------+

  * Error
  
    +--------+------------+-----------------------+
    | Status | Error code | Description           |
    +--------+------------+-----------------------+
    | 400    | 1011       | Invalid URL           |
    +--------+------------+-----------------------+
    | 400    | 1012       | Invalid username      |
    +--------+------------+-----------------------+
    | 400    | 1013       | Invalid password      |
    +--------+------------+-----------------------+
    | 403    | 2011       | Invalid client secret |
    +--------+------------+-----------------------+

Step 2: Generate One time password
-----------------------------------------
In this step, we will verify your mobile number using one-time password. This request sends a one-time password on your mobile and your registered email address.

Note: The access token must be converted to Bearer token first to comply with Outh 2.0 authentication standards.

* URL: https://example.com/weatherAPI/2fa
* Method: POST
* Request headers:
  
  * ClientCode: <value>
  * ClientSecret: <value>
  * Format: JSON
  * Mobile: <enter your phone number along with country code>

* Request body: 

  * AccessToken: Bearer <Value>

* Response: It can be either of the following:

  * Success

    +--------+--------------------------+
    | Status | Description              |
    +--------+--------------------------+
    | 200    | OTP is: <6 digit OTP>    |
    +--------+--------------------------+

  * Error

    +--------+------------+-----------------------+
    | Status | Error code | Description           |
    +--------+------------+-----------------------+
    | 400    | 1011       | Invalid URL           |
    +--------+------------+-----------------------+
    | 400    | 1012       | Invalid ClientCode    |
    +--------+------------+-----------------------+
    | 400    | 1013       | Invalid password      |
    +--------+------------+-----------------------+
    | 403    | 2011       | Invalid access token  |
    +--------+------------+-----------------------+

Step 2: Generate authentication token
-----------------------------------------
In this step, we will generate the authentication token. All transactions of our service authenticates you using this token.

* URL: https://example.com/weatherAPI/authenticationToken
* Method: POST
* Request headers:

  * ClientCode: <value>
  * ClientSecret: <value>
  * Format: JSON
  * Mobile: <enter your phone number along with country code>

* Request body: 

  * OTP: <Value>

* Response: It can be either of the following:

  * Success

+--------+------------------------------+
| Status | Description                  |
+--------+------------------------------+
| 200    | authentication token <value> |
+--------+------------------------------+

  * Error

+--------+------------+-----------------------+
| Status | Error code | Description           |
+--------+------------+-----------------------+
| 400    | 1011       | Invalid URL           |
+--------+------------+-----------------------+
| 400    | 1012       | Invalid ClientCode    |
+--------+------------+-----------------------+
| 400    | 1013       | Invalid ClientSecret  |
+--------+------------+-----------------------+
| 403    | 2011       | Invalid OTP           |
+--------+------------+-----------------------+

