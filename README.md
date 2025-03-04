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
/program?pageNo=1&pageSize=20 请求方式 GET  
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
/programe/0ce52ed49cfd44d6a14dced94a9645d7 请求方式 GET  
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
/programe/editProgram 请求方式 PUT  
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
