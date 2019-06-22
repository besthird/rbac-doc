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

