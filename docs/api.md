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

>GET /group/find

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

## 管理员

### 1.管理员列表

>GET /user

请求参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
| offset  | Integer |  偏移量  |
| limit   | Integer |  每页个数|
| id      | Integer |  管理员ID  |
| mobile  | String  |  管理员手机号|
| status  | Integer |  管理员状态  |


返回参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
| id  | Integer |  管理员ID  |
| name   | String |  姓名|
| mobile  | String  |  管理员手机号|
| password  | String  |  密码|
| status  | Integer |  状态1:有效0无效  |

返回示例
```json
{
	"code": 0,
	"data": {
		"count": 26,
		"items": [{
			"id": 1,
			"name": "超级管理员",
			"mobile": "15963611521",
			"password": "",
			"status": 1,
			"created_at": "2019-06-24 02:43:33",
			"updated_at": "2019-06-26 16:45:34"
		}, {
			"id": 9,
			"name": "用户测试0",
			"mobile": "15904435046",
			"password": "",
			"status": 1,
			"created_at": "2019-06-24 03:16:20",
			"updated_at": "2019-06-24 03:21:30"
		}]
	}
}
```

### 2.新增/保存管理员

>POST /user/save

请求参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
|   id    | Integer |  管理员ID  |
|  name   | String  |  管理员名称  |
| role_id | Array   | 角色ID |
| mobile | String   | 手机号 |
| status | Integer   | 状态 |

请求示例
```json
{
    "id": 1,
    "name": "test",
	"role_id": [1,3],
    "mobile": "单测专用项目",
    "status": "1"
}
```

### 3.删除管理员

>POST /user/delete

请求参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
|   id    | Integer |  管理员ID  |

请求示例
```json
{
	"id": 2
}
```
### 4.管理员详情

>GET /user/find

请求参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
|   id    | Integer |  管理员ID  |

返回参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
|   id    | Integer |  管理员ID  |
|   name  | String  |  管理员名  |
|   mobile| String  |  手机好  |
|   status| Integer |  管理员名  |

返回示例
```json
{
	"code": 0,
	"data": {
		"id": 1,
		"name": "超级管理员",
		"mobile": "15963611521",
		"password": "",
		"status": 1,
	}
}
```
### 5.设置状态

>GET /user/status

请求参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
|   id    | Integer |  管理员ID  |

返回参数

请求示例
```json
{
	"id": 1
}
```

### 5.登录

>POST /user/login

请求参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
|   mobile    | String |  手机号 |
|   password  | String |  密码  |

返回参数

请求示例
```json
{
	"mobile": 15904435047,
	"password": 123456,
}
```
返回示例
```json
{
	"code": 0,
	"data": {
		"token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJic19yYmFjX2FwaSIsImlhdCI6MTU2MTYwNjEzMywiZXhwIjoxNTYxNjA5NzMzLCJuYmYiOjE1NjE2MDYxMzMsInN1YiI6IiIsImp0aSI6IjY3cHZ3eUJTS1FnNVIwcUlIN1hsRHIwckxjb29hZ05pIiwidXNlcklkIjo5fQ.dbBHECGvOPy2Uk2yYL2NM5SD2JCeIaOLy-79UUvADTE"
	}
}
```

## 角色

### 1.角色列表

>GET /role

请求参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
| offset  | Integer |  偏移量  |
| limit   | Integer |  每页个数|
| name      | String |  角色  |
| status  | Integer |  角色状态  |


返回参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
| id  | Integer |  角色ID  |
| name   | String |  角色|
| comment  | String  |  角色介绍|
| status  | Integer |  状态1:有效0无效  |

返回示例
```json
{
	"code": 0,
	"data": {
		"count": 2,
		"items": [{
			"id": 1,
			"name": "角色1",
			"comment": "角色1测试",
			"status": 1,
			"created_at": "2019-06-24 10:26:13",
			"updated_at": "2019-06-24 10:26:13"
		}, {
			"id": 2,
			"name": "3",
			"comment": "4",
			"status": 1,
			"created_at": "2019-06-25 15:34:11",
			"updated_at": "2019-06-25 15:34:11"
		}]
	}
}
```

### 2.新增/保存角色

>POST /role/save

请求参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
|   id    | Integer |  角色ID  |
|  name   | String  |  角色名称  |
|  comment   | String  |  角色介绍  |
| status | Integer   | 状态1可用0不可用 |
| router_list | Array   | 路由ID |

请求示例
```json
{
	"id": 1,
	"name": "超级角色",
	"comment": "超级管理员权限角色",
	"status": 1,
	"router_list": [1]
}
```

### 3.删除角色

>POST /role/delete

请求参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
|   id    | Integer |  角色ID  |

请求示例
```json
{
	"id": 2
}
```
### 4.角色详情

>GET /role/info

请求参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
|   id    | Integer |  角色ID  |

返回参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
|   id    | Integer |  角色ID  |
|   name  | String  |  角色  |
|   comment| String |  角色介绍  |
|   status| Integer |  状态1可用0不可用  |

返回示例
```json
{
	"code": 0,
	"data": {
		"id": 2,
		"name": "3",
		"comment": "4",
		"status": 1,
		"created_at": "2019-06-25 15:34:11",
		"updated_at": "2019-06-25 15:34:11"
	}
}
```
### 5.设置角色

>POST /role/status

请求参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
|   id    | Integer |  角色ID  |

返回参数

请求示例
```json
{
	"id": 1
}
```

### 5.角色路由信息

>POST /role/router/list

请求参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
|   id    | Integer |  角色id |

返回参数

请求示例
```json
{
	"id": 1,
}
```
返回示例
```json
{
	"code": 0,
	"data": [{
		"id": 2,
		"project_id": 1,
		"group_id": 7,
		"type": 1,
		"name": "管理员",
		"route": "/user",
		"method": "get",
		"created_at": "2019-06-26 01:58:40",
		"updated_at": "2019-06-26 13:22:56"
	}, {
		"id": 4,
		"project_id": 1,
		"group_id": 1,
		"type": 0,
		"name": "管理员3",
		"route": "/user",
		"method": "get",
		"created_at": "2019-06-26 02:13:45",
		"updated_at": "2019-06-26 11:44:09"
	}]
}
```


## 路由API

### 1.路由列表

>GET /router

请求参数

| 字段名 |  类型   |   注释   |
|:------:|:-------:|:--------:|
| offset | Integer |  偏移量  |
| limit  | Integer | 每页个数 |
|  name  | String  |  路由名称  |

返回参数:

|   字段名   |  类型   |   注释   |
|:----------:|:-------:|:--------:|
|   count    | Integer |   总数   |
|   items    |  Array  | 路由列表 |
|  items.id  | Integer |  路由ID  |
| items.project_id  | Integer  | 项目ID  |
| items.name | String  |  路由名  |
| items.type | Integer  |  项目信息  |
| items.route | String  |  0页面路由 1接口路由 |
| items.method | String  |  请求方法  |
| items.group_id | Integer  |  小组ID  |
| items.group | Array  |  小组信息  |

返回示例
```json
{
	"code": 0,
	"data": {
		"count": 3,
		"items": [{
			"id": 2,
			"project_id": 1,
			"group_id": 7,
			"type": 1,
			"name": "管理员",
			"route": "/user",
			"method": "get",
			"created_at": "2019-06-26 01:58:40",
			"updated_at": "2019-06-26 13:22:56",
			"project": {
				"id": 1,
				"key": "test",
				"name": "单测专用项目"
			},
			"group": {
				"id": 7,
				"project_id": 1,
				"name": "11"
			}
		}]
	}
}
```

### 2.新增/保存路由

> POST /router/save

请求参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
|   id    | Integer |  路由ID  |
|   project_id   | Integer  | 项目ID  |
|   group_id    | String |  分组ID  |
|   type    | Integer |  0页面路由 1接口路由  |
|   name    | String |  名称  |
|   route    | String |  路由地址  |
|   method    | String |  请求方法  |

请求示例
```json
{
	"id": 1,
	"project_id": 1,
	"group_id": 1,
	"type": 1,
	"name": "默认路由",
	"route": "/",
	"method": "GET"
}
```

### 3.删除路由

>POST /router/delete

请求参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
|   id    | Integer |  路由ID  |

请求示例
```json
{
	"id": 2
}
```
### 4.路由详情

>GET /router/find

请求参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
|   id    | Integer |  路由ID  |

返回参数

| 字段名  |  类型   |   注释   |
|:-------:|:-------:|:--------:|
|   id    | Integer |  路由ID  |
|   project_id   | Integer  | 项目ID  |
|   group_id    | String |  分组ID  |
|   type    | Integer |  0页面路由 1接口路由  |
|   name    | String |  名称  |
|   route    | String |  路由地址  |
|   method    | String |  请求方法  |

返回示例
```json
{
	"code": 0,
	"data": {
		"id": 1,
		"project_id": 1,
		"group_id": 1,
		"type": 1,
		"name": "默认路由",
		"route": "/",
		"method": "GET",
		"created_at": "2019-06-27 05:35:50",
		"updated_at": "2019-06-27 05:35:50"
	}
}
```

