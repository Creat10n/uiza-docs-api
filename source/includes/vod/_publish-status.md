## Get status publish


> Example Request

```shell
curl -X GET \
  https://#{workspace_api_domain}/api/public/v3/media/entity/publish/status?id=16ab25d3-fd0f-4568-8aa0-0339bbfd674f \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

begin
  response = Uiza::Entity.get_status_publish "your-entity-id"
  puts response.progress
  puts response.status
rescue Uiza::Error::UizaError => e
  puts "description_link: #{e.description_link}"
  puts "code: #{e.code}"
  puts "message: #{e.message}"
rescue StandardError => e
  puts "message: #{e.message}"
end
```

```python
res, status_code = Entity().get_status_publish("33a86c18-f502-41a4-9c4c-d4e14efca238")

print("status_code", status_code)
```

```php
<?php
Uiza\Entity::getStatusPublish("key ...");
?>
```

```java
import io.uiza.model.Entity;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

try {
  JsonObject response = Entity.getStatusPublish("<entity-id>");
  System.out.println(response.get("status"));
} catch (UizaException e) {
  System.out.println("Status is: " + e.getStatusCode());
  System.out.println("Message is: " + e.getMessage());
  System.out.println("Description link is: " + e.getDescriptionLink());
} catch (Exception e) {

}
```

```javascript
uiza.entity.get_status_publish({
  'id': '8c6de86e-f468-4226-b476-4f320bda225a',
}).then((res) => {
  //Progress of task publish, will be success when reach 100
  // Status of task publish (processing, success, error)
}).catch((err) => {
  //Error
});
```

```go
import (
  uiza "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/entity"
)

params := &uiza.EntityPublishParams{ID: uiza.String("Your entity ID")}
response, _ := entity.GetStatusPublish(params)
log.Printf("%s\n", response)
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  ApiKey = "your-ApiKey",
  ApiBase = "your-workspace-api-domain.uiza.co"
});

var result =  UizaServices.Entity.GetStatusPublish("Entity Id");
Console.WriteLine(string.Format("Get Status Publish Success : temp_access_id = {0} ", result.Data.status));
```

Publish entity to CDN, use for streaming

> Example Response

```json
{
    "data": {
        "progress": 0,
        "status": "processing"
    },
    "version": 3,
    "datetime": "2018-06-22T19:32:39.986Z",
    "policy": "public",
    "requestId": "70d462bd-4a2d-4b38-8bbe-3578e91ead08",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="get-button"> GET </span>
```https://#{workspace_api_domain}/api/public/v3/media/entity/publish/status```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| **Authorization** | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **id** | *string* | Identifier of entity | **Yes** |


**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **progress** | *number* | Progress of task publish, will be success when reach 100 |
| **status** | *string* | Status of task publish (processing, success, error) |
