## Delete an user

> Example Request

```shell
curl -X DELETE \
  https://#{workspace_api_domain}/api/public/v3/admin/user \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
  -d '{
	  "id":"2c98b4d5-7d7f-4a0f-9258-5689f90fd28c"
}'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

begin
  user = Uiza::User.delete "your-user-id"
  puts user.id
rescue Uiza::Error::UizaError => e
  puts "description_link: #{e.description_link}"
  puts "code: #{e.code}"
  puts "message: #{e.message}"
rescue StandardError => e
  puts "message: #{e.message}"
end
```

Permanently deletes an user. It cannot be undone. Also immediately cancels all token & information of this user.

```java
import io.uiza.model.User;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

try {
  JsonObject user = User.delete("<user-id>");
  System.out.println(user.get("id"));
} catch (UizaException e) {
  System.out.println("Status is: " + e.getStatusCode());
  System.out.println("Message is: " + e.getMessage());
  System.out.println("Description link is: " + e.getDescriptionLink());
} catch (Exception e) {

}
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

var deleteResult = UizaServices.User.Delete((string)result.Data.id);
Console.WriteLine(string.Format("Delete User Id = {0} Success", deleteResult.Data.id));
```

> Example Response

```json
{
    "data": {
        "id": "2c98b4d5-7d7f-4a0f-9258-5689f90fd28c"
    },
    "version": 3,
    "datetime": "2018-06-13T16:27:06.917Z",
    "policy": "public",
    "requestId": "b2997244-3579-4898-86ae-c0395c2db1ee",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="delete-button"> DELETE </span>
```https://#{workspace_api_domain}/api/public/v3/admin/user```

**Header Request**

| Header   | Type   | Description | Required |
|-------------|--------|-------------|---------|
| Authorization | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **id** | *integer* | Identifier of user want to delete | **Yes** |



**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of user has been deleted |
