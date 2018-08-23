{
  "info": {
    "name": "Coord Curb Search API Find the rules for all curbs within a bounding box.",
    "_postman_id": "0e120709-b5fc-481e-b358-c62189a84a8b",
    "description": "Find the rules for all curbs within a bounding box..",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "Find",
      "item": [
        {
          "id": "e33665fc-5365-4886-ace1-3ad8bc520c27",
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
              "id": "3f80afd9-30a6-45e5-b47d-2ef7c8c03d49"
            }
          ]
        }
      ]
    }
  ]
}