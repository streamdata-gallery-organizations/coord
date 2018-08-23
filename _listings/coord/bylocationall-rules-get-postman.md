{
  "info": {
    "name": "Coord Curb Search API Find the rules for curbs near a location.",
    "_postman_id": "009c26fb-6cd1-4fae-b415-4571d55661f2",
    "description": "Find all of the curbs within a given radius of a particular point, and return all of their\nrules across all times of day, days of the week, times of year, etc.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "Find",
      "item": [
        {
          "id": "d7756528-283a-4d3f-96b7-c12860ade1d2",
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
              "id": "9a188db0-5c48-44ac-80a3-95ae4a2d4e81"
            }
          ]
        },
        {
          "id": "8f836111-a167-4874-9d1c-a82a66942b41",
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
              "id": "044b022b-f0a1-4a0e-b46c-e0b589077e35"
            }
          ]
        },
        {
          "id": "7ff3a777-4eaf-479e-8000-24b5f884e095",
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
              "id": "6e350317-c034-4d5d-b88b-2f2821515b0c"
            }
          ]
        },
        {
          "id": "1a082b26-3879-4867-ae40-26dc3f73ebe2",
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
              "id": "cfddb7a0-f5d7-4216-a90b-1e7d4a169b86"
            }
          ]
        },
        {
          "id": "32e72d33-3119-4326-9e5b-be4abf18399e",
          "name": "get_by_location",
          "request": {
            "url": "http://api.coord.co/v1/search/curbs/bylocation/all_rules?access_key=%7B%7D&No Name=%7B%7D",
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
            "description": "Find all of the curbs within a given radius of a particular point, and return all of their\nrules across all times of day, days of the week, times of year, etc."
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "268f4e7f-5ba3-47b4-be11-93b75af2b8bc"
            }
          ]
        }
      ]
    }
  ]
}