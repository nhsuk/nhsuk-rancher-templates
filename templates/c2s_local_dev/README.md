# C2S docker-compose file for local development

1. Clone this repo locally `git clone https://github.com/nhsuk/nhsuk-rancher-templates.git`
2. Change working directory `cd nhsuk-rancher-templates/templates/c2s_local_dev/`
3. Change username/path in the volumes `- /Users/#{username}/NHS.UK`
4. Run `docker-compose up --build --force-recreate`. This will bring up your "stack" with port 3000 exposed locally. The `--build` and `--force-recreate` will ensure you always start the stack from scratch. NOTE: Any environment variables that do not have default values will need to be added to the `.env` file or set on the command line. e.g. `${SPLUNK_HEC_TOKEN}`. If environment variable have setting that are not as required they can be changed in the `.env` file to the appropriate value.
5. To stop the "stack" run `Ctrl + C`
