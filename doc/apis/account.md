# Account API

### 0x0. Changes

- init version -v0.01 as 2018-6-6

### 0x1. Classes

#### [Address Class]

```javascript
{
  	"addressid"
}
```

#### [Trade Class]

```javascript
{
  	"tradeid"
}
```

#### [Merchant Class]

```javascript
{
  	"merchantid": "ce61b3f5-0e69-4c6a-89a2-2767771aacc9",
    "merchantname": "UNIQ",
    "desc": "Japanese clothing manufacturer",
    "logo": "https://api.sageit.vip/task/logo/UNIQ.jpg" 
}
```

#### [Profile Class]

```javascript
{
    "id":"cf0065be-fe23-4824-8c40-ff0e62de1c7f",
    "name": "soft drink",
    "categroy": {
        "id": "80a41c20-72a0-41ff-9de9-950e5c5ce91b",
        "name": "drink",
    }
}
```

### 0x2. account

Get all user account information.

- **Http Method:** GET
- **NeedMachineTicket:** NO
- **NeedUserTicket:** YES

#### Response JSON

```javascript
"result":{
	"mobile": "18314231423",
    "displayname": "xiaoming",
    "avatar": "https://api.sageit.vip/avator/",
    "gender": "M",
    "address":[
      	{
  			[Address Class],
		}
    ],
    "birth": "19941113",
    "loginpwd": "060077037e418c6909bd8730f769d04fe384e91958f89a03ae6540a639480597",
    "paypwd": "060077037e418c6909bd8730f769d04fe384e91958f89a03ae6540a639480597",
    "balance": 100,
    "walletaddress": "1hvzSofGwT8cjb8JU7nBsCSfEVQX5u9CL",
    "trades":[
  		{
  			[Trade Class]
		}
	],
    "profiles": {
  		"like":[
  			{
              	[Profile Class],
            }
		],
        "unlike":[
  			{
              	[Profile Class],
            }
		],
	},
    "dissmerchant":[
		{
  			[Merchant Class]
		}  
	]    
}
```

| Field         | Type   | Desc                             |
| ------------- | ------ | -------------------------------- |
| mobile        | string | user mobile                      |
| displayname   | string | user nickname                    |
| avatar        | string | url;storage address              |
| gender        | string | M,F,O                            |
| birth         | string | user birthday;"yyyymmdd"         |
| loginpwd      | string | user login password              |
| paypwd        | string | user payment password            |
| balance       | int    | cryptocurrency balance           |
| walletaddress | string | wallet address                   |
| trades        | list   | transaction record               |
| profiles      | list   | list all profiles                |
| dissmerchant  | list   | the merchant list that user hate |

### 0x3. account

For user modify some information.

- **Http Method:** PUT
- **NeedMachineTicket:** NO
- **NeedUserTicket:** YES

#### Request JSON

```javascript
{
  	"displayname": "xiaofang",
    "walletaddress": "1hvzSofGwT8cjb8JU7nBsCSfEVQX5u9CL", 
}
```

### 0x4. account/upload_avatar

For user modify some information.

- **Http Method:** PUT
- **NeedMachineTicket:** NO
- **NeedUserTicket:** YESRequest JSON

```javascript
{
  	"avator":Binary,
}
```

### 0x5. account/ch_loginpwd

For user modify some information.

- **Http Method:** PUT
- **NeedMachineTicket:** NO
- **NeedUserTicket:** YES

```javascript
{
  	"login_pwd":"060077037e418c6909bd8730f769d04fe384e91958f89a03ae6540a639480597"
}
```

### 0x6. account/ch_paypwd

For user modify some information.

- **Http Method:** PUT
- **NeedMachineTicket:** NO
- **NeedUserTicket:** YES

```javascript
{
  	"pay_pwd":"060077037e418c6909bd8730f769d04fe384e91958f89a03ae6540a639480597"
}
```