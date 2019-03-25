## Create an user

Create an user account for workspace

> Example Request

```shell
curl -X POST \
  https://#{workspace_api_domain}/api/public/v3/admin/user \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
  -d '{
    "status":1,
    "username":"user_test",
    "email":"user_test@uiza.io",
    "fullname":"User Test",
    "avatar":"https://exemple.com/avatar.jpeg",
    "dob":"05/15/2018",
    "gender":0,
    "password":"FMpsr<4[dGPu?B#u",
    "isAdmin":1
}'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

params = {
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
  user = Uiza::User.create params
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
import uiza

from uiza.api_resources.user import User
from uiza.exceptions import ServerException

uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
uiza.authorization = "your-authorization"

user_data = {
  "status": 1,
  "username": "test_admin_pythonvn",
  "email": "user_test@uiza.io",
  "fullname": "User Test",
  "avatar": "https://exemple.com/avatar.jpeg",
  "dob": "05/15/2018",
  "gender": 0,
  "password": "FMpsr<4[dGPu?B#u",
  "isAdmin": 1
}

try:
  res, status_code = User().create(**user_data)

  print("res ", res)
except ServerException as e:
  raise e
except Exception as e:
  raise e
```

```php
<?
require __DIR__."/../vendor/autoload.php";

Uiza\Base::setWorkspaceApiDomain("your-workspace-api-domain.uiza.co");
Uiza\Base::setAuthorization("your-authorization");

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

try {
  Uiza\User::create($params);
} catch(\Uiza\Exception\ErrorResponse $e) {
  print($e);
}
?>
```

```java
import java.util.*;
import com.google.gson.*;

import io.uiza.Uiza;
import io.uiza.exception.*;
import io.uiza.model.User;
import io.uiza.model.User.*;

public class Main {

  public static void main(String[] args) {
    Uiza.workspaceApiDomain = "your-workspace-api-domain.uiza.co";
    Uiza.authorization = "your-authorization";

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
      JsonObject response = User.create(params);
      System.out.println(response);
    } catch (UizaException e) {
      System.out.println("Status is: " + e.getStatusCode());
      System.out.println("Message is: " + e.getMessage());
      System.out.println("Description link is: " + e.getDescriptionLink());
    } catch (Exception e) {
      System.out.println(e);
    }
  }
}
```

```javascript
const uiza = require('uiza');
uiza.workspace_api_domain('your-workspace-api-domain.uiza.co');
uiza.authorization('your-authorization-key');

params = {
  'status': 1,
  'username': 'user_test_1',
  'email': 'user_test@uiza.io',
  'fullname': 'User Test',
  'avatar': 'https://exemple.com/avatar.jpeg',
  'dob': '05/15/2018',
  'gender': 0,
  'password': 'FMpsr<4[dGPu?B#u',
  'isAdmin': 1
};

uiza.user.create(params).then((res) => {
  // Identifier of user has been created
}).catch((err) => {
  // Error
});
```

```go
import (
  uiza "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/user"
)

func init() {
  Uiza.WorkspaceAPIDomain = "your-workspace-api-domain.uiza.co"
  Uiza.Authorization = "your-authorization"
}

params := &uiza.UserCreateParams{
  Status: uiza.Int64(1),
  Username: uiza.String("user_test_go"),
  Email: uiza.String("user_test@uiza.io"),
  Password: uiza.String("FMpsr<4[dGPu?B#u"),
  Avatar: uiza.String("https://exemple.com/avatar.jpeg"),
  Fullname: uiza.String("User Test Go"),
  Dob: uiza.String("05/15/2018"),
  Gender: uiza.Int64(0),
  IsAdmin: uiza.Int64(1),
}
response, err := user.Create(params)
if err != nil {
  log.Printf("%v\n", err)
} else {
  log.Printf("%v\n", response)
}
```

```csharp
using System;
using Uiza.Net.Configuration;
using Uiza.Net.Enums;
using Uiza.Net.Parameters;
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  WorkspaceApiDomain = "your-workspace-api-domain.uiza.co",
  Authorization = "your-authorization"
});

try
{
  var result = UizaServices.User.Create(new CreatUserParameter()
  {
    Status = UserStatus.Active,
    UserName = Guid.NewGuid().ToString(),
    Email = string.Format("{0}@gmail.com", Guid.NewGuid().ToString()),
    PassWord = curentPW,
    FullName = Guid.NewGuid().ToString(),
    Avatar = "https://static.uiza.io/uiza_logo_128.png"
  });

  Console.WriteLine(string.Format("Create New User Id = {0} Success", result.Data.id));
  Console.ReadLine();
}
catch (UizaException ex)
{
  Console.WriteLine(ex.Message);
  Console.ReadLine();
}
```

> Example Response

```json
{
    "data": {
        "id": "37d6706e-be91-463e-b3b3-b69451dd4752"
    },
    "version": 3,
    "datetime": "2018-06-22T18:05:47.676Z",
    "policy": "public",
    "requestId": "8b0dfeed-18b6-47e6-8e18-274968c7e94b",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="post-button"> POST </span>
```https://#{workspace_api_domain}/api/public/v3/admin/user```


**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| Authorization | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **status** | *integer* | Status of account ( ``0`` = de-active, ``1`` =  active) | **Yes** |
| **username** | *string* | Username of account (used for login instead of email) | **Yes** |
| **email** | *string* | Email (used for login instead of username) | **Yes** |
| **password** | *text* | Password (from A to x , 6 to 25 characters) | **Yes** |
| **avatar** | *string* | Link of avatar ( suggest 300x300) |  |
| **fullname** | *string* | Full name of user |  |
| **dob** | *date* | Date of birth (MM/DD/YYYY) |  |
| **gender** | *integer* | Gender ( ``0`` = Male, ``1`` = Female) |  |
| **isAdmin** | *integer* | Set this account isAdmin or not (``1`` = Yes, ``0`` = No) |  |





**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of user has been created |
