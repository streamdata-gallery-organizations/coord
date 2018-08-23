---
swagger: "2.0"
x-collection-name: Coord
x-complete: 0
info:
  title: Coord Users API Update the user's stripe payment info
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
  /testing/create_jwt:
    post:
      summary: Get JWT
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
      operationId: jwt_test_token
      x-api-path-slug: testingcreate-jwt-post
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: body
        name: request
        description: An object with the `email` field set to the verified email of
          your end user
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - JWT
  /testing/user/current/transactable_systems:
    post:
      summary: Simulate account linking for testing
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
      operationId: test_link_user_account
      x-api-path-slug: testingusercurrenttransactable-systems-post
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: body
        name: system
        description: The system the user should be provisioned for
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Simulate
      - Account
      - Linkingtesting
  /user/current:
    get:
      summary: Retrieve the current user
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
      operationId: get_user
      x-api-path-slug: usercurrent-get
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      responses:
        200:
          description: OK
      tags:
      - Retrieve
      - Current
      - User
  /user/current/stripe_info:
    post:
      summary: Update the user's stripe payment info
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
      operationId: post_stripe_info
      x-api-path-slug: usercurrentstripe-info-post
      parameters:
      - in: query
        name: access_key
        description: The API access key for the request
      - in: body
        name: stripe_info
        description: A `StripeInfo` object
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Users
      - Stripe
      - Payment
      - Info
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