## Create category relation


> Example Request

```shell
curl -X POST \
  https://#{workspace_api_domain}/api/public/v3/media/entity/related/metadata \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
  -d '{
    "entityId":"16ab25d3-fd0f-4568-8aa0-0339bbfd674f",
    "metadataIds":["095778fa-7e42-45cc-8a0e-6118e540b61d","e00586b9-032a-46a3-af71-d275f01b03cf"]
}'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

params = {
  entityId: "your-entity-id",
  metadataIds: ["your-category-id-1", "your-category-id-2"]
}

begin
  relations = Uiza::Category.create_relation params
  puts relations.first.id
  puts relations.first.entityId
rescue Uiza::Error::UizaError => e
  puts "description_link: #{e.description_link}"
  puts "code: #{e.code}"
  puts "message: #{e.message}"
rescue StandardError => e
  puts "message: #{e.message}"
end
```

```python
res, status_code = Category().create_relation(
  entity_id="16ab25d3-fd0f-4568-8aa0-0339bbfd674f",
  metadata_ids=["095778fa-7e42-45cc-8a0e-6118e540b61d","e00586b9-032a-46a3-af71-d275f01b03cf"]
)

print("status_code", status_code)
```

```php
<?php
$params = [
  "entityId" => "16ab25d3-fd0f-4568-8aa0-0339bbfd674f",
  "metadataIds" => ["095778fa-7e42-45cc-8a0e-6118e540b61d","e00586b9-032a-46a3-af71-d275f01b03cf"]
];

Uiza\Category::createRelation($params);
?>
```

```java
import io.uiza.model.Category;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

Map<String, Object> params = new HashMap<>();
params.put("entityId", "<entity-id>");
params.put("metadataIds", new String[] {"<category-id-1>", "<category-id-2>"});

try {
  JsonArray relations = Category.createRelation(params);
  JsonObject relation = relations.get(0).getAsJsonObject();
  System.out.println(relation.get("id"));
} catch (UizaException e) {
  System.out.println("Status is: " + e.getStatusCode());
  System.out.println("Message is: " + e.getMessage());
  System.out.println("Description link is: " + e.getDescriptionLink());
} catch (Exception e) {

}
```

```javascript
uiza.category.create_relation({
  'entityId': '16ab25d3-fd0f-4568-8aa0-0339bbfd674f',
  'metadataIds': ['095778fa-7e42-45cc-8a0e-6118e540b61d','e00586b9-032a-46a3-af71-d275f01b03cf']
}).then((res) => {
    //Identifier of relation between entity and category has been created
  }).catch((err) => {
    //Error
  });
```

```go
import (
  "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/category"
)

params := &uiza.CategoryRelationParams{
  EntityId: uiza.String("16ab25d3-fd0f-4568-8aa0-0339bbfd674f"),
  MetadataIds: []*string{
    uiza.String("095778fa-7e42-45cc-8a0e-6118e540b61d"),
    uiza.String("e00586b9-032a-46a3-af71-d275f01b03cf"),
}}

response, _ := category.CreateRelation(params)
for _, v := range response {
  log.Printf("%v\n", v)
}
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  ApiKey = "your-ApiKey",
  ApiBase = "your-workspace-api-domain.uiza.co"
});

var createCategoryRelationResult = UizaServices.Category.CreateRelation(new CategoryRelationParameter()
{
  EntityId = "Entity id",
  MetadataIds = listMetadata
});
Console.WriteLine(string.Format("Create Category Relation Success, total record {0}", createCategoryRelationResult.MetaData.result));
```

Add relation for entity and category

> Example Response

```json
{
    "data": [
        {
            "id": "5620ed3c-b725-4a9a-8ec1-ecc9df3e5aa6",
            "entityId": "16ab25d3-fd0f-4568-8aa0-0339bbfd674f",
            "metadataId": "095778fa-7e42-45cc-8a0e-6118e540b61d"
        },
        {
            "id": "47209e60-a99f-4c96-99fb-be4f858481b4",
            "entityId": "16ab25d3-fd0f-4568-8aa0-0339bbfd674f",
            "metadataId": "e00586b9-032a-46a3-af71-d275f01b03cf"
        }
    ],
    "metadata": {
        "total": 2,
        "result": 2,
        "page": 1,
        "limit": 20
    },
    "version": 3,
    "datetime": "2018-06-18T06:14:45.971Z",
    "policy": "public",
    "requestId": "137d4f7e-bdb8-4b9a-952f-a45eb4138382",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="post-button"> POST </span>
```https://#{workspace_api_domain}/api/public/v3/media/entity/related/metadata```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| **Authorization** | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **entityId** | *string* | Identifier of entity | **Yes** |
| **metadataIds** | *string* | Identifier of category | **Yes** |



**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of relation between entity and category has been created |
| **entityId** | *string* | Identifier of entity |
| **metadataIds** | *string* | Identifier of category |
