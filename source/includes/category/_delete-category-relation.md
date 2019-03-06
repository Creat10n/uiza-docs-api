## Delete category relation


> Example Request

```shell
curl -X DELETE \
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
  relations = Uiza::Category.delete_relation params
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
res, status_code = Category().delete_relation(
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

Uiza\Category::deleteRelation($params);
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
  JsonArray relations = Category.deleteRelation(params);
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
uiza.category.delete_relation({
  'entityId': 'c71965ac-8808-4854-8fc3-85a22ac9eb73',
  'metadataIds': ['689d3752-5515-4e35-993b-e02f370cf46c','32e8a1f4-e3b6-4369-a30d-60c6715896d1']
}).then((res) => {
    //Identifier of relation between entity and category has been deleted
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

response, _ := category.DeleteRelation(params)
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

var deleteCategoryRelationResult = UizaServices.Category.DeleteRelation(new CategoryRelationParameter()
{
  EntityId = entity.Data.id,
  MetadataIds = listMetadata
});
Console.WriteLine(string.Format("Delete Category Relation Success, total record {0}", deleteCategoryRelationResult.MetaData.result));
```

Delete  relation for entity and category

> Example Response

```json
{
    "data": [
        {
            "id": "5620ed3c-b725-4a9a-8ec1-ecc9df3e5aa6",
            "entityId": "16ab25d3-fd0f-4568-8aa0-0339bbfd674f",
            "metadataId": "095778fa-7e42-45cc-8a0e-6118e540b61d"
        },
    ],
    "metadata": {
        "total": 1,
        "result": 1,
        "page": 1,
        "limit": 20
    },
    "version": 3,
    "datetime": "2018-06-18T07:37:39.920Z",
    "policy": "public",
    "requestId": "393b0fcc-06fa-49b0-84d8-07a6acb8d1a8",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="delete-button"> DELETE </span>
```https://#{workspace_api_domain}/api/public/v3/media/entity/related/metadata```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| **Authorization** | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **entityId** | *string* | Identifier of entity |
| **metadataIds** | *string* | Identifier of category |


**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of relation between entity and category has been deleted |
| **entityId** | *string* | Identifier of entity |
| **metadataIds** | *string* | Identifier of category |
