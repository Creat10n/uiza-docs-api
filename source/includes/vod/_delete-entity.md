## Delete an entity


> Example Request

```shell
curl -X DELETE \
  https://#{workspace_api_domain}/api/public/v3/media/entity \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
  -d '{
    "id": "16ab25d3-fd0f-4568-8aa0-0339bbfd674f",
}'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

begin
  entity = Uiza::Entity.delete "your-entity-id"
  puts entity.id
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

from uiza.api_resources.entity import Entity
from uiza.exceptions import ServerException

uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
uiza.authorization = "your-authorization"

try:
  res, status_code = Entity().delete("your-entity-id")

  print("id: ", res.id)
  print("status_code", status_code)
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
  Uiza\Entity::delete("your-entity-id");
} catch(\Uiza\Exception\ErrorResponse $e) {
  print($e->getStatusCode);            	
}
?>
```

```java
import io.uiza.model.Entity;

Uiza.workspaceApiDomain = "your-workspace-api-domain.uiza.co";
Uiza.authorization = "your-authorization";

try {
  JsonObject entity = Entity.delete("<entity-id>");
  System.out.println(entity.get("id"));
} catch (UizaException e) {
  System.out.println("Status is: " + e.getStatusCode());
  System.out.println("Message is: " + e.getMessage());
  System.out.println("Description link is: " + e.getDescriptionLink());
} catch (Exception e) {

}
```

```javascript
const uiza = require('../lib/uiza')('your-workspace-api-domain.uiza.co', 'your-authorization');

uiza.entity.delete({'id': 'your-entity-id'}).then((res) => {
  // Identifier of entity has been deleted
}).catch((err) => {
  //Error
});
```

```go
import (
  uiza "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/entity"
)

func init() {
  Uiza.WorkspaceAPIDomain = "your-workspace-api-domain.uiza.co"
  Uiza.Authorization = "your-authorization"
}

params := &uiza.EntityDeleteParams{ID: uiza.String("your-entity-id")}
response, _ := entity.Delete(params)
log.Printf("%v\n", response)
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
  var result = UizaServices.Entity.Delete("your-entity-id");
  Console.WriteLine(string.Format("Delete Entity Id = {0} Success", result.Data.id));
}
catch (UizaException ex)
{
	var result = ex.UizaInnerException.Error;
}
```

Delete entity

> Example Response

```json
{
    "data": {
        "id": "16ab25d3-fd0f-4568-8aa0-0339bbfd674f"
      },
    "version": 3,
    "datetime": "2018-06-16T18:56:10.713Z",
    "policy": "public",
    "requestId": "1ca5329c-08a7-4301-bddf-71f466363ff2",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="delete-button"> DELETE </span>
```https://#{workspace_api_domain}/api/public/v3/media/entity```

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
| **id** | *string* | Identifier of entity has been deleted |
