# Prometheus KEDA ScaledObject

This manifest file defines a ScaledObject resource for Kubernetes, which automatically scales a deployment based on a Prometheus metric.

## ScaledObject Configuration

### Metadata

- **Name**: prometheus-scaledobject
- **Namespace**: default
- **Labels**: 
  - deploymentName: your-deployment-name

### Specification

- **scaleTargetRef**:
  - Name: your-deployment-name (replace with your actual deployment name)
- **pollingInterval**: 15 seconds
- **cooldownPeriod**: 30 seconds
- **minReplicaCount**: 1
- **maxReplicaCount**: 10

### Triggers

- **Type**: prometheus
  - **Metadata**:
    - **serverAddress**: <prometheus-server-address> (replace with your Prometheus server address)
    - **metricName**: access_frequency
    - **threshold**: 3
    - **query**: sum(rate(http_requests[2m]))  (You can use your own query)<br>

**Note:**: Replace placeholders <> with actual values in the manifest file to meet your project requirements.
