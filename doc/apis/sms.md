# SMS API

### 0x0. Changes

- init version -v0.01 as 2018-06-06

### 0x1. sms/vcode

Get vcode when user login and change password.

- **Http Method:** GET
- **NeedMachineTicket:** NO
- **NeedUserTicket:** YES

#### Request JSON

```javascript
{
  "mobile": "18293819282"
}
```

#### Response JSON

```javascript
"result": {
  	"vcode": 291324
}
```

### 0x2. sms/voice

- **Http Method:** GET
- **NeedMachineTicket:** NO
- **NeedUserTicket:** YES

#### Request JSON

```javascript
{
  "mobile": "18293819282"
}
```