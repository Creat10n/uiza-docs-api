## Type

> Example Request

```shell
curl -X GET \
  'https://#{workspace_api_domain}/api/public/v3/analytic/entity/video-quality/type?start_date=2018-09-01&end_date=2018-11-25&type_filter=country' \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

params = {
  start_date: "YYYY-MM-DD hh:mm",
  end_date: "YYYY-MM-DD hh:mm",
  type_filter: "country"
}

begin
  response = Uiza::Analytic.get_type params
  puts response.first.name
  puts response.first.total_view
  puts response.first.percentage_of_view
rescue Uiza::Error::UizaError => e
  puts "description_link: #{e.description_link}"
  puts "code: #{e.code}"
  puts "message: #{e.message}"
rescue StandardError => e
  puts "message: #{e.message}"
end
```

```php
<?
$params = [
  "start_date" => "YYYY-MM-DD",
  "end_date" => "YYYY-MM-DD",
  "type_filter" => "country"
];

Uiza\Analytic::getType($params);
?>
```

```java
import io.uiza.model.Analytic;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

Map<String, Object> params = new HashMap<>();
params.put("start_date", "2019-01-01");
params.put("end_date", "2019-03-01");
params.put("type_filter", TypeFilter.COUNTRY.toString());

try {
  JsonArray analytics = Analytic.getType(params);
  JsonObject analytic = analytics.get(0).getAsJsonObject();
  System.out.println(analytic);
} catch (UizaException e) {
  System.out.println("Status is: " + e.getStatusCode());
  System.out.println("Message is: " + e.getMessage());
  System.out.println("Description link is: " + e.getDescriptionLink());
} catch (Exception e) {

}
```

> Example Response

```json
{
    "data": [
        {
            "name": "Vietnam",
            "total_view": 15,
            "percentage_of_view": 0.625
        },
        {
            "name": "Other",
            "total_view": 9,
            "percentage_of_view": 0.375
        }
    ],
    "version": 3,
    "datetime": "2018-06-18T03:17:07.022Z",
    "policy": "public",
    "requestId": "244f6f8f-4fc5-4f20-a535-e8ea4e0cab0e",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

Get data base on 5 type of filter: **country**, **device**, **title**, **player**, **os**

**HTTP Request**

<span class="get-button"> GET </span>
```https://#{workspace_api_domain}/api/public/v3/analytic/entity/video-quality/type```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| **Authorization** | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **start_date** | *string* | Start date (UTC+0) with format: YYYY-MM-DD | **Yes** |
| **end_date** | *string* | End date (UTC+0) with format: YYYY-MM-DD | **Yes** |
| **type_filter** | *enum* | Value accept: [ **country**, **device**, **title**, **player**, **os** ] | **Yes** |


**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **name** | *string* | name of filter (can be country, device name, title, player name or os) |
| **total_view** | *number* |  Total view corresponding to filter |
| **percentage_of_view** | *number* | Percentage of view corresponding to filter |
