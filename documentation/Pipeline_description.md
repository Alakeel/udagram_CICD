# Pipeline Description
## Overview
### Process Workflow
1. New Commit is pushed to the project repository in Github.
2. Github trigger and CircleCI listen for the new commits of current followed project repository and create a new pipeline for the given workflows below.
3. Once the build job is passed, a manual approval required to run the deploy job.
4. CircleCI handles the deployment to AWS and uses the Environment secret given in the project settings to EB.

This pipeline is built using CircleCI 2.1 and includes the following orbs:

- node (circleci/node@5.0.2)
- eb (circleci/aws-elastic-beanstalk@2.0.1)
- aws-cli (circleci/aws-cli@3.1.1)

### Pipeline Diagram
<img src="./screenshots/sc-pipeline-overview.png" alt="pipeline diagram" />

---

## Workflows

The pipeline consists of a single workflow named 'udagram' that includes the following jobs:

1. Build
1. Hold (for manual approval, only runs on the master branch)
1. Deploy (runs after manual approval)

---

## Pipeline Jobs

### Build
The build job uses a docker image cimg/node:14.15** and contains the following steps:

  1. Installs Node 14.15
  2. Checks out the code
  3. Installs front-end and API dependencies
      ```npm run frontend:install && npm run api:install```
  4. Runs lint and build commands for the front-end and API
    ```npm run frontend:lint && npm run frontend:build && npm run api:build```



### Deploy
The deploy job uses a docker image cimg/base:stable and contains the following steps:

1. Installs Node 14.15
1. Sets up AWS Elastic Beanstalk and AWS CLI
1. Checks out the code
1. Set the Environment Secret from CircleCi to EB
1. Deploys the app using `npm run deploy`

---
@Author:
Abdullah Alakeel

