{
  "info": {
    "name": "Coord Curb Search API Find the rules for all curbs within a bounding box at a particular time.",
    "_postman_id": "888ef351-5dd7-438c-a6f8-2680e664cb26",
    "description": "Find the rules for all curbs within a bounding box at a particular time..",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "Find",
      "item": [
        {
          "id": "6455fe4c-f0dd-47fd-b7e1-f187cb162de5",
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
              "id": "209cca88-0bd8-463d-aa03-3789f4406283"
            }
          ]
        },
        {
          "id": "7f3fa1a8-dd8b-4155-8ddd-8cfd0774a052",
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
              "id": "b582ee53-965b-4c54-9a62-0e2804897a4a"
            }
          ]
        }
      ]
    }
  ]
}