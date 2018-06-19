# Task APIs

### 0x0. Changes
* init version - v0.01 at 2018-5-10

### 0x1. Classes
Tasks are user based action to earn SAGE coin from doing activities such as AD video watching, questionnaire filling, location marking etc. Tasks are published by merchants who want to do brand development with target customers or precision marketing.
Currently in our sysetm, we support 2 kind of tasks, video and questionnaire. End users can earn SAGE coin from it.

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

#### [TaskVideo Class]
````javascript
 {
    "url": "/lol.mpeg",
    "content": "<div>this is the main content shows in </div>",
}
````
| Field   | Type   | Desc           |
| ------- | ------ | -------------- |
| url     | string | video url      |
| content | HTML   | detail content |

#### [TaskQuestion Class]
````javascript
{
    "question": "your age?",
    "answer_type": "choice",
    "answers": [
        {
            "display_value": "10-16",
            "value": "youngth"
        }
    ]
}
````
| Field         | Type   | Desc                                     |
| ------------- | ------ | ---------------------------------------- |
| question      | HTML   | question                                 |
| answer_type   | string | "choice": answers are from choice, "text": user input answer |
| answers       | answer |                                          |
| display_value | HTML   | answer display                           |
| value         | string | answer value                             |

#### [TaskConfig Class]
````javascript
 {
    "start_date": "2018-01-23 09:00:00",
    "end_date": "2018-03-04 18:30:00",
    "target": "m",
    "total_sage": 100000,
    "sage_per_task": 20,
    "profile": "[Profile]",
    "cover_images":[
        {
            "url": "/lol01.png",
        },
    ],
    "task_video": "[TaskVideo]"
    "task_questionnaire": [
        {
            "class_type": "[TaskQuestion]",
        }
    ]
}
````
| Field              | Type              | Value                                    |
| ------------------ | ----------------- | ---------------------------------------- |
| start_date         | string            | task start date                          |
| end_date           | string            | task end date                            |
| total_sage         | int               | total sage of task that can used         |
| sage_per_task      | int               | sage that one person can earn from the task |
| profile            | Profile           | task related profile                     |
| cover_images       | JSON              | images shows in task list or detail      |
| cover_iamges url   | string            | image url                                |
| task_video         | TaskVideo         | task video class                         |
| task_questionnaire | TaskQuestion list | task question class list                 |

#### [TaskStatus Class]
{
    "task_total_click": 100,
    "task_total_done": 81,
}
| Field            | Type | Desc                                     |
| ---------------- | ---- | ---------------------------------------- |
| task_total_click | int  | total summary of task click by end users |
| task_total_done  | int  | total summary of task done by end users  |

#### [Task Class]
````javascript
{
    "id": "18xks9131232xs",
    "name": "LOL Vedio",
    "description": "LOL game hunting",
    "task_type": "video",
    "task_config":"[TaskConfig]",
    "merchant_info": "[MerchantInfo]",
    "task_status": "[TaskStatus]",
}
````
| Field         | Type         | Desc                                     |
| ------------- | ------------ | ---------------------------------------- |
| id            | string       | task id                                  |
| name          | string       | task display name                        |
| description   | string/HTML  | task description                         |
| task_type     | string       | "video": for video task, "questionnarie":for questionnarie task |
| task_config   | TaskConfig   | task config class                        |
| merchant_info | MerchantInfo | merchant info class                      |
| task_status   | TaskStatus   | task status class                        |

### 0x2. [API] task/{task_id}
* **Http Method:** GET/POST/PUT/DELETE
* **NeedMachineTicket:** NO
* **NeedUserTicket:** YES
#### Task JSON
````javascript
{
   [TaskClass]
}
````

### 0x3. [API] tasks

Get all merchant tasks.

- **Http Method:** GET
- **NeedMachineTicket:** NO
- **NeedUserTicket:** YES

#### Response JSON

```javascript
"result": {
  	"tasks": [
		[Task Class] 		
	]
}
```

### 0x3. tasks/task_id/finsh

Change task history.

- **Http Method:** POST
- **NeedMachineTicket:** NO
- **NeedUserTicket:** YES

#### Request JSON

```javascript
{
	"taskid": "f5847b18-2edc-46fe-95ee-c73a9cbb0c9e"
}
```

### 0x4. tasks/task_id/diss

Action for user to dislike some merchants.

- **Http Method:** POST
- **NeedMachineTicket:** NO
- **NeedUserTicket:** YES

#### Request JSON

```javascript
{
  	"merchantid": "ce61b3f5-0e69-4c6a-89a2-2767771aacc9"
}
```

