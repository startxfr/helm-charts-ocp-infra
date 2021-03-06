# Cluster VPA

This helm chart is used to deploy VerticalPodAutoscaler pod managed by a dedicated operator.
This chart is part of the cluster-xxx startx helm chart that doesn't create application deployment but rather represent a cluster configuration state orchestrated by gitops tools like ArgoCD.

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
helm show chart startx/cluster-vpa
```

### 4. Install this chart

```bash
helm install startx/cluster-vpa
```

## Default values

Complete deployment of a project with the following characteristics :

xxxxxx TO DO xxxxxx

```bash
# base configuration running default configuration
helm install startx/cluster-vpa
```

## Others values availables

- **startx** : VerticalPodAutoscaler operator (see [values.yaml](https://raw.githubusercontent.com/startxfr/helm-repository/master/charts/cluster-vpa/values-startx.yaml))

```bash
helm install startx/cluster-vpa -f https://raw.githubusercontent.com/startxfr/helm-repository/master/charts/cluster-vpa/values-startx.yaml
```

## History

| Release | Date       | Description                                                                  |
| ------- | ---------- | ---------------------------------------------------------------------------- |
| 0.3.179 | 2021-02-10 | Create chart cluster-vpa from cluster-ptp                                    |
| 0.3.187 | 2021-02-13 | Align cluster chart release to 0.3.187                                       |
| 0.3.191 | 2021-02-13 | Update cluster chart dependencies to 0.3.189                                 |
| 0.3.199 | 2021-02-20 | prepare alpha release of 0.4 and update dependencies charts                  |
| 0.3.201 | 2021-02-20 | Update icon and image for charts                                             |
| 0.3.203 | 2021-02-21 | Upgrade chart release informations                                           |
| 0.3.207 | 2021-04-19 | Core chart dependencies moved to v0.3.205                                    |
| 0.3.209 | 2021-05-06 | Prepare upgrade to 4.7 and add template for AFD                              |
| 0.3.215 | 2021-05-06 | Align all chart to release 0.3.215                                           |
| 0.3.221 | 2021-05-06 | Move to VPA operator version 5.0.3-6 (OCP 4.7 compat)                        |
| 0.3.225 | 2021-05-10 | Update all chart to use new RBAC naming                                      |
| 0.3.227 | 2021-05-27 | Update vpa operator to 4.7.0                                                 |
| 0.3.228 | 2021-06-02 | Update operator to version 4.7.0                                             |
| 0.3.305 | 2021-06-04 | publish stable update for the full repository                                |
| 0.3.343 | 2021-06-06 | publish stable update for the full repository                                |
| 0.3.381 | 2021-06-10 | Align example and cluster charts dependencies to basic chart version 0.3.377 |
| 0.3.390 | 2021-06-12 | Prepare 0.4.0 release
| 0.3.423 | 2021-06-17 | Prepare the v0.4 release. Stable aligned version of all charts
| 0.3.431 | 2021-07-05 | Move to dependencies 1.18.0
