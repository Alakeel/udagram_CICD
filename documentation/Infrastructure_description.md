# Infrastructure_description

## Process Workflow

1. End-user accesses front-end via (S3) endpoint.
1. Front-end communicates with Backend API (AWS Elastic Beanstalk) & (EC2).
1. Backend API communicates with database (Postgres) in (AWS RDS) to update/delete data.

<br/>

## Overview Architecture Diagram
<img src="./screenshots/sc-infra-overview.png" alt="circleci" />

## AWS Cloud Service
The following AWS services have been used to deploy and access the application from/to the cloud.

### S3
> Stores the static front-end application files, also it can be used to store any additional static resources for instance media.
<img src="./screenshots/sc-aws-s3.png" alt="s3" />

### Elastic Beanstalk
> Using EB to deploy the backend application to the Cloud where EB handles the creation and setup a lot of services including EC2, autoscaling, and Elastic Load Balancer and more.
<img src="./screenshots/sc-aws-eb.png" alt="eb" />

### RDS
> Setup and operate the Relational Database (Postgres).
<img src="./screenshots/sc-aws-rds.png" alt="rds" />

<br/>

## CircleCI Pipeline Overview

> Check **Pipeline_description.md** for more details.

<img src="./screenshots/sc-circleci-2.png" alt="frontend" />

---
@Author:
Abdullah Alakeel
