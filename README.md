
# Pantheon - Headless Lightning

This is a "fork'ish" version of [Acquia's Headless Lightning](https://github.com/acquia/headless-lightning) designed to be installed on Pantheon with their build tools process.

### Rational for "forking"

Headless Lightning gives us a basic headless setup with some opiniated defaults out fo the box which is great.

Pantheon composer based build tools gives us a composer based development process with CI and Github hosting which is also great and makes it super easy to setup.

This project just wraps the two together.  We have also added some basic docksal setup since we know we're hosted on Pantheon.

We have also tweaked the CircleCI tests to also work on Docksal so you can run the same tests locally as will be run on CircleCI.

> Just a heads up there may be some bits from the Acquia version of this repo hanging around if you're wondering why something is where it is and it doesn't make sense.

## Installing on Pantheon

This assumes you have already installed the [Build Tools](https://pantheon.io/docs/guides/build-tools/) dependencies and have your [CircleCI and Github tokens](https://pantheon.io/docs/guides/build-tools/#access-tokens-optional) ready to go.

To spin up your new Pantheon site, Github repo, CircleCI integration run.

`terminus build:project:create kanopi/pantheon-headless-lightning MY-NEW-PROJECT-NAME`

## Docksal setup with Pantheon

Since this is a starter project you will need to edit some things and commit them to them to the Github repo that is created for your project.

In `.docksal/docksal.env` you need to update:
* `TERMINUS_SITE` and `TERMINUS_ENVIRONMENT` variables to be the Pantheon project specific ones.
* `VIRTUAL_HOST` to be project specific.
   
The `TERMINUS_ENVIRONMENT` will be the default DB download location and can probably be left at 'dev' initially.  This should be updated to whatever environment is considered canonical though.

## Local development

As a developer working on this project you'll need to **copy** `.docksal/docksal-local.env.example` to `.docksal/docksal-local.env`.

Within that file you'll need to put your Terminus machine token for this project in. Machine tokens can be created in your [Pantheon account page](https://dashboard.pantheon.io/users/#account/tokens/).  Once you have the machine token in you will be able to run terminus commands against Pantheon within Docksal, which is what is used to download the DB.
