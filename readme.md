# Veriteos Helm Charts

This repo contains all Veriteos Helm charts and their configuration options.

## Chart: Sentinel

Custom event monitoring server and agent.
Current chart version is `0.1.0`

## Installation

Run the following commands to add the repository

```
helm repo add veriteos-charts #TODO
helm repo update
```

Install Sentinel

```
helm install sentinel-release veriteos-charts/sentinel
```

## Customize your installation

This Veriteos chart comes with a `values.yaml` file that allows for configuration and customization of all sub-charts.

For more details, please see: #TODO add values.yaml details

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
