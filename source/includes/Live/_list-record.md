## List all recorded files

> Example Request

```shell
curl -X GET \
  https://#{workspace_api_domain}/api/public/v3/live/entity/dvr \
  -H 'Authorization: uap-bfd2314eac8d463395a304d3141d172b-6a641000' \
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

begin
  live = Uiza::Live.list_recorded
  puts live.first.id
  puts live.first.entityId
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
  res, status_code = Live().list_recorded()

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
  Uiza\Live::listRecorded();
} catch(\Uiza\Exception\ErrorResponse $e) {
  print($e);
}
?>
```

```java
import java.util.*;
import com.google.gson.*;

import io.uiza.Uiza;
import io.uiza.exception.*;
import io.uiza.model.Live;
import io.uiza.model.Live.*;

public class Main {

  public static void main(String[] args) {
    Uiza.workspaceApiDomain = "your-workspace-api-domain.uiza.co";
    Uiza.authorization = "your-authorization";

    try {
      JsonArray response = Live.listRecorded();
      System.out.println(response);
    } catch (UizaException e) {
      System.out.println("Status is: " + e.getStatusCode());
      System.out.println("Message is: " + e.getMessage());
      System.out.println("Description link is: " + e.getDescriptionLink());
    } catch (Exception e) {
      System.out.println(e);
    }
  }
}
```

```javascript
const uiza = require('uiza');
uiza.workspace_api_domain('your-workspace-api-domain.uiza.co');
uiza.authorization('your-authorization-key');

uiza.live.list_recorded()
  .then((res) => {
    // Identifier of record
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

params := &uiza.LiveListRecordedParams{
  Page:uiza.Int64(1),
  Limit:uiza.Int64(2),
}

response, err := live.ListRecorded(params)
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
  var result = UizaServices.Live.ListRecorded();

  Console.WriteLine(string.Format("Success Get List All Recorded Files, total record {0}", result.MetaData != null ? result.MetaData.total : 0));
  Console.ReadLine();
}
catch (UizaException ex)
{
  Console.WriteLine(ex.Message);
  Console.ReadLine();
}
```

Retrieves list of recorded file after streamed (only available when your live event has turned on Record feature)

> Example Response

```json
{
     "data": [
         {
             "id": "040df935-61c4-46f7-a41f-0a899ebaa2cc",
             "entityId": "ee122e85-553f-4621-bc77-1396191d5846",
             "channelName": "dcb8686f-d0f8-4a0f-8b92-22db339eb315",
             "feedId": "3e3b75df-e6fa-471c-b386-8f44b8a34b6c",
             "eventType": "pull",
             "startTime": "2018-12-13T16:28:29.000Z",
             "endTime": "2018-12-13T18:28:29.000Z",
             "length": "7200",
             "fileSize": "9276182",
             "extraInfo": null,
             "endpointConfig": "s3-uiza-dvr",
             "createdAt": "2018-12-13T19:28:43.000Z",
             "updatedAt": "2018-12-13T19:28:43.000Z",
             "entityName": "Christmas 2018 Holidays Special | Best Christmas Songs & Cartoons for Kids & Babies on Baby First TV"
         },
         {
             "id": "3fec45e9-932b-4efe-b97f-dc3053acaa05",
             "entityId": "47e804bc-d4e5-4442-8f1f-20341a156a70",
             "channelName": "e9034eac-4905-4f9a-8e79-c0bd67e49dd5",
             "feedId": "12830696-87e3-4209-a877-954f8f008964",
             "eventType": "pull",
             "startTime": "2018-12-13T14:14:14.000Z",
             "endTime": "2018-12-13T16:14:14.000Z",
             "length": "7200",
             "fileSize": "439858038",
             "extraInfo": null,
             "endpointConfig": "s3-uiza-dvr",
             "createdAt": "2018-12-13T17:30:42.000Z",
             "updatedAt": "2018-12-13T17:30:42.000Z",
             "entityName": "WATCH: SpaceX to Launch Falcon 9 Rocket #Spaceflight CRS16 @1:16pm EST"
         }
     ],
     "metadata": {
         "total": 2,
         "result": 2,
         "page": 1,
         "limit": 20
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

<span class="get-button"> GET </span>
```https://#{workspace_api_domain}/api/public/v3/live/entity/dvr```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| Authorization | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |


**Response Parameters**

| Parameter | Type | Description |
| ------------- | ------------- | ------------- |
| **id** | **string** | Identifier of record |
| **entityId** | **string** | Entity's ID correspond to record |
| **channelName** | **string** | Name of channel |
| **eventType** | **string** | Event type can be *pull* or *push* |
| **startTime** | **string** | Time start record |
| **endTime** | **string** | Time end record |
| **length** | **string** | Length of record |
| **entityName** | **string** | Name of live event |
