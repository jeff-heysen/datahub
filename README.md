# DataHub: A Generalized Metadata Search & Discovery Tool
[![Build Status](https://travis-ci.org/linkedin/datahub.svg)](https://travis-ci.org/linkedin/datahub)
[![License](https://img.shields.io/github/license/linkedin/datahub)](LICENSE)
[![Gitter](https://img.shields.io/gitter/room/nwjs/nw.js.svg)](https://gitter.im/linkedin/datahub)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/linkedin/datahub/blob/master/CONTRIBUTING.md)

![DataHub](docs/imgs/datahub-logo.png)

## Introduction
DataHub is LinkedIn's generalized metadata search & discovery tool. To learn more about DataHub, check out our 
[LinkedIn blog post](https://engineering.linkedin.com/blog/2019/data-hub) and [Strata presentation](https://speakerdeck.com/shirshanka/the-evolution-of-metadata-linkedins-journey-strata-nyc-2019). 
You should also visit [DataHub Architecture](docs/architecture/architecture.md) to get a better understanding of how DataHub is implemented and 
[DataHub Onboarding Guide](docs/how/entity-onboarding.md) to understand how to extend DataHub for your own use case.
This repository contains the complete source code to be able to build DataHub's frontend & backend services.

## Quickstart
1. Install [docker](https://docs.docker.com/install/) and [docker-compose](https://docs.docker.com/compose/install/). Make sure to configure Docker to allocate enough hardware resources for Docker engine. Tested & confirmed config: 4 CPUs, 8GB RAM, 2GB Swap area.
2. Clone this repo.
3. Open Docker either from the command line or the Desktop app and ensure it is up and running then `cd` into the cloned `datahub` repo.
4. Run below command to download and run all Docker containers in your local:
    ```
    cd docker/quickstart && docker-compose pull && docker-compose up --build
    ```
    This step takes long time and it might be hard to figure out when DataHub is fully up. You can refer to [this guide](https://github.com/linkedin/datahub/blob/master/docs/debugging.md#how-can-i-confirm-if-all-docker-containers-are-running-as-expected-after-a-quickstart) to confirm DataHub is up and running.
5. At this point, you should be able to start `DataHub` by opening [http://localhost:9001](http://localhost:9001) in your browser. You can sign in using `datahub` as both username and password. However, there is no data just yet.
6. To ingest [provided](https://github.com/linkedin/datahub/blob/master/metadata-ingestion/mce-cli/bootstrap_mce.dat) sample data to DataHub, switch to a new terminal, `cd` into the cloned `datahub` repo, and run below command:
    ```
    docker build -t ingestion -f docker/ingestion/Dockerfile . && cd docker/ingestion && docker-compose up
    ```
    After running this, you should be able to see sample data in DataHub.

Refer to [debugging guide](docs/debugging.md) if you have issues in any of the above steps.

## Quicklinks
* [DataHub Architecture](docs/architecture/architecture.md)
* [DataHub Onboarding Guide](docs/how/entity-onboarding.md)
* [Docker Images](docker)
* [Frontend App](datahub-frontend)
* [Web Client App](datahub-web)
* [Generalized Metadata Service](gms)
* [Metadata Consumer Jobs](metadata-jobs)
* [Metadata Ingestion](metadata-ingestion)

## Releases
See [Releases](https://github.com/linkedin/datahub/releases) page for more details.

## Roadmap
1. [Kubernetes](https://kubernetes.io/) for container orchestration
2. Deploy DataHub to [Azure Cloud](https://azure.microsoft.com/en-us/)
