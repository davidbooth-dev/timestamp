# FCC - API's and Micro Services
## Timestamp Micro Service an FCC Project

### User stories:

- The API endpoint is `GET [project_url]/api/timestamp/:date_string?`.
- A date string is valid if can be successfully parsed by `new Date(date_string)` (JS) . 
   - Note that the unix timestamp needs to be an **integer** (not a string) specifying **milliseconds**. 
- In our test we will use date strings compliant with ISO-8601 (e.g. `"2016-11-20"`) because this will ensure an UTC timestamp.
- If the date string is **empty** it should be equivalent to trigger `new Date()`, i.e. the service uses the current timestamp.
- If the date string is **valid** the api returns a JSON having the structure 
   - `{"unix": <date.getTime()>, "utc" : <date.toUTCString()> }`
   - e.g. `{"unix": 1479663089000 ,"utc": "Sun, 20 Nov 2016 17:31:29 GMT"}`.
- If the date string is **invalid** the api returns a JSON having the structure `{"error" : "Invalid Date" }`.

#### Example usage:
- localhost:3000/api/timestamp/2015-12-25
- localhost:3000/api/timestamp/1451001600000
- localhost:3000/api/timestamp/
- localhost:3000/api/timestamp/this-is-not-a-date

#### Example output:
- {"unix":1451001600000, "utc":"Fri, 25 Dec 2015 00:00:00 GMT"}
- {"error": "Invalid Date"}
