## Update an user

> Example Request

```shell
curl -X PUT \
  https://#{workspace_api_domain}/api/public/v3/admin/user \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
  -d '{
    "id":"37d6706e-be91-463e-b3b3-b69451dd4752",
    "status":0,
    "username":"user_test",
    "email":"user_test@uiza.io",
    "avatar":"https://exemple.com/avatar.jpeg",
    "fullname":"User Test",
    "dob":"05/15/2018",
    "gender":0,
    "password":"123456789",
    "isAdmin":1
}'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

params = {
  id: "37d6706e-be91-463e-b3b3-b69451dd4752",
  status: 1,
  username: "user_test",
  email: "user_test@uiza.io",
  password: "FMpsr<4[dGPu?B#u",
  gender: 0,
  dob: "05/15/2018",
  avatar: "https://exemple.com/avatar.jpeg",
  fullname: "User Test",
  isAdmin: 0
}

begin
  user = Uiza::User.update params
  puts user.id
  puts user.username
rescue Uiza::Error::UizaError => e
  puts "description_link: #{e.description_link}"
  puts "code: #{e.code}"
  puts "message: #{e.message}"
rescue StandardError => e
  puts "message: #{e.message}"
end
```

Updates the specified user by setting the values of the parameters passed. Any parameters not provided will be left unchanged.

> Example Response

```json
{
    "data": {
        "id": "37d6706e-be91-463e-b3b3-b69451dd4752",
        "isAdmin": 1,
        "username": "user_test",
        "email": "user_test@uiza.io",
        "updatedAt": "2018-06-22T00:00:00.000Z",
        "createdAt": "2018-06-22T18:05:47.000Z"
    },
    "version": 3,
    "datetime": "2018-06-22T18:27:24.882Z",
    "policy": "public",
    "requestId": "5b7c0a49-427c-49e8-b112-820b49217a22",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="put-button"> PUT </span>
```https://#{workspace_api_domain}/api/public/v3/admin/user```

**Header Request**

| Header   | Type   | Description | Required |
|-------------|--------|-------------|---------|
| Authorization | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **id** | *string* | Identifier of user wanted to update | **Yes** |
| **status** | *integer* | Status of account ( ``0`` = de-active, ``1`` =  active) | **Yes** |
| **username** | *string* | Username of account (used for login instead of email) | **Yes** |
| **email** | *string* | Email (used for login instead of username) | **Yes** |
| **password** | *text* | Password (from a to Z, 6 to 25 characters) | **Yes** |
| **avatar** | *string* | Link of avatar (suggest 300x300) |  |
| **fullname** | *string* | Full name of user |  |
| **dob** | *date* | Date of birth (MM/DD/YYYY) |  |
| **gender** | *integer* | Gender ( ``0`` = Male, ``1`` = Female) |  |
| **isAdmin** | *integer* | Set this account isAdmin or not (``1`` = Yes, ``0`` = No) |  |



**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of user has been updated|


