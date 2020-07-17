# catchmail-docker

A docker-compose setup for catchmail. Contains: [catchmail-web](https://github.com/mat-sz/catchmail-web), [catchmail-ws](https://github.com/mat-sz/catchmail-ws) and [nginx](http://nginx.org/). This configuration should roughly match the production environment.

## Installation

Clone the repo and run the following commands:

```
git submodule update --recursive --init
HOST=localhost PORT=80 TITLE=catchmail docker-compose up
```

Make sure docker and docker-compose are installed and your user is in the docker group. In case another reverse proxy is used make sure to change the default port (from 80) and to add the `X-Forwarded-For` header with client's IP address.

The SMTP server ([microMTA](https://github.com/mat-sz/microMTA)) is exposed at port 25, this cannot be changed.

## Environment variables

| Variable      | Default value | Description                                                              |
| ------------- | ------------- | ------------------------------------------------------------------------ |
| `HOST`        | `localhost`   | Domain/external IP for the application.                                  |
| `PORT`        | `80`          | Reverse proxy port.                                                      |
| `TITLE`       | `catchmail`   | Application title.                                                       |
| `AUTH_MODE`   | `none`        | Authentication mode.                                                     |
| `AUTH_SECRET` | (empty)       | Authentication secret.                                                   |
| `LOG_MODE`    | `none`        | Logging mode. Set to `file` for the .eml files to be saved into `./log`. |
