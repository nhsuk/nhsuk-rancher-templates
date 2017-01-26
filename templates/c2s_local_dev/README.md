# C2S docker-compose file for local development

1. Clone this repo locally `git https://github.com/nhsuk/nhsuk-rancher-templates.git`
2. Change working directory `cd nhsuk-rancher-templates/templates/c2s_local_dev/`
3. Create a `.env` file with the required ENV variables (currently only SPLUNK_HEC_TOKEN). Useful ones to define are:
    1. FE_TAG= defines which version of the 'connecting-to-services' app to deploy
    2. API_TAG= defines which version of the 'nearby-services-api' app to deploy
4. Run `docker-compose up --build --force-recreate`. This will bring up your "stack" with port 3000 exposed locally. The `--build` and `--force-recreate` will ensure you always start the stack from scratch.
5. To stop the "stack" run `docker-compose stop`
