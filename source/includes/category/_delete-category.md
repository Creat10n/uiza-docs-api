## Delete category


> Example Request

```shell
curl -X DELETE \
  https://#{workspace_api_domain}/api/public/v3/media/metadata \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Cache-Control: no-cache' \
  -d '{
    "id":"095778fa-7e42-45cc-8a0e-6118e540b61d"
}'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

begin
  category = Uiza::Category.delete "your-category-id"
  puts category.id
rescue Uiza::Error::UizaError => e
  puts "description_link: #{e.description_link}"
  puts "code: #{e.code}"
  puts "message: #{e.message}"
rescue StandardError => e
  puts "message: #{e.message}"
end
```

```python
res, status_code = Category().delete("ddf09dd0-b7a8-4f29-92df-14dafb97b2aa")

print("id: ", res.id)
print("status_code", status_code)
```

```php
<?php
$category = Uiza\Category::retrieve("key ... ");
$category->destroy();

// or

Uiza\Category::delete("key ...");
?>
```

```java
import io.uiza.model.Category;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

try {
  JsonObject category = Category.delete("<category-id>");
  System.out.println(category.get("id"));
} catch (UizaException e) {
  System.out.println("Status is: " + e.getStatusCode());
  System.out.println("Message is: " + e.getMessage());
  System.out.println("Description link is: " + e.getDescriptionLink());
} catch (Exception e) {

}
```

```javascript
uiza.category.delete('c0d3e5f2-9ae7-4e46-94a2-29612d562db0')
  .then((res) => {
    //Identifier of category has been deleted
  }).catch((err) => {
    //Error
  });
```

```go
import (
  "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/category"
)

params := &uiza.CategoryIDParams{ID: uiza.String("Your category ID")}
response, _ := category.Delete(params)
log.Printf("%s", response)
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  ApiKey = "your-ApiKey",
  ApiBase = "your-workspace-api-domain.uiza.co"
});

var resultDelete = UizaServices.Category.Delete((string)createResult.Data.id);
Console.WriteLine(string.Format("Delete Category Id = {0} Success", resultUpdate.Data.id));
```

Delete category

> Example Response

```json
{
    "data": {
        "id": "095778fa-7e42-45cc-8a0e-6118e540b61d"
      },
    "version": 3,
    "datetime": "2018-06-16T18:56:10.713Z",
    "policy": "public",
    "requestId": "b80b7ad3-5529-4d5e-81f2-b4ca64285067",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="delete-button"> DELETE </span>
```https://#{workspace_api_domain}/api/public/v3/media/metadata```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| **Authorization** | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **id** | *string* | Identifier of category | **Yes** |


**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of category has been deleted |
