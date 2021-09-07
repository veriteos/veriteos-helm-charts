# Veriteos Helm Charts

This repo contains all Veriteos Helm charts and their configuration options.

## Chart: Sentinel

Custom event monitoring server and agent.
Current chart version is `0.1.1`

## Prerequisits

To use the charts here, Helm must be configured for your Kubernetes cluster. Setting up Kubernetes and Helm is outside the scope of this README. Please refer to the Kubernetes and Helm documentation.

The versions required are:

Helm 3.5+ - This is the earliest version of Helm tested. It is possible it works with earlier versions but this chart is untested for those versions.
Kubernetes 1.15+ - This is the earliest version of Kubernetes tested. It is possible that this chart works with earlier versions but it is untested.

## Installation

Charts are published to https://veriteos-charts.storage.googleapis.com/charts.

Run the following commands to add the repository

veriteos-charts/charts

```
helm repo add veriteos-charts https://veriteos-charts.storage.googleapis.com/charts
helm repo update
```

Install Sentinel

### In case you've previously installed a veriteos chart and skipped the previous add & update phase, make sure to update there repo before install, otherwise your release might be with an outdated version

```
helm repo update
```

```
helm install sentinel-release veriteos-charts/sentinel-chart
```

## Customize your installation

This Veriteos chart comes with a `values.yaml` file that allows for configuration and customization of all sub-charts.

Please note that you will need to provide a valid API key inside `values.yaml` key for the sentinel to function properly.

## Chart Values

| Key                          | Type    | Default                      | Description                                                 |
| ---------------------------- | ------- | ---------------------------- | ----------------------------------------------------------- |
| namespace                    | string  | `"sentinel"`                 | Kubernetes namespace                                        |
| deployment.apiKey            | string  | `""`                         | Api key of your sentinal release                            |
| deployment.apiHost           | string  | `"api.veriteos.com"`         | Address of veriteos public ingree API                       |
| deployment.server.image      | string  | `"veriteos/sentinel-server"` | Sentinel server image name                                  |
| deployment.server.tag        | string  | `"0.0.1"`                    | Sentinel server image tag                                   |
| deployment.server.replicas   | integer | `1`                          | Sentinel server replica count                               |
| deployment.agent.name        | string  | `"companyName"`              | Sentinel agent name displayed inside veriteos control panel |
| deployment.agent.image       | string  | `"veriteos/sentinel-worker"` | Sentinel agent image name                                   |
| deployment.agent.tag         | string  | `"0.0.3"`                    | Sentinel agent image tag                                    |
| deployment.agent.replicas    | integer | `1`                          | Sentinel agent replica count                                |
| deployment.redpanda.image    | string  | `"vectorized/redpanda"`      | Redpanda image name                                         |
| deployment.redpanda.tag      | string  | `"release-20.11.6"`          | Redpanda image tag                                          |
| deployment.redpanda.replicas | integer | `1`                          | Redpanda replica count                                      |
