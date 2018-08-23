{
  "info": {
    "name": "Coord Bike Share API Get information on all bike systems in an area, as a GeoJSON FeatureCollection.",
    "_postman_id": "67f490f2-387e-4ea1-9e3d-72af4392dfe3",
    "description": "Bike systems are individual bike share systems, often per-region.\n\nInformation about each system is returned as a GeoJSON Feature, within a single GeoJSON\nFeatureCollection.\n\nSee the [/system/{system_id}](#reference/0/get-information-for-a-bike-system) call for more\ndetails on the individual system Features.\n\n### Example\n\n#### Request:\n`curl -G \"https://api.coord.co/v1/bike/system?latitude=40.74286877312112&longitude=-73.98918628692627&radius_km=0.5&access_key=\"`\n\n#### Response:\n```\n{\n  \"features\": [\n    {\n      \"geometry\": {\n        \"coordinates\": [\n          [\n            [\n              [\n                -74.055701,\n                40.707838\n              ],\n              [\n                -74.083639,\n                40.714807\n              ],\n              ...,\n              [\n                -74.055701,\n                40.707838\n              ]\n            ]\n          ]\n        ],\n        \"type\": \"MultiPolygon\"\n      },\n      \"id\": \"CitiBike\",\n      \"properties\": {\n        \"is_transactable\": true,\n        \"station_type\": \"dock\"\n      },\n      \"type\": \"Feature\"\n    }\n  ],\n  \"type\": \"FeatureCollection\"\n}\n```",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "Bike",
      "item": [
        {
          "id": "90284134-8f81-4f25-b245-0e5d315910bc",
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
              "id": "2e450140-bbe6-4788-abfd-447c1288eccd"
            }
          ]
        }
      ]
    },
    {
      "name": "Detailed",
      "item": [
        {
          "id": "24ef3cba-939c-4b76-b3f1-e9a3184ad52f",
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
              "id": "a9c61d83-42f8-4c71-80a9-42c1856ada27"
            }
          ]
        }
      ]
    },
    {
      "name": "Cost",
      "item": [
        {
          "id": "acacc649-06b0-497e-b319-2dc627610d2c",
          "name": "get_quote",
          "request": {
            "url": "http://api.coord.co/v1/bike/quote?access_key=%7B%7D&system_ids=%7B%7D",
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
            "description": "Provide price quotes for renting a bike. There can be multiple quotes per system, reflecting\ndifferent options for buying membership such as single-ride, single-day, and multi-day\npasses. Please keep in mind that quotes are estimates.\n\n### Example\n\n#### Request:\n`curl -G \"https://api.coord.co/v1/bike/quote?access_key=\"`\n\n#### Response:\n```\n[\n  {\n    \"cost\": {\n      \"amount\": 108,\n      \"currency\": \"USD\"\n    },\n    \"id\": 2,\n    \"max_days\": 1,\n    \"system_id\": \"CitiBike\",\n    \"tax_regions\": [{\n      \"name\": \"New York City\",\n      \"tax_rate\": 0.08875\n    }, {\n      \"name\": \"Jersey City\",\n      \"tax_rate\": 0.07\n    }],\n    \"usage_fees\": [\n      {\n        \"cost\": {\n          \"amount\": 200,\n          \"currency\": \"USD\"\n        },\n        \"id\": 1,\n        \"pass_type_id\": 2,\n        \"prorated\": false,\n        \"start_time_seconds\": 1800\n      },\n      {\n        \"cost\": 1.5,\n        \"fee_increment_seconds\": 900,\n        \"prorated\": false,\n        \"start_time_seconds\": 3600\n      }\n    ]\n  },\n  {\n    \"cost\": {\n      \"amount\": 272,\n      \"currency\": \"USD\"\n    },\n    \"id\": 3,\n    \"max_days\": 3,\n    \"system_id\": \"CitiBike\",\n    \"tax_regions\": [{\n      \"name\": \"New York City\",\n      \"tax_rate\": 0.08875\n    }, {\n      \"name\": \"Jersey City\",\n      \"tax_rate\": 0.07\n    }],\n    \"usage_fees\": [\n      {\n        \"cost\": {\n          \"amount\": 100,\n          \"currency\": \"USD\"\n        },\n        \"fee_increment_seconds\": 900,\n        \"prorated\": false,\n        \"start_time_seconds\": 1800\n      }\n    ]\n  }\n]\n```"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "3702ad2e-fd32-49ef-a097-01e06fac98e7"
            }
          ]
        }
      ]
    },
    {
      "name": "Information",
      "item": [
        {
          "id": "7a9a6bc4-b511-49d6-84a3-0c0d79c07677",
          "name": "search_bike_systems",
          "request": {
            "url": "http://api.coord.co/v1/bike/system?access_key=%7B%7D&latitude=%7B%7D&longitude=%7B%7D&radius_km=%7B%7D",
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
            "description": "Bike systems are individual bike share systems, often per-region.\n\nInformation about each system is returned as a GeoJSON Feature, within a single GeoJSON\nFeatureCollection.\n\nSee the [/system/{system_id}](#reference/0/get-information-for-a-bike-system) call for more\ndetails on the individual system Features.\n\n### Example\n\n#### Request:\n`curl -G \"https://api.coord.co/v1/bike/system?latitude=40.74286877312112&longitude=-73.98918628692627&radius_km=0.5&access_key=\"`\n\n#### Response:\n```\n{\n  \"features\": [\n    {\n      \"geometry\": {\n        \"coordinates\": [\n          [\n            [\n              [\n                -74.055701,\n                40.707838\n              ],\n              [\n                -74.083639,\n                40.714807\n              ],\n              ...,\n              [\n                -74.055701,\n                40.707838\n              ]\n            ]\n          ]\n        ],\n        \"type\": \"MultiPolygon\"\n      },\n      \"id\": \"CitiBike\",\n      \"properties\": {\n        \"is_transactable\": true,\n        \"station_type\": \"dock\"\n      },\n      \"type\": \"Feature\"\n    }\n  ],\n  \"type\": \"FeatureCollection\"\n}\n```"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "358ea21b-ad90-4fe3-b6bf-78d63aa11ee2"
            }
          ]
        }
      ]
    }
  ]
}