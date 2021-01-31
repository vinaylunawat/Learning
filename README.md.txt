# RealWear Device Mangement Service - Deployment/nstallation 

## Development Environment

## Introduction

This helps running dotnetcore application (Device Management Service) for development purpose.

## Prerequisites
(Recommended Version)
- Visual Studio 2019/ VS Code 2019
- Mongodb 3.4.24
- Postman Client 8.0.3

## Installation

1. Login with Github credential on https://github.com/realwear/Foresight-MS-DeviceManagement-RSystems and copy the url to clone.

2. Clone the repository in Visual Studio/ VS Code.

3. Clean & Build the Solution.

4. Restore all the dependencies.

5. Update the appsettings.json file with Authority, Service Bus & MongoDb related configuaration. 

6. Run the service application using F5 or command line argument.

7. Open the Postman and upload the Unit Test collection file from import option.

8. Run all integration test case collection to get the test summary.

## Configure the chart

The following items can be set in appconfig.json before running the application directly.

  "Storage": {
    "MongoDBConnectionString": "",
    "MongoDBDatabaseName": "",
    "ServiceBusConnectionString": ""
  },
  "Accounts": {
    "Authority": ""
  },

-------------------------------------------------------------------------------------------------------------------------
## Integration Testing Framework using Newman postman Collection

## Introduction

This run integration test on Realwear.DeviceManagement in a Kubernetes cluster using minikube.

## Prerequisites
(Recommended Version)
- Kubernetes cluster 1.20+
- MiniKube 1.17+
- Docker 19.03+

## How to use
`git clone `
then run `./integrations.sh`
Everything is preconfigured to run from single file `./integrations.sh` 


## Configuration

The following table lists the configurable parameters of the mongoDb and DeviceMangement and the default values.

| Parameter                                                                   | Description                                                                                                        | Default                         |
| --------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------| ------------------------------- |
| **mongoDb properties**                                                   |
| `mongodb.username`                                                       | mongodb username                                                                                                | `root`                      |
| `mongodb.password`                                                       | mongodb password                                                                                                | `admin123`                      |
| `mongodb.database`                                                       | mongodb database                                                                                                | `admin`                      |
| `mongodb.port`                                                           | mongodb port                                                                                                    | `27017`                          |
|**Kubernetes Configuration**  |
|`KUBE_CONTEXT` | KUBE_CONTEXT | `minikube`|
|`NAMESPACE`| Networking Namespace for cluster | `dmt`|
|** Yaml Files **|
|`asp_pod` | Contains ASP.Net Pod definition and env configurations|
|`asp_service` | Contains ASP.Net Core Network service definitions and ports|
|`mongo_create` | Contains MongoDb Pod definition and Credentials|
|`mongo_service`| Contains MongoDb Network service definition and ports|
|**Dockerfiles **|
|`DockerfileHarness` | Contains Docker Image Definition for Postman newman|
|`RealWear.DeviceManagement/DockerFile` | Contains Docker Image Definition for ASP.Net Core |


### Configure the Postman Collection
Postman Collection Resides in **testharness** folder. `RealWearDeviceManagementService_IntegrationTest.postman_collection` 
Refrences of this file is in `DockerfileHarness` and `integrations.sh` please make sure both files referring to correct `postman_collection` file.

