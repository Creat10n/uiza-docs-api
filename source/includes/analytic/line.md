## Line

> Example Request

```shell
curl -X GET \
  'https://#{workspace_api_domain}/api/public/v3/analytic/entity/video-quality/line?start_date=2018-11-01&end_date=2018-11-19' \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
```



> Example Response

```json
{
    "data": [
        {
            "day": 1541548800000,
            "total_view": 4
        },
        {
            "day": 1541635200000,
            "total_view": 5
        },
        {
            "day": 1541721600000,
            "total_view": 5
        },
        {
            "day": 1541980800000,
            "total_view": 1
        },
        {
            "day": 1542240000000,
            "total_view": 1
        },
        {
            "day": 1542499200000,
            "total_view": 1
        },
        {
            "day": 1542585600000,
            "total_view": 1
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

**Get data grouped by hour.** Get total view in time range. This help you to draw a line chart to visualize data

``` About grouped by hour algorithm, Uiza currently support upto 16 days (it's mean when your time range is lower than 16 days, data response will be grouped by hour. Otherwise, it will return and to be grouped by day). In case your requested timerange doesn't have data, API won't show it in response.  ```

**HTTP Request**

<span class="get-button"> GET </span>
```https://#{workspace_api_domain}/api/public/v3/analytic/entity/video-quality/line```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| **Authorization** | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |


**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **start_date** | *string* | Start date (UTC+0) with format: YYYY-MM-DD | **Yes** |
| **end_date** | *string* | End date (UTC+0) with format: YYYY-MM-DD | **Yes** |


**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **day** | *timestamp* | Time point |
| **total_view** | *number* | Total view in time range  |
