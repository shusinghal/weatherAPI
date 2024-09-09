Weather report
================

This service provides temperature for each location. You can search for the past weather report and future predictions up to six months. 

Recommendation: Use postman to test your API first. If the test is successful, use postman's code snippet in your program. This helps you identify if there is a connection issue.

* URL: https://example.com/weatherAPI/v1/temperatureReport
* Method: GET
* Request headers:
  * Authentication token: Use the authentication token from step three of sign in API.
* Request body: 

+-------------+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+
| Key         | Description                        | Comments                                                                                                                          |
+-------------+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+
| latitude    | Standard latitude value            | Data type: float                                                                                                                  |
|             |                                    | Required: Yes                                                                                                                     |
+-------------+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+
| longitude   | Standard longitude value           | Data type: float                                                                                                                  |
|             |                                    | Required: Yes                                                                                                                     |
+-------------+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+
| timeFrame   | Choose a value from the following: | Day: Gives average temperature of the day.                                                                                        |
|             | * Day                              | Week: Gives average temperature of all days of a week.                                                                            |
|             | * Week                             | Month: Gives average temperature of all days of a month.                                                                          |
|             | * Month                            | Hour: Gives average temperature of all hours in a day.                                                                            |
|             | * Hour                             |                                                                                                                                   |
|             |                                    | Required: Yes                                                                                                                     |
|             |                                    | Data type: string                                                                                                                 |
+-------------+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+
| InitialDate | YYYY-MM-DD                         | Required: Yes                                                                                                                     |
|             |                                    | Data type: string                                                                                                                 |
|             |                                    | Provide the date in the given format.                                                                                             |
+-------------+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+
| language    | Choose a value from the following: | Required: No. Default is English.                                                                                                 |
|             | * English                          | Data type: string                                                                                                                 |
|             | * Portuguese                       | Choose a language only from the given list. If you choose an incorrect value, the system will display result in English language. |
|             | * French                           |                                                                                                                                   |
|             | * Mandarin                         |                                                                                                                                   |
|             | * Hindi                            |                                                                                                                                   |
|             | * Korean                           |                                                                                                                                   |
+-------------+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+

* Response 
  * Success: Success response contains following parameters. For each interval, the response contains list of the temperature.

+--------+--------------------------------------------------+
| Status | Description                                      |
+--------+--------------------------------------------------+
| 200    | City: Name of the city.                          |
|        | Temperature: Value in decimal places.            |
|        | Start date: Start date of the data.              |
|        | End date: End date of the data.                  |
|        | Interval: Data interval - hour, day, week, month |
+--------+--------------------------------------------------+

  * Error

+--------+------------+-----------------------+
| Status | Error code | Description           |
+--------+------------+-----------------------+
| 400    | 1011       | Invalid URL           |
+--------+------------+-----------------------+
| 400    | 1012       | Invalid latitue       |
+--------+------------+-----------------------+
| 400    | 1013       | Invalid longitude     |
+--------+------------+-----------------------+
| 403    | 2011       | Invalid date          |
+--------+------------+-----------------------+
| 403    | 2012       | Invalid timeframe     |
+--------+------------+-----------------------+