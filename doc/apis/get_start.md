# Get Start

### 0x0. Changes
* init version - v0.01 at 2018-5-10

### 0x1. By Default
 Sage Dapp APIs are Restful apis using HTTPS to serve data services. Which means:
 * Send request by HTTPS
 * HTTP METHOD GET/POST/PUT/DELETE map to QUID operation for object
 
   |http methed| object opeartion| desc|
   |-----|-----|----|
   |GET| Query|Query an object or object list|
   |POST| Insert| insert new object|
   |PUT| Update| update object|
   |DELETE| Delete| remove object|
* Support DataType: JSON. All request & response params are JSON format

### 0x2. Base HTTPS Address
**Current http base address:** https://api.sageit.vip
> Sample:
Request **auth/login**, full address is https://api.sageit.vip/auth/login

### 0x3. User Authentication
* Before user login, client need a credential named 'machine_ticket" for futher auth related api access, machine_ticket can only access auth apis
* Machine_ticket never expire
* After user login, client need a credential named 'user_ticket' for futher api authentication, every api access needs with user_ticket in HTTP header for identify/specify user
* User_ticket will expire after 7 days since issued, after ticket is expired, need to call refresh ticket api to refresh it, otherwise, need to re-login again before futher calling

### 0x4. API Version
**Current API version:** v0.01
Every api calling needs with current version that used in HTTP header. Using wrong version will cause unkown error. 

### 0x5. HTTP Headers
As the instruction in above, API requests need including ticket and version in HTTP header, details in below:

|header name| header value type|header value| desc|
|-----|-----|-----|-----|
|machine_ticket| string | generate before login|optional with user_ticket, credentail generate default by machine account|
|user_ticket| string| generate after login|optional with machine_ticket, user account credentail identification|
|sver| string| v0.01|current sage api version|

### 0x6. HTTP Response Format
Typical http response format (JSON) as follow: 
```` javascript
{
    "status": "OK",
    "error_code" : 200,
    "error": "",
    "result": {}
}
````
|Field|Type|Desc|
|---|---|---|
|status|string| "OK": request successs; "Fail": request failed with errors|
|error_code|int|status code for identify error type, referer to see [status code list](./status_code_list.md)|
|error|string| error message description, if status is "OK" then it's emtpy|
|result| json| return value wrapper, api response description only display result field| 

### 0x7. API Access Limit
For security reason, api access limit needs to be activated while client using apis. 

|Ticket type| Limit times per api|Out of limit action|
|----|----|---|
|machine|5 times per minute|forbidden|
|user|60 time per minute|log as warning|



