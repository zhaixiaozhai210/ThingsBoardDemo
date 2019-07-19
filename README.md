### 获取当前租户token

> auth-login.sh

```
curl -v -X POST -d @auth-login.json http://localhost:8080/api/asset \

--header "Content-Type:application/json" \
```

> auth-login.json

```json
{
	"username":"zhaixiaozhai210@gmail.com",
	"password":"sunhaiyang210"
}
```

> response

```json
{
    "token":      "eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJ6aGFpeGlhb3poYWkyMTBAZ21haWwuY29tIiwic2NvcGVzIjpbIlRFTkFOVF9BRE1JTiJdLCJ1c2VySWQiOiI5NzViYzViMC1hOTA3LTExZTktOGNjNy04OWQzOGQ5YjhlZjgiLCJmaXJzdE5hbWUiOiLmtbfmtIsiLCJsYXN0TmFtZSI6IuWtmSIsImVuYWJsZWQiOnRydWUsImlzUHVibGljIjpmYWxzZSwidGVuYW50SWQiOiI3NzViZjA1MC1hOTA3LTExZTktOGNjNy04OWQzOGQ5YjhlZjgiLCJjdXN0b21lcklkIjoiMTM4MTQwMDAtMWRkMi0xMWIyLTgwODAtODA4MDgwODA4MDgwIiwiaXNzIjoidGhpbmdzYm9hcmQuaW8iLCJpYXQiOjE1NjM1MDAwMzIsImV4cCI6MTU2MzUwOTAzMn0.ZHfUxd3iXtsxetM9K33xi7Li3j3U9BBTTyw-No0KgmKo7hLz6QVPWk1yGGbA-MQ67pugBRfrXVuuWs3UzLF0ag"
}
```

### 添加新的资产与设备

> create-asset.sh

```
curl -v -X POST -d @create-asset.json http://localhost:8080/api/asset \
--header "Content-Type:application/json" \
--header "X-Authorization: $JWT_TOKEN"
```

**note: JWT_TOKEN使用 /api/login申请,有过期时间**

> create-asset.json

```json
{
	"name":"Field C",
	"type":"Field"
}
```

> Response

```json
{
    "id": {
        "entityType": "ASSET",
        "id": "cf195cd0-a9c8-11e9-af38-1d99b874d5dd"
    },
    "createdTime": 1563501554461,
    "additionalInfo": null,
    "tenantId": {
        "entityType": "TENANT",
        "id": "775bf050-a907-11e9-8cc7-89d38d9b8ef8"
    },
    "customerId": {
        "entityType": "CUSTOMER",
        "id": "13814000-1dd2-11b2-8080-808080808080"
    },
    "name": "Field D",
    "type": "Field"
}
```

### 为资产与设备添加关联

> create-relation.sh.

```
curl -v -X POST -d @create-relation.json http://localhost:8080/api/relation \
--header "Content-Type:application/json" \
--header "X-Authorization: $JWT_TOKEN"
```

> create-relation.json

```json
{
    "from":{
        "id":"ab5b3540-a92b-11e9-8cc7-89d38d9b8ef8",
        "entityType":"ASSET"
    },
    "type":"Contains",
    "to":{
        "entityType":"ASSET",
        "id":"ee73ded0-a936-11e9-8cc7-89d38d9b8ef8"
    }
}
```
