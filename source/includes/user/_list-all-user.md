## List all users

Returns a list of your user. The users are returned sorted by creation date, with the most recent user appearing first.

If you use Admin token, you will get all the user. If you use User token, you can only get the information of that user

> Example Request

```shell
curl -X GET \
  https://#{workspace_api_domain}/api/public/v3/admin/user \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

begin
  users = Uiza::User.list
  # or users = Uiza::User.list limit: 2, page: 2
  puts users.first.id
  puts users.first.username
rescue Uiza::Error::UizaError => e
  puts "description_link: #{e.description_link}"
  puts "code: #{e.code}"
  puts "message: #{e.message}"
rescue StandardError => e
  puts "message: #{e.message}"
end
```

```python
res, status_code = User().list()

print("status_code", status_code)
```

```php
<?
Uiza\User::list();
?>
```

```java
import io.uiza.model.User;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

try {
  JsonArray users = User.list();
  JsonObject user = users.get(0).getAsJsonObject();
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

uiza.user.list().then((res) => {
  //Get list of user including all detail.
}).catch((err) => {
  //Error
});
```

```go
import (
  uiza "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/user"
)

params := &uiza.UserListParams{}
response, _ := user.List(params)
log.Printf("%s\n", response)
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  ApiKey = "your-ApiKey",
  ApiBase = "your-workspace-api-domain.uiza.co"
});

var listResult = UizaServices.User.List();
Console.WriteLine(string.Format("List User Success, total record {0}", listResult.Data.Count));
```

> Example Response

```json
{
    "data": [
        {
            "id": "1a95f752-19e0-4a2e-9951-6d1fc0adbeaf",
            "isAdmin": 0,
            "username": "user_test",
            "email": "user_test@uiza.io",
            "updatedAt": "2018-06-22T02:31:14.000Z",
            "createdAt": "2018-06-22T02:31:14.000Z"
        },
        {
            "id": "95c1229a-73e6-4ef7-98eb-e64a765c32d5",
            "isAdmin": 1,
            "username": "user_admin",
            "email": "user_admin@uiza.io",
            "updatedAt": "2018-06-22T00:00:00.000Z",
            "createdAt": "2018-06-22T02:32:29.000Z"
        }
    ],
    "metadata": {
        "total": 2,
        "result": 2,
        "page": 1,
        "limit": 20
    },
    "version": 3,
    "datetime": "2018-06-22T19:34:51.363Z",
    "policy": "public",
    "requestId": "7921f7fe-e086-4455-9ef7-fb5f1c8c2b20",
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

**Response Parameters**


| Parameter | Type | Description |
| ------------- | ------------- | ------------- |
| **id** | *string* | Identifier of user |
| **isAdmin** | *integer* | Set this account isAdmin or not (``0`` = Yes, ``1`` = No) |
| **username** | *string* | Username of account (used for login instead of email) |
| **email** | *string* | Email (used for login instead of username) |
| **createdAt** | *datetime* | Time created user |
| **updatedAt** | *datetime* | Last edited time of user |
