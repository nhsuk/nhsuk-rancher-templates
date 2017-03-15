# NHS.uk Rancher Templates

Docker templates used in PR/staging/production environments in [NHS.uk](http://www.nhs.uk).

See the [Rancher docs](https://docs.rancher.com/rancher/v1.5/en/catalog/private-catalog/) for in-depth details of how they work.

## Branches

There are 3 primary branches:

| Branch           | Associated Rancher Catalog | Use |
|:-----------------|:---------------------------------------------------|:-----|
|`production`      | [NHSuk_Production](https://rancher.nhschoices.net/env/1a9/catalog?catalogId=NHSuk_Production) | Production enviroments |
|`staging`         | [NHSuk_Staging](https://rancher.nhschoices.net/env/1a9/catalog?catalogId=NHSuk_Staging) | Staging and PR environments |
|`test_deployment` | [NHSuk (Test Deployment Branch)](https://rancher.nhschoices.net/env/1a9/catalog?catalogId=NHSuk%20(Test%20Deployment%20Branch)) | Manual testing of template work (via git force push)

## Workflow

### New application stack

Create a new template in the `templates` directory, either by:

1. Using https://www.npmjs.com/package/generator-rancher-catalog
2. Creating it manually, using one of the others as a template.

### Updating a stack

Unfortunately Rancher templating system doesn't make full use of git versioning :disappointed:

To upgrade a template/stack (i.e. adding new ENV variables) the following steps should be followed:

1. Create a new feature/branch for your change.
2. In the template directory you wish to upgrade, copy the latest versioned directory i.e. `1` and place the content in the next number sequence (`2`).
3. Make your changes in this new folder.
4. In `rancher-compose.yml` in this directory ensure you update the `catalog.version` value to something approriate for the change.
5. Update the variable `version` in `config.yml` to match the `catalog.version` value in your new `rancher-compose.yml`. This variable defines the default version to use.

## Tests
TODO...

## Deployments

The recommended way to test changes is the following (Steps 1-4 *could* be skipped):

1. Force push your feature branch to the `test_deployment` branch, using `git push -f origin feature/branch:test_deployment`.
2. Manually deploy a stack in rancher using the [NHSuk (Test Deployment)](https://rancher.nhschoices.net/env/1a9/catalog?catalogId=NHSuk%20(Test%20Deployment%20Branch)) catalog.
3. Test.
4. Push your feature branch up normally (if not already done).
5. Pull Request to get it into master.
6. All new PR builds will now use this latest template.
7. Upgrade Staging stacks and any PR builds (if you need to).
8. Pull Request for `master` -> `production`
9. Upgrade production stacks.
