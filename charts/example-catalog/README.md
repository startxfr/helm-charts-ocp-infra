# STARTX helm : example-catalog

This helm chart is chart used to deploy various example of application used in Startx demo and mostly based on [sxapi helm chart](https://startxfr.github.io/helm-repository/charts/sxapi) microservice framework.

## Requirements and guidelines

Read the [startx helm-repository homepage](https://startxfr.github.io/helm-repository) for
more information on how to use theses resources.

## Deploy this helm chart on openshift

### 1. Connect to your Openshift cluster

```bash
oc login -t <token> <cluster-url>
```

### 2. Install the repository

```bash
helm repo add startx https://startxfr.github.io/helm-repository/packages/
```

### 3. Get information about this chart

```bash
helm show chart startx/example-catalog
```

### 4. Install this chart

```bash
helm install startx/example-catalog
```

## Values dictionary

### context values dictionary

| Key                 | Default   | Description
| ------------------- | --------- | -----------------------------------------------------
| context.scope       | default   | Name of the global scope for this application (organisational tenant)
| context.cluster     | localhost | Name of the cluster running this application (plateform tenant)
| context.environment | dev       | Name of the environement for this application (ex: dev, factory, preprod or prod)
| context.component   | demo      | Component name of this application (logical tenant)
| context.app         | sxapi     | Application name (functionnal tenant, default use Chart name)
| context.version     | 0.0.1     | Version name of this application (default use Chart appVersion)

### example-catalog values dictionary

| Key                   | Default    | Description
| --------------------- | ---------- | -----------------------------------------------------
| sxapi.service.enabled | false      | Enable service for this application
| sxapi.version         | 0.3.57     | Sxapi image version to run
| sxapi.profile         | prod:start | Profile to run inside the container
| sxapi.debug           | true       | Enable debuging of the container
| sxapi.replicas        | 1          | Define the number of replicas for this sxapi instance
| sxapi.data            | string     | Files to load into the application

## Values files

### Default values file (values.yaml)

Complete deployment of an sxapi application with the following characteristics :

- 1 **service** named **example-catalog** load balancing to pod deployed
- 1 **deployment** named **example-catalog** deploying **1 pod** from version **0.3.57** sxapi image running the **prod:start** command with debug disabled
- 2 **configMap** holding sxapi configuration and pod environment variable context

```bash
# base configuration running default configuration
helm install startx/example-catalog
```

### Development values file (values-dev.yaml)

Complete deployment of a sxapi development application with the following characteristics :

- 1 **service** named **example-catalog-dev** load balancing to pod deployed
- 1 **deployment** named **example-catalog-dev** deploying **1 pod** from version **0.3.57** sxapi image running the **dev:start** command with debug disabled
- 2 **configMap** holding sxapi configuration and pod environment variable context

```bash
# base configuration running tekton v1.0.1 configuration
helm install startx/example-catalog -f https://raw.githubusercontent.com/startxfr/helm-repository/master/charts/example-catalog/values-dev.yaml
```

## History

| Release | Date       | Description
| ------- | ---------- | -----------------------------------------------------
| 0.3.225 | 2021-05-29 | Create chart example-catalog from example-sxapi
| 0.3.227 | 2021-05-29 | Add the storage_context demo resources