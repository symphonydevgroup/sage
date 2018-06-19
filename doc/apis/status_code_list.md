# Status Code & Error Message

### 0x1. Success Code
|error_code| error| desc|
|----|----|----|
|200||request success|

### 0x2. System Error Code
|error_code| error | desc|
|----|----|----|
|1001|system Error| system failed with unkonw error|
|1002|service unavailable| service is stop or offline|
|1003|remote service error| RPC service is down or offline|
|1004|ip limit| ip limit access resource|
|1005|permission denied| user role cannot access target resource|
|1006|ticket is missing| no ticket in http header|
|1007|sver is missing| no sver in http header|
|1008| params error| parameter error|
|1009| too many pending request| system is busy for handling request|

### 0x3. Auth Error Code
|error_code| error| desc|
|----|----|----|
|3001|invalid vcode| sms verify code is not corret|
|3002|username/password is not correct||
|3003|need verify mobile while login|if retry > 2 times and not offer mobile/vcode, raise this error|
|3004|username already exist||
|3005|mobile already exist||
|3006|login out of retry times, please retry after an hour|if retry > 5 times in hour, raise this error|
|3007|ticket out of date| user_ticket out of date|
