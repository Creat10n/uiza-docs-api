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
callback_id = "33a86c18-f502-41a4-9c4c-d4e14efca238"

res, status_code = Callback().retrieve(callback_id)

print("id: ", res.id)
print("status_code", status_code)
```

```php
<?php
Uiza\Callback::retrieve("id callback");
?>
```

```java
import io.uiza.model.Callback;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

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
const uiza = require('../lib/uiza')('your-workspace-api-domain.uiza.co', 'your-authorization');

uiza.callback.retrieve('1b1f97f9-9afd-46d1-a2e1-f3b3896374df').then((res) => {
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
params := &uiza.CallbackIDParams{ID: uiza.String("Your ID")}
response, _ := callback.Retrieve(params)
log.Printf("%v\n", response)
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  ApiKey = "your-ApiKey",
  ApiBase = "your-workspace-api-domain.uiza.co"
});

var retrieveResult = UizaServices.Callback.Retrieve((string)createResult.Data.id);
Console.WriteLine(string.Format("Get Callback Id = {0} Success", retrieveResult.Data.id));
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
