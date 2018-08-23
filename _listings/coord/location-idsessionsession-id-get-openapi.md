---
swagger: "2.0"
x-collection-name: Coord
x-complete: 0
info:
  title: Coord Parking Access API Retrieve an existing session
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
  version: 1.0.0
host: api.coord.co
basePath: /v1/access/parking
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
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