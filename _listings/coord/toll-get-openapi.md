---
swagger: "2.0"
x-collection-name: Coord
x-complete: 0
info:
  title: Coord Tolls API Get all tolls in an area defined by a center location and
    a radius
  description: Returns information on all tolls within a given radius.
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
  /location:
    get:
      summary: Get a list of off-street parking locations.
      description: |-
        Find all of the locations within a given are and return their pricing information and
        (when present) availability. If the `duration_m` parameter is set, total cost for a stay
        of that duration will also be returned.
      operationId: get_locations
      x-api-path-slug: location-get
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: query
        name: duration_m
        description: The expected length of time, in minutes, that the car will remainparked
          for
      - in: query
        name: latitude
        description: Latitude to return results for
      - in: query
        name: location_ids
        description: Comma separated list of the location IDs to include in the search
      - in: query
        name: longitude
        description: Longitude to return results for
      - in: query
        name: parking_start_time
        description: The ISO-8601 formatted string representing the time when the
          vehicle will arrive atthe parking location
      - in: query
        name: radius_km
        description: Distance, in kilometers, from (latitude, longitude) we will returnresults
          for
      responses:
        200:
          description: OK
      tags:
      - List
      - Of
      - Off-street
      - Parking
      - Locations
  /location/{system_id}/{location_id}:
    get:
      summary: Get detailed information on a bike location, as a GeoJSON Feature.
      description: |-
        A bike location may be a single bike station (which can have multiple docked bikes) or a
        single dockless bike itself. All working docks are returned, but only free and rentable
        dockless bikes are returned.

        ### Example

        #### Request:
        `curl -G "https://api.coord.co/v1/bike/location/CitiBike/482?access_key="`

        #### Response:
        ```
        {
          "geometry": {
            "coordinates": [
              -73.99931783,
              40.73935542
            ],
            "type": "Point"
          },
          "id": "CitiBike-482",
          "properties": {
            "is_renting": true,
            "is_returning": true,
            "last_reported": "2018-05-17T15:41:06.000Z",
            "lat": 40.73935542,
            "location_id": "482",
            "location_type": "bike_station_dock",
            "lon": -73.99931783,
            "name": "W 15 St & 7 Ave",
            "num_bikes_available": 19,
            "num_docks_available": 19,
            "region_id": "71",
            "system_id": "CitiBike"
          },
          "type": "Feature"
        }
        ```
      operationId: get_bike_location
      x-api-path-slug: locationsystem-idlocation-id-get
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - Detailed
      - Information
      - "On"
      - Bike
      - Location
      - ""
      - As
      - GeoJSON
      - Feature
  /quote:
    get:
      summary: Get the cost of renting a bike.
      description: |-
        Provide price quotes for renting a bike. There can be multiple quotes per system, reflecting
        different options for buying membership such as single-ride, single-day, and multi-day
        passes. Please keep in mind that quotes are estimates.

        ### Example

        #### Request:
        `curl -G "https://api.coord.co/v1/bike/quote?access_key="`

        #### Response:
        ```
        [
          {
            "cost": {
              "amount": 108,
              "currency": "USD"
            },
            "id": 2,
            "max_days": 1,
            "system_id": "CitiBike",
            "tax_regions": [{
              "name": "New York City",
              "tax_rate": 0.08875
            }, {
              "name": "Jersey City",
              "tax_rate": 0.07
            }],
            "usage_fees": [
              {
                "cost": {
                  "amount": 200,
                  "currency": "USD"
                },
                "id": 1,
                "pass_type_id": 2,
                "prorated": false,
                "start_time_seconds": 1800
              },
              {
                "cost": 1.5,
                "fee_increment_seconds": 900,
                "prorated": false,
                "start_time_seconds": 3600
              }
            ]
          },
          {
            "cost": {
              "amount": 272,
              "currency": "USD"
            },
            "id": 3,
            "max_days": 3,
            "system_id": "CitiBike",
            "tax_regions": [{
              "name": "New York City",
              "tax_rate": 0.08875
            }, {
              "name": "Jersey City",
              "tax_rate": 0.07
            }],
            "usage_fees": [
              {
                "cost": {
                  "amount": 100,
                  "currency": "USD"
                },
                "fee_increment_seconds": 900,
                "prorated": false,
                "start_time_seconds": 1800
              }
            ]
          }
        ]
        ```
      operationId: get_quote
      x-api-path-slug: quote-get
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: query
        name: system_ids
        description: A comma separated list of the bike systems that the user wants
          quotes for
      responses:
        200:
          description: OK
      tags:
      - Cost
      - Of
      - Renting
      - Bike
  /system:
    get:
      summary: Get information on all bike systems in an area, as a GeoJSON FeatureCollection.
      description: |-
        Bike systems are individual bike share systems, often per-region.

        Information about each system is returned as a GeoJSON Feature, within a single GeoJSON
        FeatureCollection.

        See the [/system/{system_id}](#reference/0/get-information-for-a-bike-system) call for more
        details on the individual system Features.

        ### Example

        #### Request:
        `curl -G "https://api.coord.co/v1/bike/system?latitude=40.74286877312112&longitude=-73.98918628692627&radius_km=0.5&access_key="`

        #### Response:
        ```
        {
          "features": [
            {
              "geometry": {
                "coordinates": [
                  [
                    [
                      [
                        -74.055701,
                        40.707838
                      ],
                      [
                        -74.083639,
                        40.714807
                      ],
                      ...,
                      [
                        -74.055701,
                        40.707838
                      ]
                    ]
                  ]
                ],
                "type": "MultiPolygon"
              },
              "id": "CitiBike",
              "properties": {
                "is_transactable": true,
                "station_type": "dock"
              },
              "type": "Feature"
            }
          ],
          "type": "FeatureCollection"
        }
        ```
      operationId: search_bike_systems
      x-api-path-slug: system-get
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
        description: Distance, in kilometers, from (latitude, longitude) we will return
          results for
      responses:
        200:
          description: OK
      tags:
      - Information
      - "On"
      - ""
      - Bike
      - Systems
      - In
      - Area
      - ""
      - As
      - GeoJSON
      - FeatureCollection
  /system/{system_id}:
    get:
      summary: Get detailed information on a bike system, as a GeoJSON feature.
      description: |-
        Bike systems are individual bike share systems, often per-region.

        Information is returned as a GeoJSON Feature. The geometry of the GeoJSON Feature is
        a MultiPolygon that defines the system's operational area. All bike systems have an
        operational area, in which bikes may be found and parked.
        For systems that require bikes be docked, this area is somewhat arbitrary, as bikes are
        only found at stations. In this case, the operational area is roughly the city or
        jurisdiction that the system covers.
        For semi-dockless and dockless systems that allow bikes to be parked anywhere, the
        operational area is very important and strictly defined. Often there are extra fees for
        parking outside of the operational area (also known as a "catchment area"), and almost all
        bikes should be within the area.

        These bike system types are reflected in the `station_type` property.
        * `dock` - All bikes must be taken from and returned to a dock.
        * `dockless` - All bikes are only dockless.
        * `dockless_with_hub` - Bikes may be dockless, or taken from or returned to a hub.
        A hub can be an area rather than a discrete station, where a bike can be returned and
        locked but not explicitly docked. The total price of a rental may change based on whether
        a bike is returned to a hub or not.

        Areas are returned as a GeoJSON MultiPolygon since areas may be discontiguous or have
        holes.

        ### Example

        #### Request:
        `curl -G "https://api.coord.co/v1/bike/system/CitiBike?access_key="`

        #### Response:
        ```
        {
          "type": "Feature",
          "geometry": {
              "type": "MultiPolygon",
              "coordinates": [
                [
                  [ [-74.00, 40.70], [-74.00, 40.80], [-73.90, 40.80], ..., [-74.00, 40.70] ]
                ],
                ...,
                [
                  [ [-73.00, 41.70], [-73.00, 41.80], [-72.90, 41.80], ..., [-73.00, 41.70] ],
                  [ [-72.98, 41.75], [-72.98, 41.78], [-72.95, 41.78], ..., [-72.98, 41.75] ]
                ]
              ]
            },
          "id": "CitiBike",
          "properties": {
            "email": "support@coord.co",
            "phone_number": "+6789998212",
            "station_type": "dock",
            "is_transactable": "false"
          }
        }
        ```
      operationId: get_bike_system
      x-api-path-slug: systemsystem-id-get
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - Detailed
      - Information
      - "On"
      - Bike
      - System
      - ""
      - As
      - GeoJSON
      - Feature
  /bybounds/all_rules:
    get:
      summary: Find the rules for all curbs within a bounding box.
      description: Find the rules for all curbs within a bounding box..
      operationId: get_by_bounds
      x-api-path-slug: byboundsall-rules-get
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - Find
      - Rules
      - Curbs
      - Within
      - Bounding
      - Box
  /bybounds/time_rules:
    get:
      summary: Find the rules for all curbs within a bounding box at a particular
        time.
      description: Find the rules for all curbs within a bounding box at a particular
        time..
      operationId: get_at_time_by_bounds
      x-api-path-slug: byboundstime-rules-get
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - Find
      - Rules
      - Curbs
      - Within
      - Bounding
      - Box
      - At
      - Particular
      - Time
  /bycurb/{id}/all_rules:
    get:
      summary: Find the rules on single curb.
      description: Find the rules on single curb..
      operationId: get_by_curb_id
      x-api-path-slug: bycurbidall-rules-get
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - Find
      - Rules
      - "On"
      - Single
      - Curb
  /bycurb/{id}/time_rules:
    get:
      summary: Find the rules on a single curb at a certain time.
      description: Find the rules on a single curb at a certain time..
      operationId: get_at_time_by_curb_id
      x-api-path-slug: bycurbidtime-rules-get
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - Find
      - Rules
      - "On"
      - Single
      - Curb
      - At
      - Certain
      - Time
  /bylocation/all_rules:
    get:
      summary: Find the rules for curbs near a location.
      description: |-
        Find all of the curbs within a given radius of a particular point, and return all of their
        rules across all times of day, days of the week, times of year, etc.
      operationId: get_by_location
      x-api-path-slug: bylocationall-rules-get
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - Find
      - Rulescurbs
      - Near
      - Location
  /bylocation/time_rules:
    get:
      summary: Find the rules for curbs near a location at a certain time.
      description: |-
        Find the rules for a given curb at a given time and on a given day. You can also use this
        to find all of the places that it is possible to perform a given action (for instance, find
        all the loading zones, or everywhere with two-hour parking).
      operationId: get_at_time_by_location
      x-api-path-slug: bylocationtime-rules-get
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - Find
      - Rulescurbs
      - Near
      - Location
      - At
      - Certain
      - Time
  /route:
    get:
      summary: Find a route.
      description: Find possible trips between two points using either or both of
        bike-share and transit.
      operationId: route_search
      x-api-path-slug: route-get
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: query
        name: bike_systems
        description: A comma-separated list of bike systems (as named in thebike share
          API)to use when routing
      - in: query
        name: destination_latitude
        description: The latitude of the destination point
      - in: query
        name: destination_longitude
        description: The longitude of the destination point
      - in: query
        name: modes
        description: The modes we can use in returned trip options
      - in: query
        name: num_options
        description: The maximum number of different trip options we should provide
          at once
      - in: query
        name: origin_latitude
        description: The latitude of the origin point
      - in: query
        name: origin_longitude
        description: The longitude of the origin point
      - in: query
        name: priority
        description: How we choose and sort the trip options
      - in: query
        name: time
        description: The time the trip starts or ends (depending on the `time_mode`
          flag), in ISO 8601format
      - in: query
        name: time_mode
        description: Whether `time` is the requested departure time or the requested
          arrival time
      responses:
        200:
          description: OK
      tags:
      - Routes
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
  /{location_id}/session:
    get:
      summary: Retrieve a location's sessions
      description: |-
        Retrieve information about all existing sessions at a location.

        On success, the response will be a list of existing sessions. At most one will still be
        active:
        ```
          [
            {
              "id":1,
              "start_time":"2018-04-12T00:14:20.292Z",
              "end_time":"2018-04-12T04:10:13.456Z",
              "user_id":"00000000-0000-0000-0000-000000000000"
            },
            {
              "id":2,
              "start_time":"2018-04-12T00:14:20.292Z",
              "user_id":"00000000-0000-0000-0000-000000000000"
            }
          ]
        ```
      operationId: get_location_sessions
      x-api-path-slug: location-idsession-get
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - Retrieve
      - Locations
      - Sessions
    post:
      summary: Create a new session
      description: |-
        Create a new session for the specified user at this location_id. Returns it with either
        the start_time set, or a follow-on token (barcode, number, etc.) that the end user must use
        to initiate the session at the location.

        On success, the response will be the newly created session:
        ```
          {
            "id":1,
            "start_time":"2018-04-12T00:14:20.292Z",
            "user_id":"00000000-0000-0000-0000-000000000000"
          }
        ```
      operationId: post_session
      x-api-path-slug: location-idsession-post
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - New
      - Session
  /{location_id}/session/{session_id}:
    get:
      summary: Retrieve an existing session
      description: |-
        Retrieve information about an existing session. This is useful to determine if/when an
        existing session has been started or ended (via external, barcode mechanism, for example).
        It may be polled to provide live feedback to an end user.

        On success, the response will be the existing session:
        ```
          {
            "id":1,
            "start_time":"2018-04-12T00:14:20.292Z",
            "user_id":"00000000-0000-0000-0000-000000000000"
          }
        ```
      operationId: get_session
      x-api-path-slug: location-idsessionsession-id-get
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - Retrieve
      - Existing
      - Session
  /{location_id}/session/{session_id}/end:
    put:
      summary: End a previously started session
      description: |-
        End a previously started session. Note that it is invalid to call this method for sessions
        where checkout is controlled physically (those returned with a `redemption_info` field).

        On success, the response will be the existing session with billing info:
        ```
          {
            "billing_info": {
              "cost": {
                "amount": 100,
                "currency": "USD"
              }
            },
            "end_time": "2018-04-12T00:17:50.161Z",
            "id":1,
            "start_time":"2018-04-12T00:14:20.292Z",
            "user_id":"00000000-0000-0000-0000-000000000000"
          }
        ```
      operationId: end_session
      x-api-path-slug: location-idsessionsession-idend-put
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - End
      - Previously
      - Started
      - Session
  /barcode:
    post:
      summary: Create a barcode
      description: Create a barcode for a user to be scanned upon entering/exiting
        a parking lot.
      operationId: create_barcode
      x-api-path-slug: barcode-post
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: body
        name: request
        description: A request to simulate an arrival/departure associated with the
          session
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Barcode
  /session:
    get:
      summary: Retrieve a user's sessions
      description: |-
        Retrieve information about all of a user's existing sessions.

        On success, the response will be a list of existing sessions. At most one will still be
        active:
        ```
          [
            {
              "id":1,
              "start_time":"2018-04-12T00:14:20.292Z",
              "end_time":"2018-04-12T04:10:13.456Z",
              "user_id":"00000000-0000-0000-0000-000000000000"
            },
            {
              "id":2,
              "start_time":"2018-04-12T00:14:20.292Z",
              "user_id":"00000000-0000-0000-0000-000000000000"
            }
          ]
        ```
      operationId: get_user_sessions
      x-api-path-slug: session-get
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      responses:
        200:
          description: OK
      tags:
      - Retrieve
      - Users
      - Sessions
  /testing/{location_id}/{session_id}/simulate_redemption:
    post:
      summary: For test users only - Simulate a user redemption
      description: |-
        Some sessions don't automatically start when created. Instead, they are returned with
        `redemption_info`, which might be a barcode, for example, that needs to be scanned at the
        target location. For such sessions started by test users, you can use this method to
        simulate a redemption (arrival+departure). The system will behave as though a user checked
        in at a location where the session was creationg at the time you make the call and checked
        out at a time `duration_m` minutes in the future. **This method is only available for
        sessions started by test users.**
      operationId: fake_redemption
      x-api-path-slug: testinglocation-idsession-idsimulate-redemption-post
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: query
        name: No Name
      - in: body
        name: request
        description: A request to simulate an arrival/departure associated with the
          session
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - For
      - Test
      - Users
      - Only
      - '-'
      - Simulate
      - User
      - Redemption
  /location/{id}:
    get:
      summary: Get a list of off-street parking locations.
      description: |-
        Find a single locations within a given are and return their pricing information and
        (when present) availability. If the `duration_m` parameter is set, total cost for a stay
        of that duration will also be returned.
      operationId: get_location
      x-api-path-slug: locationid-get
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: query
        name: duration_m
        description: The expected length of time, in minutes, that the car will remainparked
          for
      - in: path
        name: id
        description: The ID of the parking location to retrieve
      - in: query
        name: parking_start_time
        description: The ISO-8601 formatted string representing the time when the
          vehicle will arrive atthe parking location
      responses:
        200:
          description: OK
      tags:
      - List
      - Of
      - Off-street
      - Parking
      - Locations
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