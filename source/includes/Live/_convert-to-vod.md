## Convert into VOD

> Example Request

```shell
curl -X POST \
  https://#{workspace_api_domain}/api/public/v3/live/entity/dvr/convert-to-vod \
  -H 'Authorization: uap-bfd2314eac8d463395a304d3141d172b-6a641000' \
  -H 'Content-Type: application/json' \
  -d '{
	"id":"3fec45e9-932b-4efe-b97f-dc3053acaa05"
}'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

begin
  live = Uiza::Live.convert_to_vod "your-record-id" # Identifier of record (get from list record)
  puts live.id
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

from uiza.api_resources.live import Live
from uiza.exceptions import ServerException

uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
uiza.authorization = "your-authorization"

try:
  res, status_code = Live().convert_into_vod("your-record-id") # Identifier of record (get from list record)

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
  Uiza\Live::convertToVOD(["id" => "your-record-id"]); // Identifier of record (get from list record)
} catch(\Uiza\Exception\ErrorResponse $e) {
  print($e->getStatusCode);            	
}
?>
```

```java
import io.uiza.model.Live;

Uiza.workspaceApiDomain = "your-workspace-api-domain.uiza.co";
Uiza.authorization = "your-authorization";

try {
  JsonObject live = Live.convertToVod("<record-id>");
  System.out.println(live.get("id"));
} catch (UizaException e) {
  System.out.println("Status is: " + e.getStatusCode());
  System.out.println("Message is: " + e.getMessage());
  System.out.println("Description link is: " + e.getDescriptionLink());
} catch (Exception e) {

}
```

```javascript
const uiza = require('../lib/uiza')('your-workspace-api-domain.uiza.co', 'your-authorization');

uiza.live.convert_to_vod('your-record-id') // Identifier of record (get from list record)
  .then((res) => {
    // Identifier of record (get from list record)
  }).catch((err) => {
    //Error
  });
```

```go
import (
  "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/live"
)

func init() {
  Uiza.WorkspaceAPIDomain = "your-workspace-api-domain.uiza.co"
  Uiza.Authorization = "your-authorization"
}

param := &uiza.LiveIDParams{ID: uiza.String("your-recorded-id")} // Identifier of record (get from list record)
response, _ := live.ConvertToVOD(param)
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
  var convertIntoVODResult = UizaServices.Live.ConvertToVOD((string)createResult.Data.id);
  Console.WriteLine(string.Format("Convert VOD Success", convertIntoVODResult.Data.id));
}
catch (UizaException ex)
{
	var result = ex.UizaInnerException.Error;
}
```

Convert recorded file into VOD entity. After converted, your file can be stream via Uiza's CDN.

> Example Response

```json
{
    "data": {
        "id": "03739912-d781-4d5a-aaf8-7262691a5d0c"
    },
    "version": 3,
    "datetime": "2018-12-20T05:14:02.488Z",
    "policy": "public",
    "requestId": "438daa50-696f-4152-8e6d-36f0ba7ed66f",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="post-button"> POST </span>
```https://#{workspace_api_domain}/api/public/v3/live/entity/dvr/convert-to-vod```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| Authorization | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |


**Body Request**


| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of record (get from [list record](#list-record)) |

**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of entity has been converted |
