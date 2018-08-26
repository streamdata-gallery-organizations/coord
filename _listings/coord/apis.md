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
created: "2018-08-26"
modified: "2018-08-26"
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