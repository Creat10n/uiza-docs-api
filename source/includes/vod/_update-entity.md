## Update an entity


> Example Request

```shell
curl -X PUT \
  https://#{workspace_api_domain}/api/public/v3/media/entity \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
  -d '{
    "id": "dd934a87-3342-41fa-8cdf-6381b6d92105",
    "name": "Title edited",
    "description": "Description edited",
    "shortDescription":"001 Lorem Ipsum is simply dummy text of the printing and typesetting industry.",
    "poster":"/example.com/picture001a",
    "thumbnail":"/example.com/picture001a",
    "extendMetadata":{
        "movie_category":"action",
        "imdb_score":8.8,
        "published_year":"2018"
	}
}'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

params = {
  id: "your-entity-id",
  name: "Name edited"
}

begin
  entity = Uiza::Entity.update params
  puts entity.id
  puts entity.name
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
  res, status_code = Entity().update(id="your-entity-id", name="Update title")

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
  Uiza\Entity::update("your-enity-id", ["name" => "Name change"]);
} catch(\Uiza\Exception\ErrorResponse $e) {
  print($e);            	
}
?>
```

```java
import io.uiza.model.Entity;

Uiza.workspaceApiDomain = "your-workspace-api-domain.uiza.co";
Uiza.authorization = "your-authorization";

Map<String, Object> params = new HashMap<>();
params.put("name", "Name edited");
params.put("description", "Description edited");

try {
  JsonObject entity = Entity.update("<entity-id>", params);
  System.out.println(entity.get("id"));
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

uiza.entity.update({
  'id': 'your-entity-id',
  'name': '--Title edited--',
}).then((res) => {
  // Identifier of entity has been updated
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

params := &uiza.EntityUpdateParams{
  ID: uiza.String("your-entity-id"),
  Name: uiza.String("Update entity name"),
}
response, err := entity.Update(params)
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
  var result =uizaServices.Entity.Update(new UpdateEntityParameter()
  {
    Id = "your-entity-id",
    Name = "Sample update",
    Description = "Description update",
    ShortDescription = "ShortDescription update",
    Poster = "/example.com/updatePoster",
    Thumbnail = "/example.com/updateThumbnail"
  });

  Console.WriteLine(string.Format("Update Entity Id = {0} Success", result.Data.id));
  Console.ReadLine();
}
catch (UizaException ex)
{
  Console.WriteLine(ex.Message);
  Console.ReadLine();
}
```

Update entity's information.

> Example Response

```json
{
    "data": {
        "id": "dd934a87-3342-41fa-8cdf-6381b6d92105"
    },
    "version": 3,
    "datetime": "2018-06-15T18:52:45.755Z",
    "policy": "public",
    "requestId": "0201d964-2e57-4577-9d2c-692ec8b02f88",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="put-button"> PUT </span>
```https://#{workspace_api_domain}/api/public/v3/media/entity```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| **Authorization** | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **id** | *string* | Identifier of entity | **Yes** |
| **name** | *string* | Name of entity | |
| **description** | *text* | Full description for entity (without max-length) |  |
| **shortDescription** | *text* | Short description of entity (250 characters) |  |
| **poster** | *string* | Poster of entity |  |
| **thumbnail** | *string* | Thumbnail of entity |  |
| **extendMetadata** | *object* | Additional information of entity  <span onclick="this.classList.toggle('inactive')" class = "tool-tip inactive"><br><i> You can input additional information of entity by using [ **key** : **value** ] format. All information will show in entity detail.</i></span>|  |





**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of entity has been updated|
