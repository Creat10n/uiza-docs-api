## Get view of live feed

> Example Request

```shell
curl -X GET \
  https://#{workspace_api_domain}/api/public/v3/live/entity/tracking/current-view?id=f79cd626-bd60-4ef9-9790-c2066bcbdae9 \
  -H 'Authorization: uap-a9ad1b44c05747e8870917e5ae9e956b-05a4fd49' \
  -H 'Cache-Control: no-cache'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

begin
  response = Uiza::Live.get_view "your-live-id"
  puts response.stream_name
  puts response.watchnow
  puts response.day
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
  res, status_code = Live().get_view("your-live-id")

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
  Uiza\Live::getView(["id" => "your-live-id"]);
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
  JsonObject live = Live.getView("<live-event-id>");
  System.out.println(live.get("watchnow"));
} catch (UizaException e) {
  System.out.println("Status is: " + e.getStatusCode());
  System.out.println("Message is: " + e.getMessage());
  System.out.println("Description link is: " + e.getDescriptionLink());
} catch (Exception e) {

}
```

```javascript
const uiza = require('../lib/uiza')('your-workspace-api-domain.uiza.co', 'your-authorization');

uiza.live.get_view('8bb4bb3e-0042-4be6-a5f0-25dc65145b14')
  .then((res) => {
    // Identifier of record (get from list record)
  }).catch((err) => {
    //Error
  });
```

```go
import (
  uiza "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/live"
)

func init() {
  Uiza.WorkspaceAPIDomain = "your-workspace-api-domain.uiza.co"
  Uiza.Authorization = "your-authorization"
}

params := &uiza.LiveIDParams{ID: uiza.String("your-live-id")}
response, _ := live.GetView(params)
log.Printf("%s\n", response)
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
  var getViewResult = UizaServices.Live.GetView((string)createResult.Data.id);
  Console.WriteLine(string.Format("Get View Live Feed Success", getViewResult.Data.id));
}
catch (UizaException ex)
{
	var result = ex.UizaInnerException.Error;
}
```

This API use to get a live view status . This view only show when event has been started and being processing.

> Example Response

```json
{
    "data": {
        "stream_name": "peppa-pig-english-episodes",
        "watchnow": 1,
        "day": 1533271205999
    },
    "version": 3,
    "datetime": "2018-08-03T04:40:27.804Z",
    "policy": "public",
    "requestId": "9f52c11d-c495-4d57-9129-baad2ab28b49",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="get-button"> GET </span>
```https://#{workspace_api_domain}/api/public/v3/live/entity/tracking/current-view?id=f79cd626-bd60-4ef9-9790-c2066bcbdae9```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| Authorization | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **id** | *string* | EventId has been created.| **Yes** |




**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **stream_name** | *string* | Name of event|
| **day** | *number* | Timestamp while getting view |
| **watchnow** | *number* | Current view of event|
