{
  "info": {
    "name": "Coord Parking Search API Get a list of off-street parking locations.",
    "_postman_id": "391c0681-2b97-49a7-915a-49af115d5fd6",
    "description": "Find all of the locations within a given are and return their pricing information and\n(when present) availability. If the `duration_m` parameter is set, total cost for a stay\nof that duration will also be returned.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "List",
      "item": [
        {
          "id": "2be9a096-375f-4f10-94ae-4c6fab0424c2",
          "name": "get_locations",
          "request": {
            "url": "http://api.coord.co/v1/search/parking/location?access_key=%7B%7D&duration_m=%7B%7D&latitude=%7B%7D&location_ids=%7B%7D&longitude=%7B%7D&parking_start_time=%7B%7D&radius_km=%7B%7D",
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
            "description": "Find all of the locations within a given are and return their pricing information and\n(when present) availability. If the `duration_m` parameter is set, total cost for a stay\nof that duration will also be returned."
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "0c6fce46-885b-4867-a550-f7d2c3aa343e"
            }
          ]
        }
      ]
    }
  ]
}