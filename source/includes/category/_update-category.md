## Update category


> Example Request

```shell
curl -X PUT \
  https://#{workspace_api_domain}/api/public/v3/media/metadata \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
  -d '{
    "id":"095778fa-7e42-45cc-8a0e-6118e540b61d",
    "name":"Folder edited",
    "type":"folder",
    "description":"Folder description new",
    "orderNumber":1,
    "icon":"/exemple.com/icon_001.png"
}'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

params = {
  id: "your-category-id",
  name: "Folder edited",
  type: "folder"
}

begin
  category = Uiza::Category.update params
  puts category.id
  puts category.name
rescue Uiza::Error::UizaError => e
  puts "description_link: #{e.description_link}"
  puts "code: #{e.code}"
  puts "message: #{e.message}"
rescue StandardError => e
  puts "message: #{e.message}"
end
```

```python
res, status_code = Category().update(id="33a86c18-f502-41a4-9c4c-d4e14efca238", name="Update title")

print("id: ", res.id)
print("status_code", status_code)
```

```php
<?php
$params = [
  "name" => "Folder edited",
  "type" => "folder"
];

Uiza\Category::update("key ..", $params);
?>
```

```java
import io.uiza.model.Category;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

Map<String, Object> params = new HashMap<>();
params.put("name", "Playlist Sample");
params.put("type", Type.PLAYLIST.toString());

try {
  JsonObject category = Category.update("<category-id>", params);
  System.out.println(category.get("id"));
} catch (UizaException e) {
  System.out.println("Status is: " + e.getStatusCode());
  System.out.println("Message is: " + e.getMessage());
  System.out.println("Description link is: " + e.getDescriptionLink());
} catch (Exception e) {

}
```

```javascript
uiza.category.update({
  'id': 'c0d3e5f2-9ae7-4e46-94a2-29612d562db0',
  'name': 'Folder sample 312',
  'type': 'folder',
  'orderNumber': 1,
  'description': 'Folder description',
  'icon': 'https://exemple.com/icon.png'
}).then((res) => {
    //Identifier of category has been updated
  }).catch((err) => {
    //Error
  });
```

```go
import (
  "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/category"
)

var typeCategory = uiza.CategoryFolderType
params := &uiza.CategoryUpdateParams{
  ID: uiza.String("Your category ID"),
  Name: uiza.String(""),
  Type: &typeCategory,
  Description:uiza.String(""),
  Icon:uiza.String(""),
  OrderNumber:uiza.Int64(2),
}

response, _ := category.Update(params)
log.Printf("%s", response)
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  ApiKey = "your-ApiKey",
  ApiBase = "your-workspace-api-domain.uiza.co"
});

var resultUpdate = UizaServices.Category.Update(new UpdateCategoryParameter()
{
  Id = createResult.Data.id,
  Name = string.Format("Category name {0}", Guid.NewGuid().ToString()),
  Type = CategoryTypes.PlayList
});

Console.WriteLine(string.Format("Update Category Id = {0} Success", resultUpdate.Data.id));
```

Update information of category

> Example Response

```json
{
    "data": {
        "id": "095778fa-7e42-45cc-8a0e-6118e540b61d"
    },
    "version": 3,
    "datetime": "2018-06-18T05:05:05.639Z",
    "policy": "public",
    "requestId": "ffc89642-8acd-4819-86ee-fec1d591017a",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="put-button"> PUT </span>
```https://#{workspace_api_domain}/api/public/v3/media/metadata```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| **Authorization** | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **id** | *string* | Identifier of category | **Yes** |
| **name** | *string* | Name of category | **Yes** |
| **type** | *enum* | Has 3 types of category [ **folder**, **playlist**, **tag** ] | **Yes** |
| **description** | *string* | Description for category |  |
| **orderNumber** | *integer* | Order number for category, lower number is higher order |  |
| **icon** | *string* | Small icon for each category |  |



**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of category has been updated |
