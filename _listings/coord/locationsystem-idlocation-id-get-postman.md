{
  "info": {
    "name": "Coord Bike Share API Get detailed information on a bike location, as a GeoJSON Feature.",
    "_postman_id": "82ec3376-2b79-4df1-85a4-cf8a40c3e493",
    "description": "A bike location may be a single bike station (which can have multiple docked bikes) or a\nsingle dockless bike itself. All working docks are returned, but only free and rentable\ndockless bikes are returned.\n\n### Example\n\n#### Request:\n`curl -G \"https://api.coord.co/v1/bike/location/CitiBike/482?access_key=\"`\n\n#### Response:\n```\n{\n  \"geometry\": {\n    \"coordinates\": [\n      -73.99931783,\n      40.73935542\n    ],\n    \"type\": \"Point\"\n  },\n  \"id\": \"CitiBike-482\",\n  \"properties\": {\n    \"is_renting\": true,\n    \"is_returning\": true,\n    \"last_reported\": \"2018-05-17T15:41:06.000Z\",\n    \"lat\": 40.73935542,\n    \"location_id\": \"482\",\n    \"location_type\": \"bike_station_dock\",\n    \"lon\": -73.99931783,\n    \"name\": \"W 15 St & 7 Ave\",\n    \"num_bikes_available\": 19,\n    \"num_docks_available\": 19,\n    \"region_id\": \"71\",\n    \"system_id\": \"CitiBike\"\n  },\n  \"type\": \"Feature\"\n}\n```",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "Bike",
      "item": [
        {
          "id": "1d49b53b-bfbc-41da-ac71-0bfbf242d21a",
          "name": "search_locations",
          "request": {
            "url": "http://api.coord.co/v1/bike/location?access_key=%7B%7D&latitude=%7B%7D&longitude=%7B%7D&radius_km=%7B%7D&system_ids=%7B%7D",
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
            "description": "Get a list of locations given the input parameters. Specify a search area by radius around\na latitude and longitude, as well as any filter for specific systems. Each location will\nbe a GeoJSON Feature, and aggregated into a GeoJSON FeatureCollection.\n\n### Example\n\n#### Request:\n`curl -G \"https://api.coord.co/v1/bike/location?latitude=40.742868&longitude=-73.989186&radius_km=0.25&access_key=\"`\n\n#### Response:\n```\n{\n  \"features\": [\n    {\n      \"geometry\": {\n        \"coordinates\": [\n          -73.98918628692627,\n          40.74286877312112\n        ],\n        \"type\": \"Point\"\n      },\n      \"id\": \"CitiBike-3641\",\n      \"properties\": {\n        \"is_renting\": true,\n        \"is_returning\": true,\n        \"last_reported\": \"2018-05-17T15:39:24.000Z\",\n        \"lat\": 40.74286877312112,\n        \"location_id\": \"3641\",\n        \"location_type\": \"bike_station_dock\",\n        \"lon\": -73.98918628692627,\n        \"name\": \"Broadway & W 25 St\",\n        \"num_bikes_available\": 53,\n        \"num_docks_available\": 1,\n        \"region_id\": \"71\",\n        \"system_id\": \"CitiBike\"\n      },\n      \"type\": \"Feature\"\n    },\n    {\n      \"geometry\": {\n        \"coordinates\": [\n          -73.99144871,\n          40.74395411\n        ],\n        \"type\": \"Point\"\n      },\n      \"id\": \"CitiBike-466\",\n      \"properties\": {\n        \"is_renting\": true,\n        \"is_returning\": true,\n        \"last_reported\": \"2018-05-17T15:32:40.000Z\",\n        \"lat\": 40.74395411,\n        \"location_id\": \"466\",\n        \"location_type\": \"bike_station_dock\",\n        \"lon\": -73.99144871,\n        \"name\": \"W 25 St & 6 Ave\",\n        \"num_bikes_available\": 35,\n        \"region_id\": \"71\",\n        \"system_id\": \"CitiBike\"\n      },\n      \"type\": \"Feature\"\n    }\n  ],\n  \"type\": \"FeatureCollection\"\n}\n```"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "18ab4201-aeca-48fc-8479-1c228733bff4"
            }
          ]
        }
      ]
    },
    {
      "name": "Detailed",
      "item": [
        {
          "id": "13cdd427-ee12-4500-8710-c59f5db8efb9",
          "name": "get_bike_location",
          "request": {
            "url": {
              "protocol": "http",
              "host": "api.coord.co",
              "path": [
                "v1",
                "bike",
                "location/:system_id/:location_id"
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
                  "id": "system_id",
                  "value": "system_id",
                  "type": "string"
                },
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
            "description": "A bike location may be a single bike station (which can have multiple docked bikes) or a\nsingle dockless bike itself. All working docks are returned, but only free and rentable\ndockless bikes are returned.\n\n### Example\n\n#### Request:\n`curl -G \"https://api.coord.co/v1/bike/location/CitiBike/482?access_key=\"`\n\n#### Response:\n```\n{\n  \"geometry\": {\n    \"coordinates\": [\n      -73.99931783,\n      40.73935542\n    ],\n    \"type\": \"Point\"\n  },\n  \"id\": \"CitiBike-482\",\n  \"properties\": {\n    \"is_renting\": true,\n    \"is_returning\": true,\n    \"last_reported\": \"2018-05-17T15:41:06.000Z\",\n    \"lat\": 40.73935542,\n    \"location_id\": \"482\",\n    \"location_type\": \"bike_station_dock\",\n    \"lon\": -73.99931783,\n    \"name\": \"W 15 St & 7 Ave\",\n    \"num_bikes_available\": 19,\n    \"num_docks_available\": 19,\n    \"region_id\": \"71\",\n    \"system_id\": \"CitiBike\"\n  },\n  \"type\": \"Feature\"\n}\n```"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "dd776202-2491-4a23-866e-d1db2a80aa2a"
            }
          ]
        }
      ]
    }
  ]
}