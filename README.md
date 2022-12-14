# itbootcamp_final_api_testing
https://documenter.getpostman.com/view/23503188/2s8479zbv2

On the example of the application https://vue-demo.daniel-avellaneda.com/ demonstrate the API testing, using Postman and  Chai Assertion Library.
## Features
*   Vuetify
*   Multiple environment ready (development, production).
*   Vue router
*   Vuex
*   i18n ready.
*   Google Analytics ready.
*   Ready to add to home screen in iOS and Chrome, checks if there´s an app update every 2 hours and reloads page (When a web app is added as stand alone there´s no reload button in the browser so new .js files from a new build never get loaded)
*   Landing page.
*   Protected home page.
*   Login.
*   Signup.
*   Forgot password.
*   Account verification.
*   User profile.
*   Users admin area with CRUD operations.
*   Cities admin area with CRUD operations.
*   Testing with Cypress and mocha/chai.
*   NPM script for keeping good source code formatting using prettier and ESLint.
*   Use of ESLint for good coding practices.
*   Use of prettier for beautiful format.
*   Ability to refresh token
*   JWT Tokens, make requests with a token after login with `Authorization` header with value `Bearer yourToken` where `yourToken` is the **signed and encrypted token** given in the response from the login process.
*   Chai Assertion Library  

## YAML DOCUMENTATION
  swagger: '2.0'
info:
  version: '1.0'
  title: IT Bootcamp API - Ojacavanje
  contact: {}
host: istrazitesami.com
basePath: /
securityDefinitions: {}
schemes:
- http
consumes:
- application/json
produces:
- application/json
paths:
  /register:
    post:
      tags:
      - auth
      operationId: /register
      deprecated: false
      produces:
      - application/json
      consumes:
      - application/x-www-form-urlencoded
      parameters:
      - name: name
        in: formData
        required: true
        type: string
        description: ''
      - name: email
        in: formData
        required: true
        type: string
        description: ''
      - name: password
        in: formData
        required: true
        type: string
        description: ''
      responses:
        200:
          description: ''
          headers: {}
      security: []
  /verify:
    post:
      tags:
      - auth
      operationId: /verify
      deprecated: false
      produces:
      - application/json
      consumes:
      - application/x-www-form-urlencoded
      parameters:
      - name: id
        in: formData
        required: true
        type: string
        description: ''
      responses:
        200:
          description: ''
          headers: {}
      security: []
  /forgot:
    post:
      tags:
      - auth
      operationId: /forgot
      deprecated: false
      produces:
      - application/json
      consumes:
      - application/x-www-form-urlencoded
      parameters:
      - name: email
        in: formData
        required: true
        type: string
        description: ''
      responses:
        200:
          description: ''
          headers: {}
      security: []
  /reset:
    post:
      tags:
      - auth
      operationId: /reset
      deprecated: false
      produces:
      - application/json
      consumes:
      - application/x-www-form-urlencoded
      parameters:
      - name: id
        in: formData
        required: true
        type: string
        description: ''
      - name: password
        in: formData
        required: true
        type: string
        description: ''
      responses:
        200:
          description: ''
          headers: {}
      security: []
  /login:
    post:
      tags:
      - auth
      operationId: /login
      deprecated: false
      produces:
      - application/json
      consumes:
      - application/x-www-form-urlencoded
      parameters:
      - name: email
        in: formData
        required: true
        type: string
        description: ''
      - name: password
        in: formData
        required: true
        type: string
        description: ''
      responses:
        200:
          description: ''
          headers: {}
      security: []
  /token:
    get:
      tags:
      - auth
      operationId: /token
      deprecated: false
      produces:
      - application/json
      parameters:
      - name: Authorization
        in: header
        required: true
        default: Bearer {token}
        type: string
      responses:
        200:
          description: ''
          headers: {}
  /users:
    get:
      tags:
      - users
      operationId: /users
      deprecated: false
      produces:
      - application/json
      parameters:
      - name: Authorization
        in: header
        required: true
        default: Bearer {token}
        type: string
      - name: filter
        in: query
        required: false
        type: string
        description: ''
      - name: fields
        in: query
        required: false
        type: string
        description: '[name, email, role, city, country, phone]'
      - name: page
        in: query
        required: false
        type: integer
        format: int32
        description: ''
      - name: limit
        in: query
        required: false
        type: integer
        format: int32
        description: ''
      - name: sort
        in: query
        required: false
        type: string
        description: '[name, email, role, city, country, phone]'
      - name: order
        in: query
        required: false
        type: integer
        format: int64
        description: '[1 or -1]'
      responses:
        200:
          description: ''
          headers: {}
    post:
      tags:
      - users
      operationId: Post/users
      deprecated: false
      produces:
      - application/json
      consumes:
      - application/x-www-form-urlencoded
      parameters:
      - name: Authorization
        in: header
        required: true
        default: Bearer {token}
        type: string
    
      - name: name
        in: formData
        required: true
        type: string
        description: ''
      - name: email
        in: formData
        required: true
        type: string
        description: ''
      - name: password
        in: formData
        required: true
        type: string
        description: ''
      - name: role
        in: formData
        required: true
        type: string
        description: ''
      - name: phone
        in: formData
        required: true
        type: integer
        format: int32
        description: ''
      - name: city
        in: formData
        required: true
        type: string
        description: ''
      - name: country
        in: formData
        required: true
        type: string
        description: ''
      responses:
        200:
          description: ''
          headers: {}
  '/users/{id}':
    delete:
      tags:
      - users
      operationId: /users/:id
      deprecated: false
      produces:
      - application/json
      parameters:
      - name: id
        type: string
        required: true
        in: path
      - name: Authorization
        in: header
        required: true
        default: Bearer {token}
        type: string
      responses:
        200:
          description: ''
          headers: {}
    get:
      tags:
      - users
      operationId: Get/users/:id
      deprecated: false
      produces:
      - application/json
      parameters:
      - name: id
        type: string
        required: true
        in: path
      - name: Authorization
        in: header
        required: true
        default: Bearer {token}
        type: string
      responses:
        200:
          description: ''
          headers: {}
    patch:
      tags:
      - users
      operationId: Patch/users/:id
      deprecated: false
      produces:
      - application/json
      consumes:
      - application/x-www-form-urlencoded
      parameters:
      - name: id
        type: string
        required: true
        in: path
      - name: Authorization
        in: header
        required: true
        default: Bearer {token}
        type: string
      
      - name: name
        in: formData
        required: true
        type: string
        description: ''
      - name: email
        in: formData
        required: true
        type: string
        description: ''
      - name: role
        in: formData
        required: true
        type: string
        description: ''
      - name: phone
        in: formData
        required: true
        type: string
        description: ''
      - name: city
        in: formData
        required: true
        type: string
        description: ''
      - name: country
        in: formData
        required: true
        type: string
        description: ''
      responses:
        200:
          description: ''
          headers: {}
  /profile:
    get:
      tags:
      - profile
      operationId: /profile
      deprecated: false
      produces:
      - application/json
      parameters:
      - name: Authorization
        in: header
        required: true
        default: Bearer {token}
        type: string
      responses:
        200:
          description: ''
          headers: {}
    patch:
      tags:
      - profile
      operationId: Patch/profile
      deprecated: false
      produces:
      - application/json
      consumes:
      - application/x-www-form-urlencoded
      parameters:
      - name: Authorization
        in: header
        required: true
        default: Bearer {token}
        type: string
      - name: name
        in: formData
        required: true
        type: string
        description: ''
      - name: urlTwitter
        in: formData
        required: true
        type: string
        description: ''
      - name: urlGitHub
        in: formData
        required: true
        type: string
        description: ''
      - name: phone
        in: formData
        required: true
        type: string
        description: ''
      - name: city
        in: formData
        required: true
        type: string
        description: ''
      - name: country
        in: formData
        required: true
        type: string
        description: ''
      responses:
        200:
          description: ''
          headers: {}
  /profile/changePassword:
    post:
      tags:
      - profile
      operationId: /profile/changePassword
      deprecated: false
      produces:
      - application/json
      consumes:
      - application/x-www-form-urlencoded
      parameters:
      - name: Authorization
        in: header
        required: true
        default: Bearer {token}
        type: string
      - name: oldPassword
        in: formData
        required: true
        type: integer
        format: int32
        description: ''
      - name: newPassword
        in: formData
        required: true
        type: integer
        format: int32
        description: ''
      responses:
        200:
          description: ''
          headers: {}
  /cities/all:
    get:
      tags:
      - cities
      operationId: /cities/all
      deprecated: false
      produces:
      - application/json
      parameters:
      - name: Authorization
        in: header
        required: true
        default: Bearer {token}
        type: string
      responses:
        200:
          description: ''
          headers: {}
  /cities:
    get:
      tags:
      - cities
      operationId: /cities
      deprecated: false
      produces:
      - application/json
      parameters:
      - name: Authorization
        in: header
        required: true
        default: Bearer {token}
        type: string
      - name: filter
        in: query
        required: false
        type: string
        description: ''
      - name: fields
        in: query
        required: false
        type: string
        description: ''
      - name: page
        in: query
        required: false
        type: integer
        format: int32
        description: ''
      - name: limit
        in: query
        required: false
        type: integer
        format: int32
        description: ''
      - name: sort
        in: query
        required: false
        type: string
        description: ''
      - name: order
        in: query
        required: false
        type: integer
        format: int32
        description: ''
      responses:
        200:
          description: ''
          headers: {}
    post:
      tags:
      - cities
      operationId: Post/cities
      deprecated: false
      produces:
      - application/json
      consumes:
      - application/x-www-form-urlencoded
      parameters:
      - name: Authorization
        in: header
        required: true
        default: Bearer {token}
        type: string
      - name: name
        in: formData
        required: true
        type: string
        description: ''
      responses:
        200:
          description: ''
          headers: {}
  '/cities/{id}':
    get:
      tags:
      - cities
      operationId: /cities/:id
      deprecated: false
      produces:
      - application/json
      parameters:
      - name: id
        in: path
        required: true
        type: string
      - name: Authorization
        in: header
        required: false
        default: Bearer {token}
        type: string
    
      responses:
        200:
          description: ''
          headers: {}
    patch:
      tags:
      - cities
      operationId: Patch/cities/:id
      deprecated: false
      produces:
      - application/json
      consumes:
      - application/x-www-form-urlencoded
      parameters:
      - name: id
        in: path
        required: true
        type: string
      - name: Authorization
        in: header
        required: true
        default: Bearer {token}
        type: string
    
      - name: name
        in: formData
        required: true
        type: string
        description: ''
      responses:
        200:
          description: ''
          headers: {}
    delete:
      tags:
      - cities
      operationId: Delete/cities/:id
      deprecated: false
      produces:
      - application/json
      parameters:
      - name: id
        in: path
        required: true
        type: string
      - name: Authorization
        in: header
        required: true
        default: Bearer {token}
        type: string
      responses:
        200:
          description: ''
          headers: {}
tags:
- name: auth
- name: users
- name: profile
- name: cities

