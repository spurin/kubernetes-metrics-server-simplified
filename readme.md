# Kubernetes Metrics Server Simplified

Kubernetes Metrics Server Simplified is a streamlined version of the official [Kubernetes Metrics Server](https://github.com/kubernetes-sigs/metrics-server) which is typically deployed using [components.yaml](https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml). This simplified version has been tailored specifically for use in non-production, lab environments.

## Modifications

This project introduces the following modifications to the official Metrics Server deployment manifest to facilitate ease of use in test environments:

- **Pinned Image Version:** The image version has been pinned to ensure consistency across deployments.
- **Removed `nodeSelector`:** The `nodeSelector` configuration has been removed to allow for deployment on any node within a cluster.
- **Insecure TLS Communication:** Added the `--kubelet-insecure-tls` flag to allow for insecure communications with kubelets, suitable for environments where strict TLS verification is not required.

## Warning

This version of the Metrics Server is intended **only for non-production, lab environments**. It disables security features for ease of use and should not be used in a production environment.

## Prerequisites

Before you begin with the installation of Kubernetes Metrics Server Simplified, ensure you have:

- A Kubernetes cluster running.
- `kubectl` configured to communicate with your cluster.

## Installation

To install the Metrics Server Simplified in your Kubernetes cluster, follow these steps:

1. Apply the configuration to your cluster:

    ```bash
    kubectl apply -f https://raw.githubusercontent.com/spurin/kubernetes-metrics-server-simplified/main/components.yaml
    ```

2. Verify the installation:

    ```bash
    kubectl get deployment metrics-server -n kube-system
    ```

You should see the metrics-server deployment running in the `kube-system` namespace.

## Usage

Once installed, you can use the Metrics Server to gather metrics from your Kubernetes nodes and pods. For example, you can use the following command to see CPU and memory usage of nodes:

```bash
kubectl top nodes
```
