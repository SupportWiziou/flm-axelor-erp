# Wiziou-axelor-erp

## Deploying the app

Simply merge the wanted version of the app on master:

Go in the `open-suite-webapp folder` and pull the relevant commit (check Axelor's repo: https://github.com/axelor/axelor-open-suite)
Pull the matching versions of the submodules: `git submodule update --init --recursive`

During deployment, the `cloudbuild.yaml` file calls the `gradlefilereplacer.sh` script to replace:
- the `./open-suite-webapp/build.gradle` file by the `./build.gradle.replacement` file
- the `./open-suite-webapp/settings.gradle` file by the `./settings.gradle.replacement` file

This can later be used to run professional modules, but it is also used for the database:

#### In the `build.gradle` file,

in the dependencies of that file:

```
  implementation 'com.google.cloud.sql:postgres-socket-factory:1.11.1'
```
The socket factory is necessary for the server to work on GCP.

#### In the `settings.gradle` file, nothing needs to be changed, until professional modules are used


**Make sure the rest of the content of this replacement file is the same as the original file**
