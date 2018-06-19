# Auth API

### 0x0. Changes
* init version - v0.01 at 2018-5-10

### 0x1. auth/machine
When app start without user login, first it will check whether there is a machine_ticket in local storage, if not, need to use this api to get machine_ticket and store in local storage for futher using.
**Always Keep Machine Ticket in local stroage DO NOT DELETE IT** cause when user logout, app need machine ticket to access auth api again.
* **Http Method:** POST
* **NeedMachineTicket:** NO
* **NeedUserTicket:** NO

#### Request JSON
````javascript
{
    "device_id": "18xks9131232xs",
    "imei": "88129128192",
    "brand": "huawei",
    "model": "p7",
    "os":"android",
    "os_version": "16.04",
    "app_version":"v0.1",
}
````
|Field|Type|Desc|
|----|----|----|
|device_id|string|unique device id, if cannot acquire from system, using encrypt method to auto generate from client side|
|imei|string| IMEI|
|brand|string| device brand|
|model|string| device model|
|os|string| device os system|
|os_version|string| device os system version|
|app_version|string|current lunch app version|

#### Response JSON
```` javascript
"result": {
    "ticket": "f629478354d5b4e1db767746a244da438c00bceed05e3487f6a75a8007fda3be"
}
````
|Field|Type|Desc|
|----|----|----|
|ticket|string|machine_ticket, cache it in local storage|

#### Status Code & Error Message
referer to [status code list](./status_code_list.md)

### 0x2. auth/register
User Register method.
* **Http Method:** POST
* **NeedMachineTicket:** Yes
* **NeedUserTicket:** NO

#### Request JSON
````javascript
{
    "username": "mike717",
    "mobile": "03198762678",
    "password": "8d969eef6ecad3c29a3a629280e686cf0c3f5d5a86aff3ca12020c923adc6c92",
    "vcode": 1024
}
````
|Field|Type|Desc|
|----|----|----|
|username|string| user name|
|mobile|string|mobile number|
|password|string|sha256(user_input_password)|
|vcode|int|Sms verify code|

#### Response JSON
````javascript
"result": {
    "username": "mike717",
    "mobile": "03198762678",
}
````
|Field|Type|Desc|
|---|---|---|
|username|string||
|mobile|string||

#### Status Code & Error Message
referer to [status code list](./status_code_list.md)

### 0x3. auth/username/{username}
Check username whether exist, if exist, client side need to info user to change another unregister username.
* **Http Method:** GET
* **NeedMachineTicket:** Yes
* **NeedUserTicket:** NO

#### Request Params
|Field|Type|Desc|
|----|----|----|
|username|string|username|

#### Response JSON
````javascript
{
    "exist": false 
}
````
|Field|Type|Desc|
|----|----|----|
|exist|bool|username already exist in database or not|

#### Status Code & Error Message
referer to [status code list](./status_code_list.md)

### 0x4. auth/mobile/{mobile}
Check mobile whether exist, if exist, client side need to info user to change another unregister mobile.
* **Http Method:** GET
* **NeedMachineTicket:** Yes
* **NeedUserTicket:** NO

#### Request Params
|Field|Type|Desc|
|----|----|----|
|mobile|string|mobile number|

#### Response JSON
````javascript
{
    "exist": false 
}
````
|Field|Type|Desc|
|----|----|----|
|exist|bool|mobile already exist in database or not|

#### Status Code & Error Message
referer to [status code list](./status_code_list.md)

### 0x5. auth/login
For user login action, there're restricts in below:
> User has **5 times** retry chances in **1 hour**, out of retry times will lock the account in **1 hour** then unlock
> The fisrt 2 times retry will not need mobile and vcode, if retry >2 times, **mobile** and **vcode** is needed
* **Http Method:** POST
* **NeedMachineTicket:** Yes
* **NeedUserTicket:** NO

#### Request JSON
````javascript
{
    "username": "mike717",
    "mobile": "03198762678",
    "password": "8d969eef6ecad3c29a3a629280e686cf0c3f5d5a86aff3ca12020c923adc6c92",
    "vcode": 1024
}
````
|Field|Type|Desc|
|----|----|----|
|username|string| user name|
|mobile|string|optional, mobile number|
|password|string|sha256(user_input_password)|
|vcode|int|optional, Sms verify code|

#### Response JSON
```` javascript
"result": {
    "ticket": "f629478354d5b4e1db767746a244da438c00bceed05e3487f6a75a8007fda3be"
}
````
|Field|Type|Desc|
|----|----|----|
|ticket|string|user_ticket, cache it in local storage|

#### Status Code & Error Message
referer to [status code list](./status_code_list.md)

### 0x6. auth/ticket/{ticket}
Refresh user ticket before expired
* **Http Method:** GET
* **NeedMachineTicket:** NO
* **NeedUserTicket:** YES

#### Request Params
|Field|Type|Desc|
|----|----|----|
|ticket|string|user ticket|

#### Response JSON
```` javascript
"result": {
    "ticket": "f629478354d5b4e1db767746a244da438c00bceed05e3487f6a75a8007fda3be"
}
````
|Field|Type|Desc|
|----|----|----|
|ticket|string|machine_ticket, cache it in local storage|

#### Status Code & Error Message
referer to [status code list](./status_code_list.md)

### 0x7. auth/logout
When user logout, set current user_ticket to expired status in server side and remove user_ticket in client side
* **Http Method:** GET
* **NeedMachineTicket:** NO
* **NeedUserTicket:** YES

#### Request Params
NO
#### Response JSON
```` javascript
"result": {}
````

#### Status Code & Error Message
referer to [status code list](./status_code_list.md)

