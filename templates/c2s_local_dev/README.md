# C2S docker-compose file for local development

The `docker-compose.yml` will setup a local development environment where the code is sourced from the local machine and is set to reload on file changes.

## Pre-requisites:

* Clone all dependent service repos into `~/code`
  * `cd ~/code && git clone https://github.com/nhsuk/connecting-to-services.git`
  * `cd ~/code && git clone https://github.com/nhsuk/nearby-services-api.git`


## Steps for local development:

1. Clone this repo locally `cd ~/code && git clone https://github.com/nhsuk/nhsuk-rancher-templates.git`
1. Change working directory `cd nhsuk-rancher-templates/templates/c2s_local_dev/`
1. Run `docker-compose up --build --force-recreate`. This will bring up your "stack" with port 3000 exposed locally. The `--build` and `--force-recreate` will ensure you always start the stack from scratch. NOTE: Any environment variables that do not have default values will need to be added to the `.env` file or set on the command line. e.g. `${SPLUNK_HEC_TOKEN}`. If environment variable have setting that are not as required they can be changed in the `.env` file to the appropriate value.
1. To stop the "stack" run `docker-compose stop`


## Use existing images

If there is no need to create the Docker image locally and an existing image is needed. The line specifying the `image` can be uncommented.
