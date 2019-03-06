## Retrieve an user

Retrieves the details of an existing user. You need only supply the unique userId that was returned upon user creation.

> Example Request

```shell
curl -X GET \
  https://#{workspace_api_domain}/api/public/v3/admin/user?id=37d6706e-be91-463e-b3b3-b69451dd4752 \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

begin
  user = Uiza::User.retrieve "your-user-id"
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
user_id = "33a86c18-f502-41a4-9c4c-d4e14efca238"

res, status_code = User().retrieve(user_id)

print("id: ", res.id)
print("status_code", status_code)
```

```php
<?
Uiza\User::retrieve("id user");
?>
```

```java
import io.uiza.model.User;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

try {
  JsonObject user = User.retrieve("<user-id>");
  System.out.println(user.get("username"));
} catch (UizaException e) {
  System.out.println("Status is: " + e.getStatusCode());
  System.out.println("Message is: " + e.getMessage());
  System.out.println("Description link is: " + e.getDescriptionLink());
} catch (Exception e) {

}
```

```javascript
const uiza = require('../lib/uiza')('your-workspace-api-domain.uiza.co', 'your-authorization');

uiza.user.retrieve('55ff6888-55b7-4d5b-b090-b5b3ad511fe7')
  .then((res) => {
    // Identifier of user
  }).catch((err) => {
    //Error
  });
```

```go
import (
  uiza "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/user"
)

params := &uiza.UserIDParams{ID: uiza.String("263bbbb8-c0c9-4e1f-9123-af3a3fd46b80")}
response, _ := user.Retrieve(params)
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

var retrieveResult = UizaServices.User.Retrieve((string)result.Data.id);
Console.WriteLine(string.Format("Get User Id = {0} Success", retrieveResult.Data.id));
```

> Example Response

```json
{
    "data": [
      {
          "id": "37d6706e-be91-463e-b3b3-b69451dd4752",
          "isAdmin": 1,
          "username": "user_test",
          "email": "user_test@uiza.io",
          "updatedAt": "2018-06-22T18:05:47.000Z",
          "createdAt": "2018-06-22T18:05:47.000Z"
      },
      {
          "id": "2c98b4d5-7d7f-4a0f-9258-5689f90fd28c",
          "isAdmin": 1,
          "username": "user_test",
          "email": "user_test@uiza.io",
          "updatedAt": "2018-06-22T18:05:47.000Z",
          "createdAt": "2018-06-22T18:05:47.000Z"
      },
    ],
    "version": 3,
    "datetime": "2018-06-22T18:20:46.780Z",
    "policy": "public",
    "requestId": "428bb8be-0e42-4b62-89e9-ac45b5e3d050",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="get-button"> GET </span>
```https://#{workspace_api_domain}/api/public/v3/admin/user```

**Header Request**

| Header   | Type   | Description | Required |
|-------------|--------|-------------|---------|
| Authorization | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **id** | *string* | Identifier of user | **Yes** |



**Response Parameters**

| Parameter | Type | Description |
| ------------- | ------------- | ------------- |
| **id** | *string* | Identifier of user |
| **isAdmin** | *number* | Determine role admin of user (``0`` = Yes, ``1`` = No)  |
| **username** | *string* | Username of account (used for login instead of email) |
| **email** | *string* | Email (used for login instead of username) |
| **createdAt** | *datetime* | Time created user |
| **updatedAt** | *datetime* | Last edited time of user |
