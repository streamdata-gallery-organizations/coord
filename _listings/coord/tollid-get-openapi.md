---
swagger: "2.0"
x-collection-name: Coord
x-complete: 0
info:
  title: Coord Tolls API Get the details (e.g. pricing) of a toll specified by toll's
    ID
  description: |-
    Returns full pricing and location details for a single toll location
    across all times, vehicle types, and payment methods.
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
  /route:
    post:
      summary: Get all toll rates corresponding to a single route
      description: |-
        Returns information about the cost of a particular route due to tolls.

        Below is an example of a route:
        ```json
        {
          "departure_time": "2017-07-28T17:39:43.611Z",
          "steps": [
            {
              "polyline": [
                {"lat": 47.28348, "lng": -122.56066},
                {"lat": 47.28154, "lng": -122.56069},
                {"lat": 47.28000, "lng": -122.56075},
                {"lat": 47.27901, "lng": -122.56081},
                {"lat": 47.27900, "lng": -122.56081},
                {"lat": 47.27831, "lng": -122.56082},
                {"lat": 47.27823, "lng": -122.56082},
                {"lat": 47.27798, "lng": -122.56082}
              ]
            }
          ],
          "vehicle": {
            "axles": 2
          }
        }
        ```

        If you already have a list of waypoints along a route, you can use these directly, but if
        not, you can use a routing service like

        Google's Directions API
         to estimate the cost of travel between a given origin and destination.

        For example, imagine we are interested in the
        toll cost of a route between origin `47.287741,-122.561391` and
        destination `47.258214,-122.537900` (you may use street names instead of coordinates):

        * Make a request to Google's Directions API and get the route(s)
          between these two locations, e.g.:
          ```
          https://maps.googleapis.com/maps/api/directions/json?origin=47.287741,-122.561391&destination=47.258214,-122.537900
          ```
        * The result will be a JSON which includes one or more routes where each route has one or
          more legs and each leg has one or more steps:

          Therefore, if the result of above request is:
          ```json
          {...
            "routes": [
              {...
                "legs": [
                  {...
                    "steps": [
                      {
                        "duration": {
                          "text": "2 mins",
                          "value": 117
                        },
                        "html_instructions": "Head south on WA-16 EToll road",
                        "polyline": {
                          "points": "m{r_Hnw`kVb@Qn@Up@Sr@QvAWjAO|@I^A^Mj@Ap@@v@?r@@hA@dB?bKDrHJdEJ@?hC@N?p@?`@?t@Cf@Gp@Kh@Kb@KXIVI`@O`@QXMd@WVOj@SZUf@_@b@c@l@s@vCwDfCiDjBkC~BcDlBiC|@mAZc@dPsTvCyDrEmGdEwFnDwErEiGdB}Bb@g@d@i@jBgC"
                        },
                        "travel_mode": "DRIVING"
                      },
                      {
                        "duration": {
                          "text": "1 min",
                          "value": 38
                        },
                        "html_instructions": "Take exit 4 for Jackson Ave toward 6th AveToll road",
                        "polyline": {
                          "points": "o{m_Hhh}jVJCBA@AHIx@eA\\e@^g@lAiBp@iAf@{@|D{G\\o@`@q@n@gA`C{DNYHSDQFU"
                        },
                        "travel_mode": "DRIVING"
                      }
                    ],
                  }
                ], ...
              }
            ], ...
          }
          ```
        * For each route, iterate on all steps (of all legs) and create a `RouteStep`
          for each step, so that `encoded_polyline` is filled by `polyline.points`,
          `road_name` by `html_instructions`, and `duration` by `duration.value`. The result should look like:
          ```json
          {
            "steps": [
              {
                "encoded_polyline": "m{r_Hnw`kVb@Qn@Up@Sr@QvAWjAO|@I^A^Mj@Ap@@v@?r@@hA@dB?bKDrHJdEJ@?hC@N?p@?`@?t@Cf@Gp@Kh@Kb@KXIVI`@O`@QXMd@WVOj@SZUf@_@b@c@l@s@vCwDfCiDjBkC~BcDlBiC|@mAZc@dPsTvCyDrEmGdEwFnDwErEiGdB}Bb@g@d@i@jBgC",
                "road_name": "Head south on WA-16 E",
                "duration": "117s"
              },
              {
                "encoded_polyline": "m{r_Hnw`kVb@Qn@Up@Sr@QvAWjAO|@I^A^Mj@Ap@@v@?r@@hA@dB?bKDrHJdEJ@?hC@N?p@?`@?t@Cf@Gp@Kh@Kb@KXIVI`@O`@QXMd@WVOj@SZUf@_@b@c@l@s@vCwDfCiDjBkC~BcDlBiC|@mAZc@dPsTvCyDrEmGdEwFnDwErEiGdB}Bb@g@d@i@jBgC",
                "road_name": "Take exit 4 for Jackson Ave toward 6th Ave",
                "duration": "38s"
              }
            ],
            "departure_time": "2017-07-28T17:39:43.611Z",
            "vehicle": {
              "axles": 2
            }
          }
          ```

        Note: Google's `html_instructions` is not really equivalent to `road_name` but it usually
        contains road names. For simplicity, you can use `html_instructions` as road name. If
        your router provides road names then use that instead.

        Note: In case Google's Directions API returns `n` routes you will
        need to call the Tolls API `n` times, once per route.

        Note: The order of the steps should remain the same as the order returned
        by the router.
      operationId: get_cost_for_route
      x-api-path-slug: route-post
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: body
        name: route
        description: A description of the route being taken
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Route
  /toll:
    get:
      summary: Get all tolls in an area defined by a center location and a radius
      description: Returns information on all tolls within a given radius.
      operationId: details_by_area
      x-api-path-slug: toll-get
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: query
        name: latitude
        description: Latitude to return results for
      - in: query
        name: longitude
        description: Longitude to return results for
      - in: query
        name: radius_km
        description: Distance, in kilometers, from (`latitude`, `longitude`) we will
          returnresults for
      - in: query
        name: return_geometry
        description: Should we return geometry in the response?
      - in: query
        name: return_price
        description: Should we return prices in the response?
      responses:
        200:
          description: OK
      tags:
      - Toll
  /toll/{id}:
    get:
      summary: Get the details (e.g. pricing) of a toll specified by toll's ID
      description: |-
        Returns full pricing and location details for a single toll location
        across all times, vehicle types, and payment methods.
      operationId: details_by_id
      x-api-path-slug: tollid-get
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: path
        name: id
        description: The ID of the toll location to retrieve
      - in: query
        name: return_geometry
        description: Should we return geometry in the response?
      - in: query
        name: return_price
        description: Should we return prices in the response?
      responses:
        200:
          description: OK
      tags:
      - Toll
      - Id
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