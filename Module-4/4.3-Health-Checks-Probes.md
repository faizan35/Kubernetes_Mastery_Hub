# Health Checks with Probes

Kubernetes uses **probes** to assess the health of your application's containers and pods.

#### What are Probes?

- Mechanism used to **check and monitor** the **health** of containers running within pods.

**<u>There are three types of probes</u> :-**

1. Readiness probes,
2. Liveness probes, and
3. Startup probes.

---

## 1. Readiness Probes:

Purpose
: It tells pod is ready or not to start accepting traffic.

Scenario
: Useful during **rolling updates**.

How it Works
: It sends a request to a specified endpoint (path and port) within the container. If the container responds successfully, the pod is considered ready.

- Example in a Deployment YAML:

```yaml
readinessProbe:
  httpGet:
    path: /healthz
    port: 80
  initialDelaySeconds: 5
  periodSeconds: 5
```

## Liveness Probes:

Purpose
: Checks whether a container is still running and healthy.

Scenario
: Helps restart containers that are stuck in an unrecoverable state.

How it Works
: It similarly sends a request to a specified endpoint. If the container fails to respond successfully within a specified time frame or after a certain number of consecutive failures, Kubernetes considers the container unhealthy and may restart it.

- Example in a Deployment YAML:

```yaml
livenessProbe:
  httpGet:
    path: /healthz
    port: 80
  initialDelaySeconds: 10
  periodSeconds: 5
```

## Startup Probes:

Purpose
: Delays the startup of containers until a specified condition is met.

Scenario
: Ensures that a container is fully initialized before it starts receiving traffic.

How it Works
: The startup probe is initiated when a pod starts. It performs checks similar to readiness probes but is specifically designed to determine **when a container is fully initialized** and ready to receive traffic.

- Example in a Deployment YAML:

```yaml
startupProbe:
  httpGet:
    path: /healthz
    port: 80
  failureThreshold: 30
  periodSeconds: 10
```

In these examples:

- **`httpGet`**: specifies an HTTP request to the `/healthz` endpoint on port `80`.
- **`initialDelaySeconds`**: sets a delay before the first probe is executed.
- **`periodSeconds`**: defines the interval between subsequent probes.
- **`failureThreshold`**: (for **startup probes**) determines the number of consecutive failures required for the probe to be considered failed.

---
