---
swagger: "2.0"
x-collection-name: Coord
x-complete: 0
info:
  title: Coord Multimodal Routing API Find a route.
  description: Find possible trips between two points using either or both of bike-share
    and transit.
  version: 1.0.0
host: api.coord.co
basePath: /v1/routing
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
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