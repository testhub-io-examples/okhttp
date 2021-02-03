### Integrating with Testhub and Circle CI

#### Environment variables

You can take advantage of CirclCI native environment variables to push to Testhub

* $CIRCLE_BUILD_NUM
* $CIRCLE_BRANCH

Add a new environment variable to your Circle CI Pipeline to specify your Testhub secret token


#### Getting the CLI

There are two ways to do it:

* Build the CLI into your docker image so you know where the CLI is
* Download it on the fly on the pipeline

For downloading these two steps should accomplish it

* wget https://github.com/testhub-io/testhub-cli/releases/download/v0.10/testhub-cli_v0.10_linux_386.tar.gz
* tar -xf ./testhub-cli_v0.10_linux_386.tar.gz

You can then use `testhub-cli` executable


#### Push to Testhub

`./testhub-cli upload -t $TESTHUB_TOKEN -b $CIRCLE_BUILD_NUM --branch $CIRCLE_BRANCH -p testhub-io-examples/okhttp -f '/home/circleci/test-results/junit/*.xml'`

Here
* `testhub-io-examples/okhttp` is your Testhub organization and repo
* `/home/circleci/test-results/junit/*.xml` is the location of your JUnit test output from the pipeline. Change it accordingly

#### View on Testhub

Navigate to `https://test-hub.io/<org>/projects/<repo>/runs`

For example

https://test-hub.io/testhub-io-examples/projects/okhttp/runs


#### Quickstart Video

[Watch this 2 minute video on integrating your CircleCI repo with Testhub](https://u.pcloud.link/publink/show?code=XZayGbXZQcx4n1t4kLmxt8RrmdlojV2oyptX)
