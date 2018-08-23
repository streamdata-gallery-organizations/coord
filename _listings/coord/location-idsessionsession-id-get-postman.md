{
  "info": {
    "name": "Coord Parking Access API Retrieve an existing session",
    "_postman_id": "dd234cf6-652a-4429-b257-f3fd8519d1c0",
    "description": "Retrieve information about an existing session. This is useful to determine if/when an\nexisting session has been started or ended (via external, barcode mechanism, for example).\nIt may be polled to provide live feedback to an end user.\n\nOn success, the response will be the existing session:\n```\n  {\n    \"id\":1,\n    \"start_time\":\"2018-04-12T00:14:20.292Z\",\n    \"user_id\":\"00000000-0000-0000-0000-000000000000\"\n  }\n```",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "Retrieve",
      "item": [
        {
          "id": "a1b84c18-9742-4238-87f4-8d0aaa449863",
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
              "id": "a8458d80-c87f-4ee5-96bf-af08c06f9c36"
            }
          ]
        },
        {
          "id": "5bea4dac-178e-4bdb-bd8a-43ff1e83470f",
          "name": "get_session",
          "request": {
            "url": {
              "protocol": "http",
              "host": "api.coord.co",
              "path": [
                "v1",
                "access",
                "parking",
                ":location_id/session/:session_id"
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
                },
                {
                  "id": "session_id",
                  "value": "session_id",
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
            "description": "Retrieve information about an existing session. This is useful to determine if/when an\nexisting session has been started or ended (via external, barcode mechanism, for example).\nIt may be polled to provide live feedback to an end user.\n\nOn success, the response will be the existing session:\n```\n  {\n    \"id\":1,\n    \"start_time\":\"2018-04-12T00:14:20.292Z\",\n    \"user_id\":\"00000000-0000-0000-0000-000000000000\"\n  }\n```"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "f2cb07ae-fa1d-4dda-9055-43f29c10f306"
            }
          ]
        }
      ]
    },
    {
      "name": "New",
      "item": [
        {
          "id": "9a765a5e-44c7-4a3f-9873-d58dfc13eb63",
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
              "id": "b127d709-a65a-49a4-85f2-b3e42d6ab810"
            }
          ]
        }
      ]
    }
  ]
}