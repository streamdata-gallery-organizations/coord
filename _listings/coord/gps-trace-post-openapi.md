---
swagger: "2.0"
x-collection-name: Coord
x-complete: 0
info:
  title: Coord Tolls API Get toll rates corresponding to a sequence of timestamped
    GPS locations
  description: |-
    Returns information about the toll cost of a route given the GPS trace along the route.

    Below is an example of a request:
    ```json
    {
      "locations": [
        {
          "timestamp": "2017-07-28T17:39:00.000Z",
          "lat": 47.28348,
          "lng": -122.56066
        },
        {
          "timestamp": "2017-07-28T17:39:30.000Z",
          "lat": 47.28154,
          "lng": -122.56069
        },
        {
          "timestamp": "2017-07-28T17:40:00.000Z",
          "lat": 47.28000,
          "lng": -122.56075
        },
        {
          "timestamp": "2017-07-28T17:40:30.000Z",
          "lat": 47.27901,
          "lng": -122.56081
        },
        {
          "timestamp": "2017-07-28T17:41:00.000Z",
          "lat": 47.27900,
          "lng": -122.56081
        },
        {
          "timestamp": "2017-07-28T17:41:30.000Z",
          "lat": 47.27831,
          "lng": -122.56082
        },
        {
          "timestamp": "2017-07-28T17:42:00.000Z",
          "lat": 47.27823,
          "lng": -122.56082
        },
        {
          "timestamp": "2017-07-28T17:42:30.000Z",
          "lat": 47.27798,
          "lng": -122.56082
        }
      ],
      "vehicle": {
        "axles": 2
      }
    }
    ```

    The order of the `coordinates` and `timestamps` matters. Also, `coordinates` are
    one-to-one mapped to `timestamps`. The response would look like:
      ```json
      [
        {
          "checkpoints": [
              {
                  "end": {
                      "lat": 42.348327,
                      "lng": -71.103810
                  },
                  "start": {
                      "lat": 42.348411,
                      "lng": -71.104341
                  }
              }
          ],
          "estimated_cross_time": "2014-11-06T17:08:36.000Z",
          "id": 1467,
          "name": "Allston (EB)",
          "prices": [...],
          "roadway_name": "Massachusetts Turnpike"
        }
      ]
      ```
  version: 1.0.0
host: api.coord.co
basePath: /v1/search/tolling
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /gps_trace:
    post:
      summary: Get toll rates corresponding to a sequence of timestamped GPS locations
      description: |-
        Returns information about the toll cost of a route given the GPS trace along the route.

        Below is an example of a request:
        ```json
        {
          "locations": [
            {
              "timestamp": "2017-07-28T17:39:00.000Z",
              "lat": 47.28348,
              "lng": -122.56066
            },
            {
              "timestamp": "2017-07-28T17:39:30.000Z",
              "lat": 47.28154,
              "lng": -122.56069
            },
            {
              "timestamp": "2017-07-28T17:40:00.000Z",
              "lat": 47.28000,
              "lng": -122.56075
            },
            {
              "timestamp": "2017-07-28T17:40:30.000Z",
              "lat": 47.27901,
              "lng": -122.56081
            },
            {
              "timestamp": "2017-07-28T17:41:00.000Z",
              "lat": 47.27900,
              "lng": -122.56081
            },
            {
              "timestamp": "2017-07-28T17:41:30.000Z",
              "lat": 47.27831,
              "lng": -122.56082
            },
            {
              "timestamp": "2017-07-28T17:42:00.000Z",
              "lat": 47.27823,
              "lng": -122.56082
            },
            {
              "timestamp": "2017-07-28T17:42:30.000Z",
              "lat": 47.27798,
              "lng": -122.56082
            }
          ],
          "vehicle": {
            "axles": 2
          }
        }
        ```

        The order of the `coordinates` and `timestamps` matters. Also, `coordinates` are
        one-to-one mapped to `timestamps`. The response would look like:
          ```json
          [
            {
              "checkpoints": [
                  {
                      "end": {
                          "lat": 42.348327,
                          "lng": -71.103810
                      },
                      "start": {
                          "lat": 42.348411,
                          "lng": -71.104341
                      }
                  }
              ],
              "estimated_cross_time": "2014-11-06T17:08:36.000Z",
              "id": 1467,
              "name": "Allston (EB)",
              "prices": [...],
              "roadway_name": "Massachusetts Turnpike"
            }
          ]
          ```
      operationId: get_cost_for_gps_trace
      x-api-path-slug: gps-trace-post
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: body
        name: body
        description: A sequence of timestamped GPS locations in chronological order
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Gps
      - Trace
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---