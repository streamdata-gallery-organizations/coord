{
  "info": {
    "name": "Coord Parking Access API Create a new session",
    "_postman_id": "5844a1e2-dd9e-4b10-a277-3da38d2c2243",
    "description": "Create a new session for the specified user at this location_id. Returns it with either\nthe start_time set, or a follow-on token (barcode, number, etc.) that the end user must use\nto initiate the session at the location.\n\nOn success, the response will be the newly created session:\n```\n  {\n    \"id\":1,\n    \"start_time\":\"2018-04-12T00:14:20.292Z\",\n    \"user_id\":\"00000000-0000-0000-0000-000000000000\"\n  }\n```",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "Retrieve",
      "item": [
        {
          "id": "d5daf51e-a004-4cca-a871-d6c28a9396f3",
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
              "id": "4a0c7d57-f057-4161-9463-b7204ac81555"
            }
          ]
        }
      ]
    },
    {
      "name": "New",
      "item": [
        {
          "id": "76d97bdb-78e1-4192-b896-1ffc27c45f5d",
          "name": "post_session",
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
            "method": "POST",
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
            "description": "Create a new session for the specified user at this location_id. Returns it with either\nthe start_time set, or a follow-on token (barcode, number, etc.) that the end user must use\nto initiate the session at the location.\n\nOn success, the response will be the newly created session:\n```\n  {\n    \"id\":1,\n    \"start_time\":\"2018-04-12T00:14:20.292Z\",\n    \"user_id\":\"00000000-0000-0000-0000-000000000000\"\n  }\n```"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "b3803d1b-c472-4a0a-930b-118c2b2672fd"
            }
          ]
        }
      ]
    }
  ]
}