# 接口文档

## 项目API

### 1.项目列表

> GET /project

请求参数

| 字段名 |  类型   |   注释   |
|:------:|:-------:|:--------:|
| offset | Integer |  偏移量  |
| limit  | Integer | 每页个数 |
|  key   | String  | 项目KEY  |
|   id   | Integer |  项目ID  |
|  name  | String  |  项目名  |

返回参数:

|   字段名   |  类型   |   注释   |
|:----------:|:-------:|:--------:|
|   count    | Integer |   总数   |
|   items    |  Array  | 项目列表 |
|  items.id  | Integer |  项目ID  |
| items.key  | String  | 项目KEY  |
| items.name | String  |  项目名  |

返回示例
```json
{
    "code": 0,
    "data": {
        "count": 1,
        "items": [
            {
                "id": 1,
                "key": "test",
                "name": "单测专用项目",
                "comment": "单测专用项目, 勿动",
                "created_at": "2019-06-22 00:49:41",
                "updated_at": "2019-06-22 00:51:14"
            }
        ]
    }
}
```

### 2.新增、保存项目

> POST /project/save

请求参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
|   key   | String  | 项目KEY  |
|   id    | Integer |  项目ID  |
|  name   | String  |  项目名  |
| comment | String  | 项目介绍 |

请求示例
```json
{
    "id": 1,
    "key": "test",
    "name": "单测专用项目",
    "comment": "单测专用项目, 勿动"
}
```

### 3.删除项目

> POST /project/delete

请求参数

| 字段名 |  类型   |  注释  |
|:------:|:-------:|:------:|
|   id   | Integer | 项目ID |

请求示例
```json
{
    "id": 2
}
```

## 组API

### 1.小组列表

>GET /group

请求参数

| 字段名 |  类型   |   注释   |
|:------:|:-------:|:--------:|
| offset | Integer |  偏移量  |
| limit  | Integer | 每页个数 |
| project_id   | String  | 项目ID  |
|   id   | Integer |  小组ID  |
|  name  | String  |  小组名  |

返回参数:

|   字段名   |  类型   |   注释   |
|:----------:|:-------:|:--------:|
|   count    | Integer |   总数   |
|   items    |  Array  | 小组列表 |
|  items.id  | Integer |  小组ID  |
| items.project_id  | Integer  | 项目ID  |
| items.name | String  |  小组名  |
| items.project | Array  |  项目信息  |

返回示例
```json
{
	"code": 0,
	"data": {
		"count": 6,
		"items": [{
			"id": 1,
			"project_id": 1,
			"name": "测试小组，误删",
			"created_at": "2019-06-23 08:38:27",
			"updated_at": "2019-06-23 08:38:27",
			"project": {
				"id": 1,
				"key": "test",
				"name": "单测专用项目"
			}
		}]
	}
}
```

### 2.新增小组

> POST /group/save

请求参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
|   id    | Integer |  组ID  |
|   project_id   | Integer  | 项目ID  |
|   name    | String |  组名  |

请求示例
```json
{
    "id": 1,
    "name": "单测专用组"
}
```

### 3.删除小组

>POST /group/delete

请求参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
|   id    | Integer |  组ID  |

请求示例
```json
{
	"id": 2
}
```
### 4.小组详情

请求参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
|   id    | Integer |  组ID  |

返回参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
|   id    | Integer |  组ID  |
|   project_id    | Integer |  项目ID  |
|   name    | String |  组名  |

返回示例
```json

{
	"code": 0,
	"data": {
		"id": 1,
		"project_id": 1,
		"name": "测试小组，误删",
		"created_at": "2019-06-23 08:38:27",
		"updated_at": "2019-06-23 08:38:27"
	}
}
```
