## Update a callback

> Example Request

```shell
curl -X PUT \
  https://#{workspace_api_domain}/api/public/v3/media/entity/callback \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -d '{
    "url":"https://callback-url.uiza.co",
    "method":"GET"
  }'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

params = {
  id: "your-callback-id",
  url: "https://callback-url.uiza.co",
  method: "GET"
}

begin
  callback = Uiza::Callback.update params
  puts callback.id
  puts callback.url
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

from uiza.api_resources.callback import Callback
from uiza.exceptions import ServerException

uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
uiza.authorization = "your-authorization"

try:
  res, status_code = Callback().update(id="your-callback-id", method="POST")

  print("res ", res)
except ServerException as e:
  raise e
except Exception as e:
  raise e
```

```php
<?php
require __DIR__."/../vendor/autoload.php";

Uiza\Base::setWorkspaceApiDomain("your-workspace-api-domain.uiza.co");
Uiza\Base::setAuthorization("your-authorization");

$params = [
  "url" => "https://callback-url.uiza.co",
  "method" => "POST"
];

try {
  Uiza\Callback::update("your-callback-id", $params);
} catch(\Uiza\Exception\ErrorResponse $e) {
  print($e);            	
}
?>
```

```java
import io.uiza.model.Callback;

Uiza.workspaceApiDomain = "your-workspace-api-domain.uiza.co";
Uiza.authorization = "your-authorization";

Map<String, Object> params = new HashMap<>();
params.put("url", "<your-server-callback>");
params.put("method", Method.POST);

try {
  JsonObject callback = Callback.update("<callback-id>", params);
  System.out.println(callback.get("name"));
} catch (UizaException e) {
  System.out.println("Status is: " + e.getStatusCode());
  System.out.println("Message is: " + e.getMessage());
  System.out.println("Description link is: " + e.getDescriptionLink());
} catch (Exception e) {

}
```

```javascript
const uiza = require('uiza');
uiza.workspace_api_domain('your-workspace-api-domain.uiza.co');
uiza.authorization('your-authorization-key');

/** create */
uiza.callback.update({
  'id': 'your-callback-id',
  'url': 'https://callback-url.uiza.co',
  'method': 'GET'
}).then((res) => {
  //Identifier of callback has been updated
}).catch((err) => {
  //Error
});
```

```go
import (
  uiza "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/callback"
)

func init() {
  Uiza.WorkspaceAPIDomain = "your-workspace-api-domain.uiza.co"
  Uiza.Authorization = "your-authorization"
}

callbackMethodPOST := uiza.HTTPMethodPost
params := &uiza.CallbackUpdateParams{
	ID:    uiza.String("your-callback-id"),
	Url:    uiza.String("https://callback-url.uiza.commm"),
	Method: &callbackMethodPOST,
}

response, err := callback.Update(params)
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
  var result = UizaServices.Callback.Update(new UpdateCallbackParameter()
  {
    Id = "your-callback-id",
    Url = "https://callback-url.uiza.co/update",
    Method = CallbackMethodTypes.Post
  });

  Console.WriteLine(string.Format("Update Callback Id = {0} Success", result.Data.id));
  Console.ReadLine();
}
catch (UizaException ex)
{
  Console.WriteLine(ex.Message);
  Console.ReadLine();
}
```

This API will allow you setup a callback to your server when an entity is completed for upload or public

> Example Response

```json
{
    "data": {
        "id": "8b83886e-9cc3-4eab-9258-ebb16c0c73de"
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

<span class="put-button"> PUT </span>
```https://#{workspace_api_domain}/api/public/v3/media/entity/callback```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| Authorization | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **id** | *string* | Id of callback setting| **Yes** |
| **url** | *string* | Your server URL for callback |  |
| **method** | *enum* | Method of callback (get-post-put..) | |
| **jsonData** | *object* | Extra data you want to attach in callback response |  |
| **headersData** | *object* | Add parameter to headers |  |



**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Id of callback setting|
