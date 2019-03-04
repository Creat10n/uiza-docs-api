## Delete a record file

> Example Request

```shell
curl -X DELETE \
  https://#{workspace_api_domain}/api/public/v3/live/entity/dvr \
  -H 'Authorization: uap-bfd2314eac8d463395a304d3141d172b-6a641000' \
  -d '{
	"id":"009596b1-f751-4102-86f7-7290a9f3f0cf"
}'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

begin
  live = Uiza::Live.delete "your-record-id" #Identifier of record (get from list record)
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
res, status_code = Live().delete_recorded("ddf09dd0-b7a8-4f29-92df-14dafb97b2aa")

print("status_code", status_code)
```

```php
<?php
Uiza\Live::delete("id record ...");
?>
```

```java
import io.uiza.model.Live;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

try {
  JsonObject live = Live.delete("<record-id>");
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

uiza.live.delete('id....')
  .then((res) => {
    // Identifier of deleting a record
  }).catch((err) => {
    //Error
  });
```

```go
import (
  "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/live"
)

param := &uiza.LiveIDParams{ID: uiza.String("Your Recorded ID")}
response, _ := live.Delete(param)
log.Printf("%s\n", response)
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  ApiKey = "your-ApiKey",
  ApiBase = "your-workspace-api-domain.uiza.co"
});
var deleteRecordFileResult = UizaServices.LiveStreaming.Delete((string)createResult.Data.id);
Console.WriteLine(string.Format("Delete Live Feed Success", deleteRecordFileResult.Data.id));
```

Delete a recorded file

> Example Response

```json
{
     "data": {
         "id": "009596b1-f751-4102-86f7-7290a9f3f0cf"
     },
     "version": 3,
     "datetime": "2018-12-20T04:16:52.893Z",
     "policy": "public",
     "requestId": "f3f1b857-e6ca-4419-b610-947e62583481",
     "serviceName": "api",
     "message": "OK",
     "code": 200,
     "type": "SUCCESS"
 }
```

**HTTP Request**

<span class="delete-button"> DELETE </span>
```https://#{workspace_api_domain}/api/public/v3/live/entity/dvr```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| Authorization | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |


**Body Request**


| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of record (get from [list record](#list-record)) |

**Response Parameters**

| Parameter | Type | Description |
| ------------- | ------------- | ------------- |
| **id** | **string** | Identifier of record has been deleted |
