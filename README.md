# BSI Secvisogram CSAF Validator Service

- [About the project](#about-the-project)
- [Getting started](#getting-started)
- [Documentation](#documentation)
- [Configuration](#configuration)
- [Developing](#developing)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Run server](#run-server)
- [Testing](#testing)
- [Contributing](#contributing)
- [Dependencies](#dependencies)

## About the project

This is a service to validate documents against the [CSAF standard](https://docs.oasis-open.org/csaf/csaf/v2.0/csaf-v2.0.html). It uses the [csaf-validator-lib](https://github.com/secvisogram/csaf-validator-lib) under the hood which is included as a `git subtree` module.

[(back to top)](#bsi-secvisogram-csaf-validator-service)

## Getting started

To run the validator service you basically need the same as for [developing](#developing).

- install Node.js 16
- install production dependencies and copy all relevant files to the dist
  folder by running `npm run dist`
- copy the content of the dist folder to your working directory
- Make sure to set the environment variable `NODE_ENV` to `production`
- Configure the service using a `local-production.json` file in
  `backend/config`. All available parameters are outlined in `backend/config/development.json`. See [https://www.npmjs.com/package/config](https://www.npmjs.com/package/config) for more information on how to configure using different techniques such as environment variables.
- test 6.3.8 requires an installation of hunspell.
  - For more details on how to manage languages, please also see [Managing Hunspell languages](https://github.com/secvisogram/csaf-validator-lib#managing-hunspell-languages)
- start the service with `node backend/server.js`

To manage the process you can use Docker or an init system of your choice.

You most likely also want to run this behind a reverse proxy to handle TLS
termination or CORS headers if the service is accessed from other domains. See
[https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)
for more information.

## Documentation

The documentation is available as a swagger resource provided by the service itself under `/docs`. So once the server is running, visit [http://localhost:&lt;config port&gt;/docs](http://localhost:3000/docs) in your browser. The default port of the application `3000`. See [configuration](#configuration) to learn about ways to change it.

[(back to top)](#bsi-secvisogram-csaf-validator-service)

## Configuration

The project uses the [config](https://www.npmjs.com/package/config) npm package for configuration. It provides a variety of possibilities to inject configuration values e.g. environment variables or environment specific files.

[(back to top)](#bsi-secvisogram-csaf-validator-service)

## Developing

### Prerequisites

You need at least **Node.js version 16 or higher**. [Nodesource](https://github.com/nodesource/distributions/blob/master/README.md) provides binary distributions for various Linux distributions.

[(back to top)](#bsi-secvisogram-csaf-validator-service)

### Installation

- Install server and csaf-validator-lib dependencies
  ```sh
  npm ci
  ```

[(back to top)](#bsi-secvisogram-csaf-validator-service)

### Run server

- Start the server

  ```sh
  npm run dev
  ```

[(back to top)](#bsi-secvisogram-csaf-validator-service)

## Testing

Many tests are integration tests which need a running server. So make sure to start it before running the tests:

```sh
npm run dev
```

Tests are implemented using [mocha](https://mochajs.org/). They can be run using the following command:

```sh
npm test
```

[(back to top)](#bsi-secvisogram-csaf-validator-service)

## Contributing

You can find our guidelines here [CONTRIBUTING.md](https://github.com/secvisogram/secvisogram/blob/main/CONTRIBUTING.md)

[(back to top)](#bsi-secvisogram-csaf-validator-service)

## Dependencies

For the complete list of dependencies please take a look at [package.json](https://github.com/secvisogram/csaf-validator-lib/blob/main/package.json)

- [fastify](https://fastify.io/)
- [fastify-swagger](https://github.com/fastify/fastify-swagger)
- [csaf-validator-lib](https://github.com/secvisogram/csaf-validator-lib)

[(back to top)](#bsi-secvisogram-csaf-validator-service)
