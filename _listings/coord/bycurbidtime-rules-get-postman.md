{
  "info": {
    "name": "Coord Curb Search API Find the rules on a single curb at a certain time.",
    "_postman_id": "eb917a83-8f71-4418-80ac-46fbb643d5af",
    "description": "Find the rules on a single curb at a certain time..",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "Find",
      "item": [
        {
          "id": "1d5c50bf-7be4-4bb4-bb24-496c06fc4f68",
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
              "id": "ca221298-a367-4bb3-8adb-fa54a43ce4fe"
            }
          ]
        },
        {
          "id": "cb7b66ee-0706-4933-846c-0714990d5aff",
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
              "id": "6e19062a-921d-4eaf-ab20-de350b8caecb"
            }
          ]
        },
        {
          "id": "90ff88ea-e9cf-41e9-adb8-fee63e84869b",
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
              "id": "01bdd8e0-7c7a-4f5f-87d9-4fcfbd4f152d"
            }
          ]
        },
        {
          "id": "6341ddf2-24da-43db-96e3-60c8101831bd",
          "name": "get_at_time_by_curb_id",
          "request": {
            "url": {
              "protocol": "http",
              "host": "api.coord.co",
              "path": [
                "v1",
                "search",
                "curbs",
                "bycurb/:id/time_rules"
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
            "description": "Find the rules on a single curb at a certain time.."
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "6a4d0e3d-f358-4cb0-8556-db2fd03dae15"
            }
          ]
        }
      ]
    }
  ]
}