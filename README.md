## BBHCar 接口说明
API 地址前缀: https://admin.bbhcar.top/api  
除了登录接口和地址中带有/anonymous/的接口,其余所有接口需要在header添加
```
Header Authorization: Bearer token  
#token 为登录接口返回的 token
```

* 登录接口  
/auth/token 请求方式: POST, Body
```
{
    "username":"admin",
    "password":"P@ssw0rd"
}
```
返回
```
{
    "token": "eyJhbGciOiJIUzUxMiJ9.eyJodHRwczovL2JiaGNhci5jb20vY2xhaW0vcm9sZXMiOlsiUk9MRV9BRE1JTiIsIlJPTEVfVVNFUiJdLCJodHRwczovL3ZhZ3Rvb2xzLmNvbS9jbGFpbS9tb2JpbGUiOiIxMzg4ODg4ODg4OCIsImh0dHBzOi8vYmJoY2FyLmNvbS9jbGFpbS9lbmFibGVkIjp0cnVlLCJodHRwczovL2JiaGNhci5jb20vY2xhaW0vdXNlcm5hbWUiOiJhZG1pbiIsImV4cCI6MTc0MDkyNTQ0OCwiaHR0cHM6Ly9iYmhjYXIuY29tL2NsYWltL2NyZWF0ZWQiOjE3NDAzMjA2NDg3MTksImh0dHBzOi8vYmJoY2FyLmNvbS9jbGFpbS91c2VySWQiOiI4ODdkZTc4NjgwMDg0ZTRhOTdkYTJjYTAxMDhlOWEyMiJ9.zLP0zLYlDjyngn5qFGbl16mYAb43-oVA_TyT0rs6od-EIZp5moQ0UmdCrslMIGPxfCh_vAMCLVDbefZ6B-8Qhw"
}
```

* 个人信息  
/user/profile 请求方式 GET  
返回
```
{
    "id": "887de78680084e4a97da2ca0108e9a22",
    "changeVersion": 0,
    "createdBy": "SYSTEM",
    "createdDate": 1740319938000,
    "lastModifiedBy": "SYSTEM",
    "lastModifiedDate": 1740319938000,
    "username": "admin",
    "password": "",
    "mobile": "13888888888",
    "status": true,
    "roles": [
        "ROLE_ADMIN",
        "ROLE_USER"
    ]
}
```

* 修改密码 (用户修改自己的密码)  
/api/user/change-password 请求方式 PUT
```
{
    "oldPassword": "P@ssw0rd",
    "newPassword": "P@ssw0rd1"
}
```
返回
```
Http Status Code : 200
```

* 工具箱列表  
/toolbox/getToolBoxListByToolTypeAndUserType?keyword=b&toolType=USB&userType=1&pageNo=1&pageSize=20 请求方式 GET  
返回
```
{
    "data": [
        {
            "id": "DA95751CE7E1448FAF60A1FFD8BBE037",
            "changeVersion": 0,
            "createdBy": "SYSTEM",
            "createdDate": 1740366766000,
            "toolName": "bbhdesk",
            "toolIcon": "https://ffdkajfldsdjf",
            "toolUrl": "https://ffdkajfldsdjf",
            "toolSort": 1,
            "toolType": "USB",
            "userType": 1,
            "toolDesc": "BBHDesc 是远程控制工具"
        },
        {
            "id": "c0beafa5939f4105b60d3d304f81e4ba",
            "changeVersion": 0,
            "createdBy": "admin",
            "createdDate": 1740379225000,
            "lastModifiedBy": "admin",
            "lastModifiedDate": 1740379225000,
            "toolName": "bbhdesk1",
            "toolIcon": "https://ffdkajfldsdjf.com",
            "toolUrl": "https://ffdkajfldsdjf.com",
            "toolSort": 2,
            "toolType": "USB",
            "userType": 1,
            "toolDesc": "BBHDesc2 是远程控制工具"
        }
    ],
    "paging": {
        "firstPage": 1,
        "lastPage": 1,
        "nextPage": 0,
        "prevPage": 0,
        "currentPage": 1,
        "totalPage": 1,
        "rowCount": 2,
        "pageSize": 20,
        "hasNext": false,
        "hasPrev": false,
        "hasFirst": true,
        "hasLast": true,
        "startOffset": 0
    }
}
```
* 查看/下载 工具  
/toolbox/DA95751CE7E1448FAF60A1FFD8BBE037 请求方式 GET   
返回
```
{
    "id": "DA95751CE7E1448FAF60A1FFD8BBE037",
    "changeVersion": 0,
    "createdBy": "SYSTEM",
    "createdDate": 1740366766000,
    "toolName": "bbhdesk",
    "toolIcon": "https://ffdkajfldsdjf",
    "toolUrl": "https://ffdkajfldsdjf",
    "toolSort": "1",
    "toolType": "USB",
    "userType": 1,
    "toolDesc": "BBHDesc 是远程控制工具"
}
```
* 添加工具  
/toolbox/addToolBox 请求方式 POST
```
{
    "toolName": "bbhdesk2",
    "toolIcon": "https://ffdkajfldsdjf.com",
    "toolUrl": "https://ffdkajfldsdjf.com",
    "toolSort": 2,
    "toolType": "USB",
    "userType": 1,
    "toolDesc": "BBHDesc2 是远程控制工具"
}
```
返回
```
{
    "id": "c0beafa5939f4105b60d3d304f81e4ba",
    "createdBy": "admin",
    "createdDate": 1740379224651,
    "lastModifiedBy": "admin",
    "lastModifiedDate": 1740379224651,
    "toolName": "bbhdesk2",
    "toolIcon": "https://ffdkajfldsdjf.com",
    "toolUrl": "https://ffdkajfldsdjf.com",
    "toolSort": 2,
    "toolType": "USB",
    "userType": 1,
    "toolDesc": "BBHDesc2 是远程控制工具"
}
```
* 修改工具  
/toolbox/editToolBox 请求方式 PUT
```
{
    "id": "c0beafa5939f4105b60d3d304f81e4ba",
    "toolName": "bbhdesk3",
    "toolIcon": "https://ffdkajfldsdjf.com",
    "toolUrl": "https://ffdkajfldsdjf.com",
    "toolSort": 2,
    "toolType": "USB",
    "userType": 1,
    "toolDesc": "BBHDesc3 是远程控制工具"
}
```
返回
```
{
    "id": "c0beafa5939f4105b60d3d304f81e4ba",
    "createdBy": "admin",
    "createdDate": 1740379224651,
    "lastModifiedBy": "admin",
    "lastModifiedDate": 1740379224651,
    "toolName": "bbhdesk3",
    "toolIcon": "https://ffdkajfldsdjf.com",
    "toolUrl": "https://ffdkajfldsdjf.com",
    "toolSort": 2,
    "toolType": "USB",
    "userType": 1,
    "toolDesc": "BBHDesc3 是远程控制工具"
}
```
* 删除工具  
/toolbox/deleteToolBox/c0beafa5939f4105b60d3d304f81e4ba 请求方式 DELETE   
返回
```
Http Status Code : 200
```
* 获取服务器列表  
/program/server/getServerListByAreaType?areaType=1&pageNo=1&pageSize=20 请求方式 GET areaType 1 = 国内 2 = 国际  
返回
```
{
    "data": [
        {
            "id": "9f2602a9d7dc4fd5bc3bedc42ada930d",
            "changeVersion": 0,
            "createdBy": "SYSTEM",
            "createdDate": 1740388231000,
            "lastModifiedBy": "SYSTEM",
            "lastModifiedDate": 1740388263000,
            "serverAddr": "1.1.1.1",
            "serverPort": "22",
            "serverName": "国内上海服务器1",
            "serverRoot": "root",
            "serverPassword": "password",
            "areaDesc": "国内-上海",
            "areaType": 1
        }
    ],
    "paging": {
        "firstPage": 1,
        "lastPage": 1,
        "nextPage": 0,
        "prevPage": 0,
        "currentPage": 1,
        "totalPage": 1,
        "rowCount": 1,
        "pageSize": 20,
        "hasNext": false,
        "hasPrev": false,
        "hasFirst": true,
        "hasLast": true,
        "startOffset": 0
    }
}
```
* 获取服务器详细信息  
/program/server/9f2602a9d7dc4fd5bc3bedc42ada930d 请求方式 GET  
返回
```
{
    "id": "9f2602a9d7dc4fd5bc3bedc42ada930d",
    "changeVersion": 0,
    "createdBy": "SYSTEM",
    "createdDate": 1740388231000,
    "lastModifiedBy": "SYSTEM",
    "lastModifiedDate": 1740388263000,
    "serverAddr": "1.1.1.1",
    "serverPort": "22",
    "serverName": "国内上海服务器1",
    "serverRoot": "root",
    "serverPassword": "password",
    "areaDesc": "国内-上海",
    "areaType": 1
}
```
* 添加服务器  
/program/server/addServer 请求方式 POST
```
{
    "serverAddr": "1.1.1.1",
    "serverPort": "22",
    "serverName": "国内上海服务器1",
    "serverRoot": "root",
    "serverPassword": "password",
    "areaDesc": "国内-上海",
    "areaType": 1
}
```
返回
```
{
    "id": "9f2602a9d7dc4fd5bc3bedc42ada930d",
    "changeVersion": 0,
    "createdBy": "SYSTEM",
    "createdDate": 1740388231000,
    "lastModifiedBy": "SYSTEM",
    "lastModifiedDate": 1740388263000,
    "serverAddr": "1.1.1.1",
    "serverPort": "22",
    "serverName": "国内上海服务器1",
    "serverRoot": "root",
    "serverPassword": "password",
    "areaDesc": "国内-上海",
    "areaType": 1
}
```
* 修改服务器  
/program/server/editServer 请求方式 PUT
```
{
    "id": "9f2602a9d7dc4fd5bc3bedc42ada930d",
    "serverAddr": "1.1.1.1",
    "serverPort": "22",
    "serverName": "国内上海服务器1",
    "serverRoot": "root",
    "serverPassword": "password",
    "areaDesc": "国内-上海",
    "areaType": 1
}
```
返回
```
{
    "id": "9f2602a9d7dc4fd5bc3bedc42ada930d",
    "changeVersion": 0,
    "createdBy": "SYSTEM",
    "createdDate": 1740388231000,
    "lastModifiedBy": "SYSTEM",
    "lastModifiedDate": 1740388263000,
    "serverAddr": "1.1.1.1",
    "serverPort": "22",
    "serverName": "国内上海服务器1",
    "serverRoot": "root",
    "serverPassword": "password",
    "areaDesc": "国内-上海",
    "areaType": 1
}
```
* 删除服务器  
/program/server/deleteServer/c0beafa5939f4105b60d3d304f81e4ba 请求方式 DELETE  
返回
```
Http Status Code : 200
```

* 重启服务器  
/api/program/server/rebootServer 请求方式 PUT
```
["9f2602a9d7dc4fd5bc3bedc42ada930d","9f2602a9d7dc4fd5bc3bedc42ada930d","9f2602a9d7dc4fd5bc3bedc42ada930d"]
```
返回
```
Http Status Code : 200
```


* 查看公告  
/program/announcement 请求方式 GET  
返回
```
{
    "id": "070a1b10a5ef4ef6aa478b7cc603bd68",
    "changeVersion": 0,
    "createdBy": "SYSTEM",
    "createdDate": 1740408778000,
    "lastModifiedBy": "SYSTEM",
    "lastModifiedDate": 1740408778000,
    "announcementCn": "大家好",
    "announcementEn": "hello"
}
```

* 修改公告  
/program/announcement/settings 请求方式 PUT
```
{
    "announcementCn": "大家好,我是谁",
    "announcementEn": "hello,Who am i"
}
```
返回
```
{
    "id": "070a1b10a5ef4ef6aa478b7cc603bd68",
    "lastModifiedBy": "admin",
    "lastModifiedDate": 1740410927768,
    "announcementCn": "大家好,我是谁",
    "announcementEn": "hello,Who am i"
}
```

* 心跳检测  
/online/check?clientId=&clientType=&heartbeatType= 请求方式 GET

| 参数  | 说明                                             |
|---|------------------------------------------------|
| programId | 应用ID                                           |
| clientId | 客户端ID，需要生成一个UUID 去除掉-之后的字符串，在同一个检测心跳的流程中应该保持不变 |
| clientType | 客户端类型，客户端 S 服务端 C                              |
| heartbeatType | 心跳类型，登录 LOGIN， 保持 KEEPALIVE                    |

返回
```
{"onlineStatus": "online"}
# 如果结果为 offline 则客户端立即下线
```

* 上报客户端连接信息  
/api/user/report-client-connection-infomation 请求方式 PUT  
```
{
    "id": "887de78680084e4a97da2ca0108e9a22",
    "connectType": "USB",
    "connectIp": "111.23.3.90"
    "connectPort": "10420"
}
```
返回
```
{
    "id": "887de78680084e4a97da2ca0108e9a22",
    "changeVersion": 0,
    "createdBy": "SYSTEM",
    "createdDate": 1740319938000,
    "lastModifiedBy": "SYSTEM",
    "lastModifiedDate": 1740319938000,
    "username": "admin",
    "password": "",
    "mobile": "13888888888",
    "status": true,
    "roles": [
        "ROLE_ADMIN",
        "ROLE_USER"
    ],
    "comboId": "0a1fb0ca00a04ef696eec719b4313459",
    "comboName": "Super Engineer",
    "expireTime": 1772986998000,
    "userType": "3",
    "realName": "刘书宝",
    "remark": "管理员",
    "port": "port0:vkey_password,port1:10011,port2:10012,port3:10013,port4:10014,port5:10015,port6:10016,port7:10017,port8:10018,port9:10019,port10:10020",
    "online": false
}
```


* 匿名根据应用ID查询应用详情  
/anonymous/program/9f2602a9d7dc4fd5bc3bedc42ada930d 请求方式 GET  
返回
```
{
    "id": "0ce52ed49cfd44d6a14dced94a9645d7",
    "changeVersion": 0,
    "createdBy": "SYSTEM",
    "createdDate": 1740908896000,
    "lastModifiedBy": "SYSTEM",
    "lastModifiedDate": 1740908896000,
    "programName": "111",
    "programVersion": "2321",
    "programMD5": "313",
    "programKey": "313",
    "updateUrl": "321321",
    "clientKeepalive": 30,
    "serverKeepalive": 60,
    "programStatus": 111,
    "programDesc": "111"
}
```

* 匿名根据应用名称查询应用详情  
/anonymous/program/name?programName= 请求方式 GET  
返回
```
{
    "id": "0ce52ed49cfd44d6a14dced94a9645d7",
    "changeVersion": 0,
    "createdBy": "SYSTEM",
    "createdDate": 1740908896000,
    "lastModifiedBy": "SYSTEM",
    "lastModifiedDate": 1740908896000,
    "programName": "111",
    "programVersion": "2321",
    "programMD5": "313",
    "programKey": "313",
    "updateUrl": "321321",
    "clientKeepalive": 30,
    "serverKeepalive": 60,
    "programStatus": 111,
    "programDesc": "111"
}
```

* 应用列表  
/program?keyword=&programStatus=&pageNo=1&pageSize=20 请求方式 GET  
返回
```
{
    "data": [
    {
        "id": "0ce52ed49cfd44d6a14dced94a9645d7",
        "changeVersion": 0,
        "createdBy": "SYSTEM",
        "createdDate": 1740908896000,
        "lastModifiedBy": "SYSTEM",
        "lastModifiedDate": 1740908896000,
        "programName": "111",
        "programVersion": "2321",
        "programMD5": "313",
        "programKey": "313",
        "updateUrl": "321321",
        "clientKeepalive": 30,
        "serverKeepalive": 60,
        "programStatus": 111,
        "programDesc": "111"
    }
  ],
  "paging": {
      "firstPage": 1,
      "lastPage": 1,
      "nextPage": 0,
      "prevPage": 0,
      "currentPage": 1,
      "totalPage": 1,
      "rowCount": 1,
      "pageSize": 20,
      "hasNext": false,
      "hasPrev": false,
      "hasFirst": true,
      "hasLast": true,
      "startOffset": 0
    }
}
```

* 应用详情  
/program/0ce52ed49cfd44d6a14dced94a9645d7 请求方式 GET  
返回
```
{
    "id": "0ce52ed49cfd44d6a14dced94a9645d7",
    "changeVersion": 0,
    "createdBy": "SYSTEM",
    "createdDate": 1740908896000,
    "lastModifiedBy": "SYSTEM",
    "lastModifiedDate": 1740908896000,
    "programName": "111",
    "programVersion": "2321",
    "programMD5": "313",
    "programKey": "313",
    "updateUrl": "321321",
    "clientKeepalive": 30,
    "serverKeepalive": 60,
    "programStatus": 111,
    "programDesc": "111"
}
```

* 添加应用  
/program/addProgram 请求方式 POST
```
{
    "programName": "111",
    "programVersion": "2321",
    "programMD5": "313",
    "programKey": "313",
    "updateUrl": "321321",
    "clientKeepalive": 30,
    "serverKeepalive": 60,
    "programStatus": 111,
    "programDesc": "111"
}
```
返回
```
{
    "id": "0ce52ed49cfd44d6a14dced94a9645d7",
    "changeVersion": 0,
    "createdBy": "SYSTEM",
    "createdDate": 1740908896000,
    "lastModifiedBy": "SYSTEM",
    "lastModifiedDate": 1740908896000,
    "programName": "111",
    "programVersion": "2321",
    "programMD5": "313",
    "programKey": "313",
    "updateUrl": "321321",
    "clientKeepalive": 30,
    "serverKeepalive": 60,
    "programStatus": 111,
    "programDesc": "111"
}
```

* 编辑应用  
/program/editProgram 请求方式 PUT
```
{
    "id": "0ce52ed49cfd44d6a14dced94a9645d7",
    "changeVersion": 0,
    "createdBy": "SYSTEM",
    "createdDate": 1740908896000,
    "lastModifiedBy": "SYSTEM",
    "lastModifiedDate": 1740908896000,
    "programName": "111",
    "programVersion": "2321",
    "programMD5": "313",
    "programKey": "313",
    "updateUrl": "321321",
    "clientKeepalive": 30,
    "serverKeepalive": 60,
    "programStatus": 111,
    "programDesc": "111"
}
```
返回
```
{
    "id": "0ce52ed49cfd44d6a14dced94a9645d7",
    "changeVersion": 0,
    "createdBy": "SYSTEM",
    "createdDate": 1740908896000,
    "lastModifiedBy": "SYSTEM",
    "lastModifiedDate": 1740908896000,
    "programName": "111",
    "programVersion": "2321",
    "programMD5": "313",
    "programKey": "313",
    "updateUrl": "321321",
    "clientKeepalive": 30,
    "serverKeepalive": 60,
    "programStatus": 111,
    "programDesc": "111"
}
```

* 删除应用  
/program/deleteProgram/0ce52ed49cfd44d6a14dced94a9645d7 请求方式 DELETE
```
Http Status Code : 200
```

* 套餐明细列表 (USB国内，USB国际，等等)  
/combo/items 请求方式 GET
```
[
    {
        "id": "7e09c882b44e43be8ad40469b912fb80",
        "changeVersion": 0,
        "createdBy": "SYSTEM",
        "createdDate": 1740924938000,
        "lastModifiedBy": "SYSTEM",
        "lastModifiedDate": 1740971010000,
        "itemName": "USB国内",
        "areaType": 1,
        "itemSort": 1
    },
    {
        "id": "58796971fcd54ddcbc72d9622a88d3cb",
        "changeVersion": 0,
        "createdBy": "SYSTEM",
        "createdDate": 1740924938000,
        "lastModifiedBy": "SYSTEM",
        "lastModifiedDate": 1740971009000,
        "itemName": "USB国际",
        "areaType": 2,
        "itemSort": 2
    },
    {
        "id": "cb86b6b5f6e2464d8fe06b648800ecdb",
        "changeVersion": 0,
        "createdBy": "SYSTEM",
        "createdDate": 1740924938000,
        "lastModifiedBy": "SYSTEM",
        "lastModifiedDate": 1740970840000,
        "itemName": "DOIP国内",
        "areaType": 1,
        "itemSort": 3
    },
    {
        "id": "da3a0e809fdb484ebac057559972da26",
        "changeVersion": 0,
        "createdBy": "SYSTEM",
        "createdDate": 1740924938000,
        "lastModifiedBy": "SYSTEM",
        "lastModifiedDate": 1740970841000,
        "itemName": "DOIP国际",
        "areaType": 2,
        "itemSort": 4
    },
    {
        "id": "f46b1c8434fd48e9b97568154762f79b",
        "changeVersion": 0,
        "createdBy": "SYSTEM",
        "createdDate": 1740924938000,
        "lastModifiedBy": "SYSTEM",
        "lastModifiedDate": 1740970844000,
        "itemName": "SoftEther VPN国内",
        "areaType": 1,
        "itemSort": 5
    },
    {
        "id": "6d99e06fe47d4414a5f7ee1907fb6f1a",
        "changeVersion": 0,
        "createdBy": "SYSTEM",
        "createdDate": 1740924938000,
        "lastModifiedBy": "SYSTEM",
        "lastModifiedDate": 1740970848000,
        "itemName": "SoftEther VPN国际",
        "areaType": 2,
        "itemSort": 6
    }
]
```

* 获取套餐列表  
/combo?keyword=&pageNo=1&pageSize=20 请求方式 GET  
返回
```
{
    "data": [
        {
            "id": "57373bdd0fb94c489408eff5f9a3c949",
            "changeVersion": 0,
            "createdBy": "admin",
            "createdDate": 1740988693000,
            "lastModifiedBy": "admin",
            "lastModifiedDate": 1740988693000,
            "comboName": "free1",
            "comboContent": "DOIP国内+DOIP国际",
            "comboPrice": "200",
            "comboValidity": "27"
        },
        {
            "id": "faee49a8b7934480a0365bc99ee2c8e7",
            "changeVersion": 0,
            "createdBy": "SYSTEM",
            "createdDate": 1740986714000,
            "lastModifiedBy": "SYSTEM",
            "lastModifiedDate": 1740986714000,
            "comboName": "free",
            "comboContent": "usb国内+usb国际",
            "comboPrice": "100",
            "comboValidity": "7"
        }
    ],
    "paging": {
        "firstPage": 1,
        "lastPage": 1,
        "nextPage": 0,
        "prevPage": 0,
        "currentPage": 1,
        "totalPage": 1,
        "rowCount": 2,
        "pageSize": 20,
        "hasNext": false,
        "hasPrev": false,
        "hasFirst": true,
        "hasLast": true,
        "startOffset": 0
    }
}
```
* 获取套餐详情  
/combo/7e09c882b44e43be8ad40469b912fb80 请求方式 GET  
返回
```
{
    "id": "faee49a8b7934480a0365bc99ee2c8e7",
    "comboName": "free",
    "comboContent": "usb国内+usb国际",
    "comboPrice": "100",
    "comboValidity": "7",
    "comboItems": [
        {
            "itemName": "USB国内",
            "areaType": 1,
            "itemSort": 1
        },
        {
            "itemName": "USB国际",
            "areaType": 2,
            "itemSort": 2
        }
    ]
}
```

* 添加套餐  
/combo 请求方式 POST
```
{
    "comboName": "free1",
    "comboPrice": "200",
    "comboValidity": "27",
    "comboItems": [
        { "id": "cb86b6b5f6e2464d8fe06b648800ecdb" },
        { "id": "da3a0e809fdb484ebac057559972da26" }
    ]
}
```
返回
```
{
    "id": "57373bdd0fb94c489408eff5f9a3c949",
    "createdBy": "admin",
    "createdDate": 1740988692999,
    "lastModifiedBy": "admin",
    "lastModifiedDate": 1740988692999,
    "comboName": "free1",
    "comboContent": "DOIP国内+DOIP国际",
    "comboPrice": "200",
    "comboValidity": "27",
    "comboItems": [
        {
            "id": "cb86b6b5f6e2464d8fe06b648800ecdb",
            "itemName": "DOIP国内"
        },
        {
            "id": "da3a0e809fdb484ebac057559972da26",
            "itemName": "DOIP国际"
        }
    ]
}
```

* 编辑套餐  
/combo 请求方式 PUT
```
{
    "id": "57373bdd0fb94c489408eff5f9a3c949",
    "comboName": "free2",
    "comboPrice": "200",
    "comboValidity": "27",
    "comboItems": [
        { "id": "f46b1c8434fd48e9b97568154762f79b" },
        { "id": "da3a0e809fdb484ebac057559972da26" }
    ]
}
```
返回
```
{
    "id": "57373bdd0fb94c489408eff5f9a3c949",
    "lastModifiedBy": "admin",
    "lastModifiedDate": 1740989001744,
    "comboName": "free2",
    "comboContent": "SoftEther VPN国内+DOIP国际",
    "comboPrice": "200",
    "comboValidity": "27",
    "comboItems": [
        {
            "id": "f46b1c8434fd48e9b97568154762f79b",
            "itemName": "SoftEther VPN国内"
        },
        {
            "id": "da3a0e809fdb484ebac057559972da26",
            "itemName": "DOIP国际"
        }
    ]
}
```

* 删除套餐  
/combo/faee49a8b7934480a0365bc99ee2c8e7 请求方式 DELETE
```
Http Status Code : 200
```

* 获取系统角色  
/api/user/roles 请求方式 GET
返回
```
[
    {
        "id": "38ddf55cd77255e7a43d275842c6a1ee",
        "changeVersion": 0,
        "createdBy": "SYSTEM",
        "createdDate": 1722413684000,
        "lastModifiedBy": "SYSTEM",
        "lastModifiedDate": 1722414399000,
        "roleName": "ROLE_FLASHDATEN",
        "roleDesc": "固件用户"
    },
    {
        "id": "71ddf58ae77145e7a43d275842c6a1cd",
        "changeVersion": 0,
        "createdBy": "SYSTEM",
        "createdDate": 1721046613000,
        "lastModifiedBy": "SYSTEM",
        "lastModifiedDate": 1722414406000,
        "roleName": "ROLE_USER",
        "roleDesc": "普通用户"
    },
    {
        "id": "31d170c9f85a43f2b06efdffa685b749",
        "changeVersion": 0,
        "createdBy": "SYSTEM",
        "createdDate": 1721920226000,
        "lastModifiedBy": "SYSTEM",
        "lastModifiedDate": 1722764791000,
        "roleName": "ROLE_ADMIN",
        "roleDesc": "车型管理员"
    },
    {
        "id": "a469c743524611ef9d7a0242ac110003",
        "changeVersion": 0,
        "createdBy": "SYSTEM",
        "createdDate": 1722764883000,
        "lastModifiedBy": "SYSTEM",
        "lastModifiedDate": 1722764937000,
        "roleName": "ROLE_DATASET",
        "roleDesc": "参数管理员"
    },
    {
        "id": "3930ac5de84b419982f6b58f8e2d4447",
        "changeVersion": 0,
        "createdBy": "SYSTEM",
        "createdDate": 1721046613000,
        "lastModifiedBy": "SYSTEM",
        "lastModifiedDate": 1722764939000,
        "roleName": "ROLE_SUPER",
        "roleDesc": "超级管理员"
    },
    {
        "id": "a469c743524611ef9d7a0242ac110004",
        "changeVersion": 0,
        "createdBy": "SYSTEM",
        "createdDate": 1725687060000,
        "lastModifiedBy": "SYSTEM",
        "lastModifiedDate": 1725804190000,
        "roleName": "ROLE_REPORT",
        "roleDesc": "诊断报告"
    },
    {
        "id": "82999d2bee3241f59e87b0d095acd3c0",
        "changeVersion": 0,
        "createdBy": "SYSTEM",
        "createdDate": 1741329731000,
        "lastModifiedBy": "SYSTEM",
        "lastModifiedDate": 1741329731000,
        "roleName": "ROLE_SFD1",
        "roleDesc": "SFD1"
    }
]
```

* 管理员修改用户密码  
/api/user/change-password-by-admin 请求方式 PUT
```
{
    "userId": "887de78680084e4a97da2ca0108e9a22",
    "newPassword": "P@ssw0rd1"
}
```
返回
```
Http Status Code : 200
```

* 用户列表获取用户详情  
/api/user/887de78680084e4a97da2ca0108e9a22 请求方式 GET  
返回
```
{
    "id": "887de78680084e4a97da2ca0108e9a22",
    "changeVersion": 0,
    "createdBy": "SYSTEM",
    "createdDate": 1740319938000,
    "lastModifiedBy": "SYSTEM",
    "lastModifiedDate": 1740319938000,
    "username": "admin",
    "password": "$2a$10$sl76JLjQ.hyP6QPz7yxAbOrHrCSfUJ5BB8qbkjocrQL7VIH2c0zWC",
    "mobile": "13888888888",
    "status": true,
    "roles": [
        "ROLE_ADMIN",
        "ROLE_USER"
    ],
    "comboId": "3c9f714e8b554369a765ac42e6f970a1",
    "comboName": "111",
    "userType": "4",
    "realName": "刘书宝",
    "remark": "刘书宝牛逼plus"
}
```

* 用户列表  
/api/user?keyword=刘&userType=&comboId=&status=&pageNo=1&pageSize=20 请求方式 GET  
返回
```
{
    "data": [
        {
            "id": "887de78680084e4a97da2ca0108e9a22",
            "changeVersion": 0,
            "createdBy": "SYSTEM",
            "createdDate": 1740319938000,
            "lastModifiedBy": "SYSTEM",
            "lastModifiedDate": 1740319938000,
            "username": "admin",
            "password": "",
            "mobile": "13888888888",
            "status": true,
            "comboId": "3c9f714e8b554369a765ac42e6f970a1",
            "comboName": "111",
            "userType": "4",
            "realName": "刘书宝",
            "remark": "刘书宝牛逼plus"
        }
    ],
    "paging": {
        "firstPage": 1,
        "lastPage": 1,
        "nextPage": 0,
        "prevPage": 0,
        "currentPage": 1,
        "totalPage": 1,
        "rowCount": 1,
        "pageSize": 20,
        "hasNext": false,
        "hasPrev": false,
        "hasFirst": true,
        "hasLast": true,
        "startOffset": 0
    }
}
```

* 用户列表删除用户  
/api/user/887de78680084e4a97da2ca0108e9a22 请求方式 DELETE  
返回
```
Http Status Code : 200
```

* 用户列表添加用户  
/api/user/addUser 请求方式 POST
```
{
    "username": "ffff",
    "password": "fffff",
    "mobile": "13888888888",
    "roles": [
        "ROLE_ADMIN",
        "ROLE_USER"
    ],
    "comboId": "0a1fb0ca00a04ef696eec719b4313459",
    "comboName": "Super Engineer",
    "expireTime": 1772986998000,
    "userType": "3",
    "realName": "刘书宝",
    "remark": "管理员",
    "port": "port0:vkey_password,port1:10011,port2:10012,port3:10013,port4:10014,port5:10015,port6:10016,port7:10017,port8:10018,port9:10019,port10:10020",
}
```
返回
```
{
    "id": "887de78680084e4a97da2ca0108e9a22",
    "changeVersion": 0,
    "createdBy": "SYSTEM",
    "createdDate": 1740319938000,
    "lastModifiedBy": "SYSTEM",
    "lastModifiedDate": 1740319938000,
    "username": "admin",
    "password": "",
    "mobile": "13888888888",
    "status": true,
    "roles": [
        "ROLE_ADMIN",
        "ROLE_USER"
    ],
    "comboId": "0a1fb0ca00a04ef696eec719b4313459",
    "comboName": "Super Engineer",
    "expireTime": 1772986998000,
    "userType": "3",
    "realName": "刘书宝",
    "remark": "管理员",
    "port": "port0:vkey_password,port1:10011,port2:10012,port3:10013,port4:10014,port5:10015,port6:10016,port7:10017,port8:10018,port9:10019,port10:10020",
    "online": false
}
```

* 用户列表修改用户  
/api/user/editUser 请求方式 PUT
```
{
    "id": "887de78680084e4a97da2ca0108e9a22",
    "roles": [
        "ROLE_ADMIN",
        "ROLE_USER"
    ],
    "comboId": "0a1fb0ca00a04ef696eec719b4313459",
    "comboName": "Super Engineer",
    "expireTime": 1772986998000,
    "userType": "3",
    "realName": "刘书宝",
    "remark": "管理员",
    "port": "port0:vkey_password,port1:10011,port2:10012,port3:10013,port4:10014,port5:10015,port6:10016,port7:10017,port8:10018,port9:10019,port10:10020",
}
```
返回
```
{
    "id": "887de78680084e4a97da2ca0108e9a22",
    "changeVersion": 0,
    "createdBy": "SYSTEM",
    "createdDate": 1740319938000,
    "lastModifiedBy": "SYSTEM",
    "lastModifiedDate": 1740319938000,
    "username": "admin",
    "password": "",
    "mobile": "13888888888",
    "status": true,
    "roles": [
        "ROLE_ADMIN",
        "ROLE_USER"
    ],
    "comboId": "0a1fb0ca00a04ef696eec719b4313459",
    "comboName": "Super Engineer",
    "expireTime": 1772986998000,
    "userType": "3",
    "realName": "刘书宝",
    "remark": "管理员",
    "port": "port0:vkey_password,port1:10011,port2:10012,port3:10013,port4:10014,port5:10015,port6:10016,port7:10017,port8:10018,port9:10019,port10:10020",
    "online": false
}
```
* 强制下线客户端  
/api/user/force-offline-client 请求方式 PUT   
```
{
    "id": "887de78680084e4a97da2ca0108e9a22"
}
```
返回
```
{
    "id": "887de78680084e4a97da2ca0108e9a22",
    "changeVersion": 0,
    "createdBy": "SYSTEM",
    "createdDate": 1740319938000,
    "lastModifiedBy": "SYSTEM",
    "lastModifiedDate": 1740319938000,
    "username": "admin",
    "password": "",
    "mobile": "13888888888",
    "status": true,
    "roles": [
        "ROLE_ADMIN",
        "ROLE_USER"
    ],
    "comboId": "0a1fb0ca00a04ef696eec719b4313459",
    "comboName": "Super Engineer",
    "expireTime": 1772986998000,
    "userType": "3",
    "realName": "刘书宝",
    "remark": "管理员",
    "port": "port0:vkey_password,port1:10011,port2:10012,port3:10013,port4:10014,port5:10015,port6:10016,port7:10017,port8:10018,port9:10019,port10:10020",
    "online": false
}
```

* 强制下线服务端  
/api/user/force-offline-server 请求方式 PUT  
```
{
    "id": "887de78680084e4a97da2ca0108e9a22"
}
```
返回
```
{
    "id": "887de78680084e4a97da2ca0108e9a22",
    "changeVersion": 0,
    "createdBy": "SYSTEM",
    "createdDate": 1740319938000,
    "lastModifiedBy": "SYSTEM",
    "lastModifiedDate": 1740319938000,
    "username": "admin",
    "password": "",
    "mobile": "13888888888",
    "status": true,
    "roles": [
        "ROLE_ADMIN",
        "ROLE_USER"
    ],
    "comboId": "0a1fb0ca00a04ef696eec719b4313459",
    "comboName": "Super Engineer",
    "expireTime": 1772986998000,
    "userType": "3",
    "realName": "刘书宝",
    "remark": "管理员",
    "port": "port0:vkey_password,port1:10011,port2:10012,port3:10013,port4:10014,port5:10015,port6:10016,port7:10017,port8:10018,port9:10019,port10:10020",
    "online": false
}
```

* 强制下线客户端和服务端  
/api/user/force-offline 请求方式 PUT  
```
{
    "id": "887de78680084e4a97da2ca0108e9a22"
}
```
返回
```
{
    "id": "887de78680084e4a97da2ca0108e9a22",
    "changeVersion": 0,
    "createdBy": "SYSTEM",
    "createdDate": 1740319938000,
    "lastModifiedBy": "SYSTEM",
    "lastModifiedDate": 1740319938000,
    "username": "admin",
    "password": "",
    "mobile": "13888888888",
    "status": true,
    "roles": [
        "ROLE_ADMIN",
        "ROLE_USER"
    ],
    "comboId": "0a1fb0ca00a04ef696eec719b4313459",
    "comboName": "Super Engineer",
    "expireTime": 1772986998000,
    "userType": "3",
    "realName": "刘书宝",
    "remark": "管理员",
    "port": "port0:vkey_password,port1:10011,port2:10012,port3:10013,port4:10014,port5:10015,port6:10016,port7:10017,port8:10018,port9:10019,port10:10020",
    "online": false
}
```



* 全球加速vpn列表  
/api/program/vpn/getVpnPagingListByKeywordAndVpnType?keyword=&vpnType=&pageNo=1&pageSize=10 请求方式 GET  
返回
```
{
    "data": [
        {
            "id": "ff82fd68493b4f609eae87450d949525",
            "changeVersion": 0,
            "createdBy": "SYSTEM",
            "createdDate": 1742130331000,
            "lastModifiedBy": "SYSTEM",
            "lastModifiedDate": 1742130331000,
            "vpnName": "11111",
            "vpnType": 1,
            "vpnIp": "111.111.111.111",
            "vpnIPSec": "fffff",
            "username": "vpnserver",
            "password": "testxte",
            "vpnDesc": "描述"
        }
    ],
    "paging": {
        "firstPage": 1,
        "lastPage": 1,
        "nextPage": 0,
        "prevPage": 0,
        "currentPage": 1,
        "totalPage": 1,
        "rowCount": 1,
        "pageSize": 10,
        "hasNext": false,
        "hasPrev": false,
        "hasFirst": true,
        "hasLast": true,
        "startOffset": 0
    }
}
```

* 全球加速vpn详情  
/api/program/vpn/ff82fd68493b4f609eae87450d949525 请求方式 GET  
返回
```
{
    "id": "ff82fd68493b4f609eae87450d949525",
    "changeVersion": 0,
    "createdBy": "SYSTEM",
    "createdDate": 1742130331000,
    "lastModifiedBy": "SYSTEM",
    "lastModifiedDate": 1742130331000,
    "vpnName": "11111",
    "vpnType": 1,
    "vpnIp": "111.111.111.111",
    "vpnIPSec": "fffff",
    "username": "vpnserver",
    "password": "testxte",
    "vpnDesc": "描述"
}
```

* 添加全球加速vpn  
/api/program/vpn/addVpn 请求方式 POST
```
{
    "vpnName": "222",
    "vpnType": 2,
    "vpnIp": "222.222.222.222",
    "vpnIPSec": "cccccc",
    "username": "vpnserver2",
    "password": "testxte123",
    "vpnDesc": "描述2"
}
```
返回
```
{
    "id": "8485bd76ae0b4b768c28706b2245b505",
    "createdBy": "admin",
    "createdDate": 1742131090242,
    "lastModifiedBy": "admin",
    "lastModifiedDate": 1742131090242,
    "vpnName": "222",
    "vpnType": 2,
    "vpnIp": "222.222.222.222",
    "vpnIPSec": "cccccc",
    "username": "vpnserver2",
    "password": "testxte123",
    "vpnDesc": "描述2"
}
```

* 修改全球加速vpn  
/api/program/vpn/editVpn 请求方式 PUT
```
{
    "id": "8485bd76ae0b4b768c28706b2245b505",
    "vpnName": "222edit",
    "vpnType": 2,
    "vpnIp": "222.222.222.222",
    "vpnIPSec": "cccccc",
    "username": "vpnserver2",
    "password": "testxte123",
    "vpnDesc": "描述2"
}
```
返回
```
{
    "id": "8485bd76ae0b4b768c28706b2245b505",
    "lastModifiedBy": "admin",
    "lastModifiedDate": 1742131198570,
    "vpnName": "222edit",
    "vpnType": 2,
    "vpnIp": "222.222.222.222",
    "vpnIPSec": "cccccc",
    "username": "vpnserver2",
    "password": "testxte123",
    "vpnDesc": "描述2"
}
```

* 删除全球加速vpn  
/api/program/vpn/deleteVpn/ff82fd68493b4f609eae87450d949525 请求方式 DELETE  
  返回
```

