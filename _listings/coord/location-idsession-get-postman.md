{
  "info": {
    "name": "Coord Parking Access API Retrieve a location's sessions",
    "_postman_id": "ba6363c2-3868-445e-95f7-f0e0e84034f4",
    "description": "Retrieve information about all existing sessions at a location.\n\nOn success, the response will be a list of existing sessions. At most one will still be\nactive:\n```\n  [\n    {\n      \"id\":1,\n      \"start_time\":\"2018-04-12T00:14:20.292Z\",\n      \"end_time\":\"2018-04-12T04:10:13.456Z\",\n      \"user_id\":\"00000000-0000-0000-0000-000000000000\"\n    },\n    {\n      \"id\":2,\n      \"start_time\":\"2018-04-12T00:14:20.292Z\",\n      \"user_id\":\"00000000-0000-0000-0000-000000000000\"\n    }\n  ]\n```",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "Retrieve",
      "item": [
        {
          "id": "009c757b-c773-4555-a80d-286b9ab11b0d",
          "name": "get_location_sessions",
          "request": {
            "url": {
              "protocol": "http",
              "host": "api.coord.co",
              "path": [
                "v1",
                "access",
                "parking",
                ":location_id/session"
              ],
              "query": [
                {
                  "key": "access_key",
                  "value": "%7B%7D",
                  "disabled": false
                },
                {
                  "key": "No Name",
                  "value": "%7B%7D",
                  "disabled": false
                }
              ],
              "variable": [
                {
                  "id": "location_id",
                  "value": "location_id",
                  "type": "string"
                }
              ]
            },
            "method": "GET",
            "header": [
              {
                "key": "Accept",
                "value": "*/*",
                "disabled": false
              }
            ],
            "body": {
              "mode": "raw"
            },
            "description": "Retrieve information about all existing sessions at a location.\n\nOn success, the response will be a list of existing sessions. At most one will still be\nactive:\n```\n  [\n    {\n      \"id\":1,\n      \"start_time\":\"2018-04-12T00:14:20.292Z\",\n      \"end_time\":\"2018-04-12T04:10:13.456Z\",\n      \"user_id\":\"00000000-0000-0000-0000-000000000000\"\n    },\n    {\n      \"id\":2,\n      \"start_time\":\"2018-04-12T00:14:20.292Z\",\n      \"user_id\":\"00000000-0000-0000-0000-000000000000\"\n    }\n  ]\n```"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "6b676977-92c9-443c-ad56-8f84d01121a7"
            }
          ]
        }
      ]
    }
  ]
}