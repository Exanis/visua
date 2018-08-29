# VISUA

**For** non-programmers

**Who** want to process data easily

*VISUA*

**Offer** an easy way to manage data

**And unlike others** have a very easy-to-use, intuitive GUI with no code involved

*Ready to try ?*

## Components links

- [![Build Status](https://travis-ci.org/Exanis/visua-api.svg?branch=master)](https://travis-ci.org/Exanis/visua-api)
[![codecov](https://codecov.io/gh/Exanis/visua-api/branch/master/graph/badge.svg)](https://codecov.io/gh/Exanis/visua-api) **API**: https://github.com/Exanis/visua-api
- [![Build Status](https://travis-ci.org/Exanis/visua-frontend.svg?branch=master)](https://travis-ci.org/Exanis/visua-frontend) [![codecov](https://codecov.io/gh/Exanis/visua-frontend/branch/master/graph/badge.svg)](https://codecov.io/gh/Exanis/visua-frontend) **Frontend**: https://github.com/Exanis/visua-frontend
- [![Build Status](https://travis-ci.org/Exanis/visua-runner.svg?branch=master)](https://travis-ci.org/Exanis/visua-runner) [![codecov](https://codecov.io/gh/Exanis/visua-runner/branch/master/graph/badge.svg)](https://codecov.io/gh/Exanis/visua-runner) **Runner**: https://github.com/Exanis/visua-runner

To make testing and development easier, a skaffold project (aimed to be launched on local server using minikube) can also be found here: https://github.com/Exanis/visua-dev

All those parts are submodules of this repository.

## Settings

Settings of Visua are changed using env variables. Here are the available variables:

### API

| Setting | Default value | Usage |
|---------|---------------|-------|
| DEBUG | False | If set to True, the app will run in Debug mode (giving way more informations when crashing). Please **never** set this settings to True in a production environment.
| ALLOWED_HOSTS | ['*'] | A list of host allowed. If you want to limit the access to the api to a specific URL, you can change this. Note that this is probably not what you want; instead, you should use a reverse proxy in front of the API (since it's typically launched in a docker environment, you can't be sure of the address used) |
| DATABASE_URL | None (required) | Database URL. Visua API need a postgres database to properly work. A common example could be *pgsql://my_user:my_password@my_server:5432/my_database* |
| SECRET_KEY | change me | Application secret key (used to create user's auth token). Please set this to a secret random value.
| RUNNER_KEY | change me | Runner join secret key (used by runners to connect to your application). Please set this to a secret random value. |

### Runner

| Setting | Default value | Usage |
|---------|---------------|-------|
| API_SERVER | None (required) | Address of the API server (note that the runner must be able to talk to this server, and vice-versa) |
| API_TOKEN | None (required) | API auth token (must be the same as the RUNNER_KEY in the API) |
| RUNNER_ADDR | None (required) | Address where the API can talk to the runner |
| RUNNER_NAME | (value of RUNNER_ADDR) | Name used by the API to display the runner in the runner list |

**Note**: The runner will always run on port 8887 ; this port is the one exposed by the Dockerfile, and can then be redirected if needed when the container is launched.