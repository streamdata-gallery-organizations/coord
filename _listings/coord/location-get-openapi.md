---
swagger: "2.0"
x-collection-name: Coord
x-complete: 0
info:
  title: Coord Parking Search API Get a list of off-street parking locations.
  description: |-
    Find all of the locations within a given are and return their pricing information and
    (when present) availability. If the `duration_m` parameter is set, total cost for a stay
    of that duration will also be returned.
  version: 1.0.0
host: api.coord.co
basePath: /v1/search/parking
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