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
res, status_code = Entity().update(id="33a86c18-f502-41a4-9c4c-d4e14efca238", name="Update title")

print("id: ", res.id)
print("status_code", status_code)
```

```php
<?php
$entity = Uiza\Entity::retrieve("key ... ");
$entity->name = "Name change";
$entity->save();

// or

Uiza\Entity::update("key ..", ["name" => "Name change"]);
?>
```

```java
import io.uiza.model.Entity;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

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
uiza.entity.update({
  'id': '16de511f-5.......',
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
params := &uiza.EntityUpdateParams{
  ID: uiza.String("Your entity ID"),
  Name: uiza.String("Update entity name"),
}
response, _ := entity.Update(params)
log.Printf("%s\n", response)
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
	ApiKey = "your-ApiKey",
	ApiBase = "your-workspace-api-domain.uiza.co"
});

var result = uizaServices.Entity.Update(new UpdateEntityParameter()
{
	Id = "Entity Id",
	Name = "Sample update",
	Description = "Description update",
	ShortDescription = "ShortDescription update",
	Poster = "/example.com/updatePoster",
	Thumbnail = "/example.com/updateThumbnail"
});
Console.WriteLine(string.Format("Update Entity Id = {0} Success", result.Data.id));
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
