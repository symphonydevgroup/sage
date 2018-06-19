# Profile APIS

### 0x0. Changes
* init version - v0.01 at 2018-5-10

### 0x1. Classes
#### [ProfileCategroy Class]
````javascript
{
    "id": "9s9s9sd9",
    "name": "drink",
}
````
|Field|Type|Desc|
|---|---|---|
|id|string|categroy id|
|name|string|categroy display name|

#### [Profile Class]
````javascript
{
    "id":"19s99123123",
    "name": "soft drink",
    "categroy": {
        "id": "9s9s9sd9",
        "name": "drink",
    }
}
````
|Field|Type|Desc|
|---|---|---|
|id|string| profile id|
|name| string| profile display name|
|category| ProfileCategory| |

### 0x2. [API] profiles
list all profiles
* **Http Method:** GET
* **NeedMachineTicket:** NO
* **NeedUserTicket:** YES
#### Request Params
NO
#### Return Result
````javascript
"result": {
    "profiles":[
        {
            [Profile Class],
        }
    ]
}
````
