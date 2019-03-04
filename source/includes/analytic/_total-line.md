## Total Line

> Example Request

```shell
curl -X GET \
  'https://#{workspace_api_domain}/api/public/v3/analytic/entity/video-quality/total-line-v2?start_date=2018-11-01%2008:00&end_date=2018-11-19%2014:00&metric=rebuffer_count' \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

params = {
  start_date: "YYYY-MM-DD hh:mm",
  end_date: "YYYY-MM-DD hh:mm",
  metric: "rebuffer_count"
}

begin
  response = Uiza::Analytic.get_total_line params
  puts response.first.rebuffer_count
rescue Uiza::Error::UizaError => e
  puts "description_link: #{e.description_link}"
  puts "code: #{e.code}"
  puts "message: #{e.message}"
rescue StandardError => e
  puts "message: #{e.message}"
end
```

> Example Response

```json
{
    "data": [
        {
            "date_time": 1542978000000,
            "rebuffer_count": 1.6666666666666667
        },
        {
            "date_time": 1543204800000,
            "rebuffer_count": 0.5
        },
        {
            "date_time": 1543215600000,
            "rebuffer_count": 5
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

**Get data grouped by hour (data refresh every 5 minutes).** Track video playback on any [metric](#analytic-metrics) performance, so you can know exactly what’s happening on every user’s device and debug more effectively.

``` About grouped by hour algorithm, Uiza currently support up to 16 days (it means when your time range is lower than 16 days, data response will be grouped by hour. Otherwise, it will return and to be grouped by day). In case your requested timerange doesn't have data, API won't show it in response.  ```

**HTTP Request**

<span class="get-button"> GET </span>
```https://#{workspace_api_domain}/api/public/v3/analytic/entity/video-quality/total-line-v2```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| **Authorization** | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |


**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **start_date** | *string* | Start date (UTC+0) with format: YYYY-MM-DD hh:mm (24-hour clock) | **Yes** |
| **end_date** | *string* | End date (UTC+0) with format: YYYY-MM-DD hh:mm (24-hour clock) | **Yes** |
| **metric** | *string* | You can get data of any metric from [list](#analytic-metrics) (use Slug) | **Yes** |


**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **date_time** | *timestamp* | Time point |
| **playback_failure_score** | *number* | see [list](#analytic-metrics) |
| **playback_failure_percentage** | *number* | see [list](#analytic-metrics) |
| **page_load_time** | *number* | see [list](#analytic-metrics) |
| **video_startup_time** | *number* | see [list](#analytic-metrics) |
| **player_startup_time** | *number* | see [list](#analytic-metrics) |
| **aggregate_startup_time** | *number* | see [list](#analytic-metrics) |
| **seek_latency** | *number* | see [list](#analytic-metrics) |
| **exits_before_video_start** | *number* | see [list](#analytic-metrics) |
| **rebuffer_percentage** | *number* | see [list](#analytic-metrics) |
| **rebuffer_frequency** | *number* | see [list](#analytic-metrics) |
| **rebuffer_duration** | *number* | see [list](#analytic-metrics) |
| **rebuffer_count** | *number* | see [list](#analytic-metrics) |
| **upscale_percentage** | *number* | see [list](#analytic-metrics) |
| **downscale_percentage** | *number* | see [list](#analytic-metrics) |
| **max_upscale_percentage** | *number* | see [list](#analytic-metrics) |
| **max_downscale_percentage** | *number* | see [list](#analytic-metrics) |
