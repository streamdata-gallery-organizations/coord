---
swagger: "2.0"
x-collection-name: Coord
x-complete: 0
info:
  title: Coord Bike Share API Get detailed information on a bike system, as a GeoJSON
    feature.
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
  version: 1.0.0
host: api.coord.co
basePath: /v1/bike
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /location:
    get:
      summary: Get bike locations in the requested search area, as a GeoJSON FeatureCollection.
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
      operationId: search_locations
      x-api-path-slug: location-get
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
      - in: query
        name: system_ids
        description: Comma separated list of the bike system IDs to include in the
          search
      responses:
        200:
          description: OK
      tags:
      - Bike
      - Locations
      - In
      - Requested
      - Search
      - Area
      - ""
      - As
      - GeoJSON
      - FeatureCollection
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