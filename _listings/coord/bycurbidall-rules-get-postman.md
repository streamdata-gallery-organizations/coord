{
  "info": {
    "name": "Coord Curb Search API Find the rules on single curb.",
    "_postman_id": "227b0db5-92ab-4c9b-9554-e698a64ae3de",
    "description": "Find the rules on single curb..",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "Find",
      "item": [
        {
          "id": "b298218d-09c0-4c72-8cb9-67b320efacd2",
          "name": "get_by_bounds",
          "request": {
            "url": "http://api.coord.co/v1/search/curbs/bybounds/all_rules?access_key=%7B%7D&No Name=%7B%7D",
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
            "description": "Find the rules for all curbs within a bounding box.."
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "5522580f-29c2-4f2b-9dd5-54e6bbd65290"
            }
          ]
        },
        {
          "id": "a1daa032-f147-45d7-aa78-3cbc7eea19bb",
          "name": "get_at_time_by_bounds",
          "request": {
            "url": "http://api.coord.co/v1/search/curbs/bybounds/time_rules?access_key=%7B%7D&No Name=%7B%7D",
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
            "description": "Find the rules for all curbs within a bounding box at a particular time.."
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "81f525b6-89f0-472d-9296-91354b49537c"
            }
          ]
        },
        {
          "id": "223916e4-6834-4d91-a603-6e7b4124f888",
          "name": "get_by_curb_id",
          "request": {
            "url": {
              "protocol": "http",
              "host": "api.coord.co",
              "path": [
                "v1",
                "search",
                "curbs",
                "bycurb/:id/all_rules"
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
                  "id": "id",
                  "value": "id",
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
            "description": "Find the rules on single curb.."
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "4f5b272b-21eb-44dd-a05e-5ca0d220a880"
            }
          ]
        }
      ]
    }
  ]
}