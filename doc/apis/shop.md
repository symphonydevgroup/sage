# Shop APIS

### 0x0. Changes
* init version - v0.01 at 2018-5-10

### 0x1. shops
* **Http Method:** GET
* **NeedMachineTicket:** NO
* **NeedUserTicket:** YES

#### Request JSON
````javascript
{
    "Location":{
        "latitude": 0.111822,
        "longitude": 0.121232
    }
}
````
#### Response JSON
````javascript
"result": {
    "shops":[
        {
            "id": "129123ns99snd01231",
            "name": "zoo coffee",
            "location": {
                "latitude": 0.111822,
                "longitude": 0.121232,
                "country": "china",
                "province": "shanghai",
                "city": "shanghai",
                "district": "xuhui",
                "address": "Room 2112, #9888 HongDa Street"
            },
            "logo": "./zoocoffee_logo.png"
            "stars": 4.5
        }
    ]
}
````javascript
