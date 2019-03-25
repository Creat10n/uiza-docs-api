## Create a callback

> Example Request

```shell
curl -X POST \
  https://#{workspace_api_domain}/api/public/v3/media/entity/callback \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -d '{
    "url":"https://callback-url.uiza.co",
    "method":"POST"
  }'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

params = {
  url: "https://callback-url.uiza.co",
  method: "POST"
}

begin
  callback = Uiza::Callback.create params
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

callback_data = {
  "url":"https://callback-url-python.uiza.co",
  "method":"GET"
}

try:
  res, status_code = Callback().create(**callback_data)

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
  Uiza\Callback::create($params);
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
  JsonObject callback = Callback.create(params);
  System.out.println(callback.get("id"));
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

uiza.callback.create({
  'url': 'https://callback-url.uiza.co',
  'method': 'POST'
}).then((res) => {
  //Identifier of callback has been created
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
params := &uiza.CallbackCreateParams{
  Url:    uiza.String("https://callback-url.uiza.co"),
  Method: &callbackMethodPOST,
}

response, err := callback.Create(params)
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
  var createResult = UizaServices.Callback.Create(new CreateCallbackParameter()
  {
    Url = "https://callback-url.uiza.co",
    Method = CallbackMethodTypes.Post,
  });

  Console.WriteLine(string.Format("Create New Callback Id = {0} Success", createResult.Data.id));
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

<span class="post-button"> POST </span>
```https://#{workspace_api_domain}/api/public/v3/media/entity/callback```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| Authorization | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **url** | *string* | Your server URL for callback | **Yes** |
| **method** | *enum* | Method of callback (get-post-put..) | **Yes** |
| **jsonData** | *object* | Extra data you want to attach in callback response |  |
| **headersData** | *object* | Add parameter to headers |  |


**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Id of callback setting |
