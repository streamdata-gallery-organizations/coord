---
swagger: "2.0"
x-collection-name: Coord
x-complete: 0
info:
  title: Coord Users API Create JWT
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
  version: 1.0.0
host: api.coord.co
basePath: /v1/users
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /create_jwt:
    post:
      summary: Create JWT
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
      operationId: jwt_token
      x-api-path-slug: create-jwt-post
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: body
        name: request
        description: A object with the `email` field set to the verified email of
          your end user
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - JWT
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