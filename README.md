## Build Status

Travis Ci:

[![Build Status](https://travis-ci.org/appirio-tech/lc1-discussion-service.svg?branch=master)](https://travis-ci.org/appirio-tech/lc1-discussion-service)

Wercker:

[![wercker status](https://app.wercker.com/status/4cb9c0baf2652f5f848a6c410e19f0c1/m "wercker status")](https://app.wercker.com/project/bykey/390f3f96c8d649ec41a49f9c486c512f)

## serenity-discussion-api is a Discussion API Service

The topcoder Discussion API was initially built using the [Apigee a127 scaffolding](https://github.com/apigee-127/a127-documentation/wiki).

Routing is handled by using the swagger config file at api\swagger\swagger.yaml.
Routing is done using [swagger tools](https://github.com/apigee-127/swagger-tools) and the [a127-magic](https://github.com/apigee-127/magic) modules.

## Swagger

The documentaiton for the API and resources are in swagger.  You can view the swagger config using a127 tools or the built in Swagger UI.

To Edit/view swagger config run ```a127 project edit``` from project root
You can also view the swagger config via the /docs url when the project is running.

Current API Documentation can be found here:  http://lc1-discussion-service.herokuapp.com/docs/


## Configuration

Configuration is stored in the /config/*.yaml files.  The [node config](https://github.com/lorenwest/node-config) module is used to load configuration.

Please see the config documentation:  https://github.com/lorenwest/node-config/wiki

The "local" config files are all ignored in git.

Configuration:

```yaml
    app:
        port: 1234 #port to launch
        pg:
            dialect: postgres
            database: serenity_discussions
            username: username
            password: password
            host: host
            port: 5432
        pgURL:
```

For the database connection you can either use the pg object or the pgURL.  The pgURL is looked for first and will override the pg.

## Models

We are following a similar patterns to access patterns as we do in the serenity-core repo.

Use a model:

Example for Message model

```javascript
var datasource = require('./datasource');
var Message = datasource.Message;

// Message is now a Sequelize Model
```

## Node.js design guide.

Please follow Joyent's NodeJS design guide:  https://www.joyent.com/developers/node/design
Please use 2 spaces instead of tabs.
Please use lodash instead of underscore.

## Database Migrations

All tables should be setup using [db-migrate](https://github.com/kunklejr/node-db-migrate) with migration files in config/schema-migrations.

Migration can be run via grunt ```grunt dbmigrate```

## Running the server

You can run the server using ```grunt``` which will use the local config.

## Tests

Tests are built using mocha tests.   They can be run with ```grunt test```.  There is an example postman configuration file at test/postman.json.  This can be imported into Postman for testing.

