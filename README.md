# Visual Studio Code - Apama development (incl. Analytics Builder)

## Purpose & how to use

This repository gives you a quickstart into Apama development by providing a Visual Studio Code devcontainer environment for testing and deploying to your Cumulocity IoT Cloud tenant. In order to get started you can simply fork this repository and go through the instructions below.

## Instructions

### Prerequisites
1. You need to "buy" the [Apama docker](https://hub.docker.com/_/softwareag-apama-builder) (it is free with community edition, but you need to activate it for your docker account)
2. In order to deploy to Cumulcoity IoT Cloud you need a tenant with subscribed Apama and Analytics Builder
3. Ensure you are logged into your docker account inside Visual Studio Code when you build the devcontainer

### Before you build
Before you build the devcontainer within Visual Studio Code you should take a look at the devcontainer.json and adjust the build parameters and environment variables.

| Parameter                             | Description                                               | Comments                                      |
| -------------                         |:-------------:                                            | -----:                                        |
| APAMA_VERSION                         | the tag of the Apama base container                       | Please see docker hub for available versions  |
| APAMA_ANALYTICS_BUILDER_SDK_BRANCH    | the branch/version of the Analytics Builder SDK           | Please see [Github](https://github.com/SoftwareAG/apama-analytics-builder-block-sdk) for the available branches  |
| CUMULOCITY_SERVER_URL                 | The Cumulocity IoT instance to connect to                 |                                               |
| CUMULOCITY_TENANT                     | The tenantId of your Cumulocity IoT tenant                |                                               |
| CUMULOCITY_USERNAME                   | The username of your Cumulocity IoT user                  |                                               |
| CUMULOCITY_PASSWORD                   | The username of your Cumulocity IoT password              |                                               |
| CUMULOCITY_APPKEY                     | The application key the local Apama will use for testing  |                                               |

__*Note:*__

*The Analytics Builder SDK needs to be in the same version as the Apama in the Cloud when you want to deploy. Therefore it also recommended to use the same Apama version in the devcontainer (e.g. if the Cloud is in version 10.7 the same versions should be used in the devcontainer for both Apama and SDK).*

### Starting in Visual Studio Code
After you finsihed the configuration you can click the devcontainer icon in the bottom left of Visual Studio Code and select `Open Folder in Container...`.
Once the container has been built and started you should see four folders in your VCS workspace:
1. Development (the contents of this repository)
2. Analytics Builder SDK
3. Analytics Builder SDK Documentation
4. Apama

## Analytics Builder Development

Please check the SDK documentation for more detailed instructions.

### Testing
You can find an example pysys project under `Development -> example`. Simply navigate to the folder where the `pysysproject.xml` is located and run `pysys test`.

### Deploying to Cumulocity IoT
In order to deploy your blocks to your Cumulocity IoT tenant you can simply run `apama blocks deploy <extensionName>` from the folder where your blocks are located ( the .mon files). The extensionName can be freely chosen. You can try it out by navigating to `Development -> example -> blocks` and run the command from there.

### Undeploying from Cumulocity IoT
In order to remove your blocks again from your Cumulocity IoT tenant just run `apama blocks undeploy <extensionName>`. The extensionName has to be the same as you used when deploying.

---

These tools are provided as-is and without warranty or support. They do not constitute part of the Software AG product suite. Users are free to use, fork and modify them, subject to the license agreement. While Software AG welcomes contributions, we cannot guarantee to include every contribution in the master project.

Contact us at [TECHcommunity](mailto:technologycommunity@softwareag.com?subject=Github/SoftwareAG) if you have any questions.