## Update password

Update password allows Admin or User update their current password.

> Example Request

```shell
curl -X PUT \
  https://#{workspace_api_domain}/api/public/v3/admin/user/changepassword \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
  -d '{
    "id":"2c98b4d5-7d7f-4a0f-9258-5689f90fd28c",
    "oldPassword":"FMpsr<4[dGPu?B#u",
    "newPassword":"S57Eb{:aMZhW=)G$"
}'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

params = {
  id: "your-user-id",
  oldPassword: "FMpsr<4[dGPu?B#u",
  newPassword: "S57Eb{:aMZhW=)G$"
}

begin
  response = Uiza::User.change_password params
  puts response.result
rescue Uiza::Error::UizaError => e
  puts "description_link: #{e.description_link}"
  puts "code: #{e.code}"
  puts "message: #{e.message}"
rescue StandardError => e
  puts "message: #{e.message}"
end
```

```python
res, status_code = User().change_password(
  id="9f1cd871-9244-48a1-a233-846a3b540741",
  old_password="S57Eb{:aMZhW=)G$",
  new_password="FMpsr<4[dGPu?B#u"
)

print("id", res.id)
print("status_code", status_code)
```

```php
<?
$params = [
  "id" => "id user",
  "oldPassword" => "FMpsr<4[dGPu?B#u",
  "newPassword" => "S57Eb{:aMZhW=)G$"
];

Uiza\User::changePassword($params);
?>
```

```java
import io.uiza.model.User;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

Map<String, Object> params = new HashMap<>();
params.put("oldPassword", "FMpsr<4[dGPu?B#u");
params.put("newPassword", "S57Eb{:aMZhW=)G$");

try {
  JsonObject user = User.changePassword("<user-id>", params);
  System.out.println(user);
} catch (UizaException e) {
  System.out.println("Status is: " + e.getStatusCode());
  System.out.println("Message is: " + e.getMessage());
  System.out.println("Description link is: " + e.getDescriptionLink());
} catch (Exception e) {

}
```

```javascript
const uiza = require('../lib/uiza')('your-workspace-api-domain.uiza.co', 'your-authorization');

uiza.user.change_password({
  'id': '263bbbb8-c0c9-4e1f-9123-af3a3fd46b80',
  'oldPassword': 'FMpsr<4[dGPu?B#u',
  'newPassword': 'S57Eb{:aMZhW=)G$'
}).then((res) => {
  // Identifier of user has been reset password
}).catch((err) => {
  //Error
});
```

```go
import (
  uiza "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/user"
)

params := &uiza.UserChangePasswordParams{
  ID: uiza.String("263bbbb8-c0c9-4e1f-9123-af3a3fd46b80"),
  OldPassword: uiza.String("FMpsr<4[dGPu?B#u"),
  NewPassword: uiza.String("S57Eb{:aMZhW=)G$"),
}
response, _ := user.ChangePassword(params)
log.Printf("%s\n", response)
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  ApiKey = "your-ApiKey",
  ApiBase = "your-workspace-api-domain.uiza.co"
});

var curentPW = Guid.NewGuid().ToString();
var result = UizaServices.User.Create(new CreatUserParameter()
{
  Status = UserStatus.Active,
  UserName = Guid.NewGuid().ToString(),
  Email = string.Format("{0}@gmail.com", Guid.NewGuid().ToString()),
  PassWord = curentPW,
  FullName = Guid.NewGuid().ToString(),
  Avatar = "https://static.uiza.io/uiza_logo_128.png"
});

var changePWResult = UizaServices.User.ChangePassword(new ChangePasswordParameter()
{
  Id = (string)result.Data.id,
  NewPassword = Guid.NewGuid().ToString(),
  OldPassWord = curentPW,
});

Console.WriteLine(string.Format("Change Password User Id = {0} Success", changePWResult.Data.id));
```

> Example Response

```json
{
    "data": {
        "id":"2c98b4d5-7d7f-4a0f-9258-5689f90fd28c"
    },
    "version": 3,
    "datetime": "2018-06-22T16:27:06.917Z",
    "policy": "public",
    "requestId": "b2997244-3579-4898-86ae-c0395c2db1ee",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="put-button"> PUT </span>
```https://#{workspace_api_domain}/api/public/v3/admin/user/changepassword```

**Header Request**

| Header   | Type   | Description | Required |
|-------------|--------|-------------|---------|
| Authorization | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**


| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
|**oldPassword**|*string*|Current password|**Yes**|
|**newPassword**|*string*|New password (from a to Z, 6 to 25 characters)|**Yes**|
|**id**|*string*| Identifier of user need reset password    <span onclick="this.classList.toggle('inactive')" class = "tool-tip inactive"><br><i>If API-key belong to Admin, input ID of user that you want to reset password. In case API-key belong to normal user, this field isn't require.</i></span>|**Yes**|



**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of user has been reset password |
