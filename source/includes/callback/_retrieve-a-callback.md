## Retrieve a callback

> Example Request

```shell
curl -X GET \
  https://#{workspace_api_domain}/api/private/v3/media/entity/callback?id=0a6bf245-1cce-494f-a193-b5a44aa05558 \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

begin
  callback = Uiza::Callback.retrieve "your-callback-id"
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
  res, status_code = Callback().retrieve("your-callback-id")

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

try {
  Uiza\Callback::retrieve("your-callback-id");
} catch(\Uiza\Exception\ErrorResponse $e) {
  print($e->getStatusCode);            	
}
?>
```

```java
import io.uiza.model.Callback;

Uiza.workspaceApiDomain = "your-workspace-api-domain.uiza.co";
Uiza.authorization = "your-authorization";

try {
  JsonObject callback = Callback.retrieve("<callback-id>");
  System.out.println(callback.get("url"));
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

uiza.callback.retrieve('your-callback-id').then((res) => {
  //Identifier of callback has been retrieved
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

params := &uiza.CallbackIDParams{ID: uiza.String("your-callback-id")}
response, err := callback.Retrieve(params)
if err != nil {
  log.Printf("%v\n", err)
} else {
  log.Printf("%v\n", response)
}
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  WorkspaceApiDomain = "your-workspace-api-domain.uiza.co",
  Authorization = "your-authorization"
});

try
{
  var retrieveResult = UizaServices.Callback.Retrieve((string)createResult.Data.id);
  Console.WriteLine(string.Format("Get Callback Id = {0} Success", retrieveResult.Data.id));
}
catch (UizaException ex)
{
	var result = ex.UizaInnerException.Error;
}
```

Retrieves the details of an existing callback.

> Example Response

```json
{
    "data": {
        "id": "0a6bf245-1cce-494f-a193-b5a44aa05558",
        "url": "https://callback-url.uiza.co",
        "headersData": null,
        "jsonData": {
          "text": "example callback"
        },
        "method": "POST",
        "status": 1,
        "createdAt": "2018-06-23T01:27:08.000Z",
        "updatedAt": "2018-06-23T01:27:08.000Z"
    },
    "version": 3,
    "datetime": "2018-06-23T01:28:47.240Z",
    "policy": "public",
    "requestId": "eaa569a4-e11d-4615-9def-d5c95a575cc2",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="get-button"> GET </span>
```https://#{workspace_api_domain}/api/public/v3/media/entity/callback```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| Authorization | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **id** | *string* | Id of callback setting| **Yes** |


**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of callback |
| **url** | *string* | Your server URL for callback |
| **method** | *enum* | Method of callback (get-post-put..) |
| **jsonData** | *object* | Data you want you add to your callback as JSON format |
| **headersData** | *object* | Parameter of header |
