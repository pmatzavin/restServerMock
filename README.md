# RestServerMock

  A Simple REST HTTP server that serves the configured JSON responses.

## About

  The motivation for implementing this module was to provide a quick and simple server to be used
  when developing a rest client.
  In that cases where the rest server has not been implemented yet,
  I wanted to have an HTTP server responding with some mock JSON responses,
  without relying on a more complex mocking framework.

## Configuration

  The server's port and the server routes are configured in a JSON file:

  Example file:
  ```
  {

    "port": 3001

    , "routes": [

      {
        "path": "/a"
        , "type": "GET"
        , "response": {
          "field_1": "f1 get a ok"
          , "field_2": "f2 get a ok"
        }
      }

      , {
        "path": "/a"
        , "type": "POST"
        , "response": {
          "field_1": "f1 post a ok"
          , "field_2": "f2 post a ok"
        }
      }

      , {
        "path": "/a"
        , "type": "PUT"
        , "response": {
          "field_1": "f1 put a ok"
          , "field_2": "f2 put a ok"
        }
      }

      , {
        "path": "/a"
        , "type": "DELETE"
        , "response": {
          "field_1": "f1 delete a ok"
          , "field_2": "f2 delete a ok"
        }
      }

    ]

  }
  ```
## Usage

### As a commandline tool

```
node rest-server-mock path_to_configuration_file
```

### As a module

```
var restServerMock = require('rest-server-mock') // Include the module.
restServerMock(path_to_configuration_file)       // Start the server. Returns a promise.
.then(function (server) {
    console.log('RestServerMock is listening on port: ', server.address().port, ' ...')
    console.log('Configuration file: ', process.argv[2])
}
, function (err) {
    console.log(err)
})
// Note that the restServerMock method returns a promise.
```

