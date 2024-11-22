# A local zitadel deployment intended for testing purposes. 

This repository includes configurations and scripts to locally deploy
[Zitadel](https://github.com/zitadel/zitadel)
along with a few other helpful services:
* A minimal OpenID Connect Identity Provider
  ([link](https://github.com/lukawaay/oidc_test_srv)). 
  A configuration file lets you prepare a list of users and regular
  authorization flows are implemented where one can choose a user the want to
  authenticate as.
* A minimal Zitadel application
  ([link](https://github.com/lukawaay/zitadel_test_app)).
  It allows one to login through Zitadel and display basic information about
  their account. It also exposes an OAuth bearer token that can be used to test
  API requests.
* A mail catching server: [MailHog](https://github.com/mailhog/MailHog).
  Mail sent from Zitadel can be viewed through a web UI.


# Usage

Start a new development environment:
```
ENV_PATH=./environments/foo
./create $ENV_PATH
```

Enter the environment and use Docker Compose to start it:
```
cd ENV_PATH
[docker](docker) compose up -d
```

## Exposed Services

### Zitadel

Available URLs:
- [http://localhost:8080/](http://localhost:8080/)
- [http://zitadelinstance.localhost:8080/](http://zitadelinstance.localhost:8080/)

Admin User:
- Username: `zitadel-admin@zitadel.localhost`
- Password: `Password1!`

The environment creation script will instantiate a database that will provide a
configuration for the other services. Everything is already hooked up and ready
to use.

### MalHog

App URL: [http://localhost:8025](http://localhost:8025)

### Identity Provider

Issuer URL: [http://localhost:7123](http://localhost:7123)

### Zitadel App

App URL: [http://localhost:9123](http://localhost:9123)

## Exposed Configurations

### Zitadel

Files:
- Configuration file: `$ENV_PATH/mounts/config/zitadel.yaml`
- Database setup file: `$ENV_PATH/mounts/config/zitadel_steps.yaml`
- Master key file: `$ENV_PATH/mounts/config/zitadel_masterkey`

### Identity Provider

Files:
- Configuration file (users and clients): `$ENV_PATH/mounts/idp.json`

# Roadmap

Planned Features:
- [ ] Support deployment of a local instance of the Zitadel codebase.
