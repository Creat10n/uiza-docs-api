## Update an user

Updates the specified user by setting the values of the parameters passed. Any parameters not provided will be left unchanged.

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

```python
res, status_code = User().update(id="33a86c18-f502-41a4-9c4c-d4e14efca238", status=1)

print("id: ", res.id)
print("status_code", status_code)
```

```php
<?
$params = [
  "status"  => 1,
  "username" => "test",
  "email" => "abc_test@uiza.io",
  "fullname" => "Test",
  "avatar" => "https://exemple.com/avatar.jpeg",
  "dob" => "05/15/2018",
  "gender" => 0,
  "password" => "FMpsr<4[dGPu?B#u",
  "isAdmin" => 1
];

Uiza\User::update("id user", $params);
?>
```

```java
import io.uiza.model.User;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

Map<String, Object> params = new HashMap<>();
params.put("status", Status.ACTIVE.getVal());
params.put("username", "user_test");
params.put("email", "user_test@uiza.io");
params.put("fullname", "User Test");
params.put("avatar", "https://exemple.com/avatar.jpeg");
params.put("dob", "05/15/2018");
params.put("gender", Gender.MALE.getVal());
params.put("password", "FMpsr<4[dGPu?B#u");
params.put("isAdmin", Role.ADMIN.getVal());

try {
  JsonObject user = User.update("<user-id>", params);
  System.out.println(user.get("email"));
} catch (UizaException e) {
  System.out.println("Status is: " + e.getStatusCode());
  System.out.println("Message is: " + e.getMessage());
  System.out.println("Description link is: " + e.getDescriptionLink());
} catch (Exception e) {

}
```

```javascript
const uiza = require('../lib/uiza')('your-workspace-api-domain.uiza.co', 'your-authorization');

uiza.user.update({
  'id': '9e4df7c2-111d-4107-9c2e-6d2cb13c06f0',
  'status': 0,
  'username': 'user_test_110',
  'email': 'user_test@uiza.io',
  'avatar': 'https://exemple.com/avatar.jpeg',
  'fullname': 'User Test',
  'dob': '05/15/2018',
  'gender': 0,
  'password': '123456789',
  'isAdmin': 1
}).then((res) => {
  // Identifier of user wanted to update
}).catch((err) => {
  //Error
});
```

```go
import (
  uiza "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/user"
)

params := &uiza.UserUpdateParams{
  ID: uiza.String("d0b81f08-0a93-4b0e-a6b4-15027349b7d6"),
  Status: uiza.Int64(0),
  Username: uiza.String("user_test_go"),
  Email: uiza.String("user_test_go@uiza.io"),
  Password: uiza.String("FMpsr<4[dGPu?B#u"),
  Avatar: uiza.String("https://exemple.com/avatar1.jpeg"),
  Fullname: uiza.String("User Test"),
  Dob: uiza.String("02/28/2011"),
  Gender: uiza.Int64(1),
  IsAdmin: uiza.Int64(0),
}
response, _ := user.Update(params)
log.Printf("%s\n", response)
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  ApiKey = "your-ApiKey",
  ApiBase = "your-workspace-api-domain.uiza.co"
});

var result = UizaServices.User.Create(new CreatUserParameter()
{
  Status = UserStatus.Active,
  UserName = Guid.NewGuid().ToString(),
  Email = string.Format("{0}@gmail.com", Guid.NewGuid().ToString()),
  PassWord = Guid.NewGuid().ToString();,
  FullName = Guid.NewGuid().ToString(),
  Avatar = "https://static.uiza.io/uiza_logo_128.png"
});

var updateResult = UizaServices.User.Update(new UpdateUserParameter()
{
  Id = (string)result.Data.id,
  Status = UserStatus.Active,
  UserName = Guid.NewGuid().ToString(),
  Email = string.Format("{0}@gmail.com", Guid.NewGuid().ToString()),
  PassWord = Guid.NewGuid().ToString()
});

Console.WriteLine(string.Format("Update User Id = {0} Success", updateResult.Data.id));
```

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
