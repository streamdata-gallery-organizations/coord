---
name: Coord
x-slug: coord
description: Coord is a mobility company that creates seamless mobility and self-driving
  experiences today through deep integrations. The company offers bike-share API,
  Curbs API, Tolls API, Routing API and etc.
image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
x-kinRank: "7"
x-alexaRank: "1035226"
tags: Coord
created: "2018-08-29"
modified: "2018-08-29"
url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/apis.md
specificationVersion: "0.14"
apis:
- name: Bike Share API - Get bike locations in the requested search area, as a GeoJSON
    FeatureCollection.
  x-api-slug: location-get
  description: |-
    Get a list of locations given the input parameters. Specify a search area by radius around
    a latitude and longitude, as well as any filter for specific systems. Each location will
    be a GeoJSON Feature, and aggregated into a GeoJSON FeatureCollection.

    ### Example

    #### Request:
    `curl -G "https://api.coord.co/v1/bike/location?latitude=40.742868&longitude=-73.989186&radius_km=0.25&access_key="`

    #### Response:
    ```
    {
      "features": [
        {
          "geometry": {
            "coordinates": [
              -73.98918628692627,
              40.74286877312112
            ],
            "type": "Point"
          },
          "id": "CitiBike-3641",
          "properties": {
            "is_renting": true,
            "is_returning": true,
            "last_reported": "2018-05-17T15:39:24.000Z",
            "lat": 40.74286877312112,
            "location_id": "3641",
            "location_type": "bike_station_dock",
            "lon": -73.98918628692627,
            "name": "Broadway & W 25 St",
            "num_bikes_available": 53,
            "num_docks_available": 1,
            "region_id": "71",
            "system_id": "CitiBike"
          },
          "type": "Feature"
        },
        {
          "geometry": {
            "coordinates": [
              -73.99144871,
              40.74395411
            ],
            "type": "Point"
          },
          "id": "CitiBike-466",
          "properties": {
            "is_renting": true,
            "is_returning": true,
            "last_reported": "2018-05-17T15:32:40.000Z",
            "lat": 40.74395411,
            "location_id": "466",
            "location_type": "bike_station_dock",
            "lon": -73.99144871,
            "name": "W 25 St & 6 Ave",
            "num_bikes_available": 35,
            "region_id": "71",
            "system_id": "CitiBike"
          },
          "type": "Feature"
        }
      ],
      "type": "FeatureCollection"
    }
    ```
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/bike
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/location-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/location-get-openapi.md
- name: Bike Share API - Get detailed information on a bike location, as a GeoJSON
    Feature.
  x-api-slug: locationsystem-idlocation-id-get
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
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/bike
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/locationsystem-idlocation-id-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/locationsystem-idlocation-id-get-openapi.md
- name: Bike Share API - Get the cost of renting a bike.
  x-api-slug: quote-get
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
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/bike
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/quote-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/quote-get-openapi.md
- name: Bike Share API - Get information on all bike systems in an area, as a GeoJSON
    FeatureCollection.
  x-api-slug: system-get
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
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/bike
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/system-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/system-get-openapi.md
- name: Bike Share API - Get detailed information on a bike system, as a GeoJSON feature.
  x-api-slug: systemsystem-id-get
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
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/bike
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/systemsystem-id-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/systemsystem-id-get-openapi.md
- name: Curb Search API - Find the rules for all curbs within a bounding box.
  x-api-slug: byboundsall-rules-get
  description: Find the rules for all curbs within a bounding box..
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/search/curbs
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/byboundsall-rules-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/byboundsall-rules-get-openapi.md
- name: Curb Search API - Find the rules for all curbs within a bounding box at a
    particular time.
  x-api-slug: byboundstime-rules-get
  description: Find the rules for all curbs within a bounding box at a particular
    time..
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/search/curbs
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/byboundstime-rules-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/byboundstime-rules-get-openapi.md
- name: Curb Search API - Find the rules on single curb.
  x-api-slug: bycurbidall-rules-get
  description: Find the rules on single curb..
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/search/curbs
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/bycurbidall-rules-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/bycurbidall-rules-get-openapi.md
- name: Curb Search API - Find the rules on a single curb at a certain time.
  x-api-slug: bycurbidtime-rules-get
  description: Find the rules on a single curb at a certain time..
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/search/curbs
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/bycurbidtime-rules-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/bycurbidtime-rules-get-openapi.md
- name: Curb Search API - Find the rules for curbs near a location.
  x-api-slug: bylocationall-rules-get
  description: |-
    Find all of the curbs within a given radius of a particular point, and return all of their
    rules across all times of day, days of the week, times of year, etc.
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/search/curbs
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/bylocationall-rules-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/bylocationall-rules-get-openapi.md
- name: Curb Search API - Find the rules for curbs near a location at a certain time.
  x-api-slug: bylocationtime-rules-get
  description: |-
    Find the rules for a given curb at a given time and on a given day. You can also use this
    to find all of the places that it is possible to perform a given action (for instance, find
    all the loading zones, or everywhere with two-hour parking).
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/search/curbs
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/bylocationtime-rules-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/bylocationtime-rules-get-openapi.md
- name: Multimodal Routing API - Find a route.
  x-api-slug: route-get
  description: Find possible trips between two points using either or both of bike-share
    and transit.
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/routing
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/route-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/route-get-openapi.md
- name: Parking Access API - Retrieve a location's sessions
  x-api-slug: location-idsession-get
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
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/access/parking
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/location-idsession-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/location-idsession-get-openapi.md
- name: Parking Access API - Create a new session
  x-api-slug: location-idsession-post
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
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/access/parking
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/location-idsession-post-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/location-idsession-post-openapi.md
- name: Parking Access API - Retrieve an existing session
  x-api-slug: location-idsessionsession-id-get
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
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/access/parking
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/location-idsessionsession-id-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/location-idsessionsession-id-get-openapi.md
- name: Parking Access API - End a previously started session
  x-api-slug: location-idsessionsession-idend-put
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
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/access/parking
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/location-idsessionsession-idend-put-openapi.md
- name: Parking Access API - Create a barcode
  x-api-slug: barcode-post
  description: Create a barcode for a user to be scanned upon entering/exiting a parking
    lot.
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/access/parking
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/barcode-post-openapi.md
- name: Parking Access API - Retrieve a user's sessions
  x-api-slug: session-get
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
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/access/parking
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/session-get-openapi.md
- name: Parking Access API - For test users only - Simulate a user redemption
  x-api-slug: testinglocation-idsession-idsimulate-redemption-post
  description: |-
    Some sessions don't automatically start when created. Instead, they are returned with
    `redemption_info`, which might be a barcode, for example, that needs to be scanned at the
    target location. For such sessions started by test users, you can use this method to
    simulate a redemption (arrival+departure). The system will behave as though a user checked
    in at a location where the session was creationg at the time you make the call and checked
    out at a time `duration_m` minutes in the future. **This method is only available for
    sessions started by test users.**
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/access/parking
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/testinglocation-idsession-idsimulate-redemption-post-openapi.md
- name: Parking Search API - Get a list of off-street parking locations.
  x-api-slug: location-get
  description: |-
    Find all of the locations within a given are and return their pricing information and
    (when present) availability. If the `duration_m` parameter is set, total cost for a stay
    of that duration will also be returned.
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/search/parking
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/location-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/location-get-openapi.md
- name: Parking Search API - Get a list of off-street parking locations.
  x-api-slug: locationid-get
  description: |-
    Find a single locations within a given are and return their pricing information and
    (when present) availability. If the `duration_m` parameter is set, total cost for a stay
    of that duration will also be returned.
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/search/parking
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/locationid-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/locationid-get-openapi.md
- name: Tolls API - Get toll rates corresponding to a sequence of timestamped GPS
    locations
  x-api-slug: gps-trace-post
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
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/search/tolling
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/gps-trace-post-openapi.md
- name: Tolls API - Get all toll rates corresponding to a single route
  x-api-slug: route-post
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
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/search/tolling
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/route-post-openapi.md
- name: Tolls API - Get all tolls in an area defined by a center location and a radius
  x-api-slug: toll-get
  description: Returns information on all tolls within a given radius.
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/search/tolling
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/toll-get-openapi.md
- name: Tolls API - Get the details (e.g. pricing) of a toll specified by toll's ID
  x-api-slug: tollid-get
  description: |-
    Returns full pricing and location details for a single toll location
    across all times, vehicle types, and payment methods.
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/search/tolling
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/tollid-get-openapi.md
- name: Users API - Create JWT
  x-api-slug: create-jwt-post
  description: |-
    Create a JWT for accessing user-authenticated APIs.

    If you currently are using an identity provider like Auth0 or Firebase or are generating
    your own JWTs to manage your end users' idenitites, you shouldn't need to use this API
    method. Please contact sales@coord.co so that we can set you up to use your existing JWTs!

    Otherwise, as long as you have your own backend, you may instead call this API method to
    generate valid JWTs. Note that you must include both your access_key on the URL parameter
    AND include a special `Authorization: Bearer <Server Token>` header. Contact sales@coord.co
    to receive your secret server token.

    The request body must contain an `email` field and optionally an `external_uid` field:

    ```
    {
      "external_uid": "1234",
      "email": "foo@bar.com"
    }
    ```

    The response will contain an object with a `jwt_token` field set to a JWT that expires
    in one hour. You may include this token in Authorization header required by all transaction
    APIs:

    ```
    {
      "jwt_token": "abc.123.zyx"
    }
    ```
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/users
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/create-jwt-post-openapi.md
- name: Users API - Get JWT
  x-api-slug: testingcreate-jwt-post
  description: |-
    Create a **test** JWT for accessing user-authenticated APIs. Note that API calls made using
    such a JWT will be serviced by sandbox backends, so it's safe to start/stop sessions, hail
    rides, and rent vehicles for testing purposes.

    ** Do not send any real user info. This endpoint is here for testing only. **

    The request body must contain an `email` field and optionally an `external_uid` field:

    ```
    {
      "external_uid": "1234",
      "email": "foo@bar.com"
    }
    ```

    The response will contain an object with a `jwt_token` field set to a JWT that expires
    in one hour. You may include this token in Authorization header required by all transaction
    APIs:

    ```
    {
      "jwt_token": "abc.123.zyx"
    }
    ```
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/users
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/testingcreate-jwt-post-openapi.md
- name: Users API - Simulate account linking for testing
  x-api-slug: testingusercurrenttransactable-systems-post
  description: |-
    Link a test user account to a system. This endpoint simulates the account linking flow
    outlined in `/user/current/link_account`. To link the test user's account with CitiBike,
    send:

    ```
    {
      "system_id": "CitiBike",
      "linked_account": true
    }
    ```

    On success, the response will be the same transactable system:
    ```
    {
      "system_id": "CitiBike",
      "linked_account": true
    }
    ```

    You can also unlink a system by setting `linked_account` to `false` instead. The full list
    of the user's current transactable systems can be found in the `transactable_systems` field
    when you call `GET /v1/users/user/current`.

    Not all systems require account linking to be transactable, and some systems require you to
    send additional information in order to connect to them. We will return a `400` if the user
    would not be able to link their account due to one of these reasons.

    ** Note that this method will not work for non-test users. **
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/users
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/testingusercurrenttransactable-systems-post-openapi.md
- name: Users API - Retrieve the current user
  x-api-slug: usercurrent-get
  description: |-
    Retrieves information about the currently logged in user, including any associated profile
    information, vehicle information, and provisioned systems.

    The response will be the full User object:

    ```
      {
        "email": "user@domain.com",
        "vehicle": {
          "license_plate": {
            "text": "123abc",
            "country": "us",
            "subdivision": "ny"
          }
        }
        "transactable_systems": [
          {
            "system_id": "CitiBike",
            "linked_account": true
          }
        ]
      }
    ```
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/users
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/usercurrent-get-openapi.md
- name: Users API - Update the user's stripe payment info
  x-api-slug: usercurrentstripe-info-post
  description: |-
    Update the Stripe information associated with this user. You must call this endpoint in
    order for the current user to transact with a system that requires Stripe information. If
    this is the case, the system's transaction_info will contain
    `stripe_info.stripe_customer_id` in the `users_api_fields` array.

    Note that it's not possible to call this endpoint for test users (using a test JWT) and as
    such we do not support test transactions for any system with the
    stripe_info.stripe_customer_id requirement. If you are interested in transacting, please
    contact sales@coord.co.

    The request body must contain a Stripe token for this user that's targeted to Coord. You
    can do this either by tokenizing a new credit card on Stripe, or by generating a token from
    an existing Stripe customer in your system. In order to target the token to Coord, you must
    have already registered your Stripe account as a "platform" via Stripe Connect, and we must
    have accepted an invitation to connect to your platform. Assuming that has happened,
    you'll be able to generate coord-targeted tokens via an API call like the folllwing:

    Assuming your already have a customer with id `cus_abc` on your side:

    ```
    curl https://api.stripe.com/v1/tokens \
      -u sk_your_stripe_secret_key: \
      -d customer=cus_abc \
      -H "Stripe-Account: acct_coord_connected_account_id"
    ```

    Note the Stripe-Account header, which tells Stripe to create a token targeted to a specific
    connected account. You must always include that header and set its value to the ID of
    Coord's connected account, which you can find here: https://dashboard.stripe.com/applications/users.

    See https://stripe.com/docs/api#tokens for more info on Stripe tokens.

    ```
      {
        "coord_targeted_token": "tok_123"
      }
    ```

    On success, the response will be the identical object with a customer_id field set. This ID
    is the ID of the customer that Coord creates on Stripe.
    ```
      {
        "coord_targeted_token": "tok_123"
        "customer_id": "cus_xyz"
      }
    ```
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/users
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/usercurrentstripe-info-post-openapi.md
- name: Users API - Update the current user's vehicle
  x-api-slug: usercurrentvehicle-put
  description: |-
    Update the vehicle information associated with the currently logged in user.

    The request should contain a vehicle object:
    ```
      {
        "license_plate": {
          "text": "123abc",
          "country": "us",
          "subdivision": "ny"
        }
      }
    ```

    On success, the response will be the identical object:
    ```
      {
        "license_plate": {
          "text": "123abc",
          "country": "us",
          "subdivision": "ny"
        }
      }
    ```
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/coord-logo.png
  humanURL: https://coord.co
  baseURL: https://api.coord.co//v1/users
  tags: Parking, Tolls, Bikes, Routes, General Data, Relative Data, Service API
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/coord/master/_listings/coord/usercurrentvehicle-put-openapi.md
x-common:
- type: x-blog
  url: https://medium.com/coord
- type: x-blog-rss
  url: https://medium.com/feed/coord
- type: x-openapi
  url: https://jsapi.apiary.io/apis/coordprodsearchtolls.source
- type: x-api-gallery
  url: http://convertapi.api.gallery.streamdata.io
- type: x-api-stack
  url: http://coord.stack.network
- type: x-developer
  url: https://coord.co/docs/
- type: x-pricing
  url: https://coord.co/#pricing
- type: x-twitter
  url: https://twitter.com/coordcity
- type: x-website
  url: https://coord.co
include: []
maintainers:
- FN: Kin Lane
  x-twitter: apievangelist
  email: info@apievangelist.com
---