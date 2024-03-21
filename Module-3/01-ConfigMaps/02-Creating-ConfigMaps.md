# Creating ConfigMaps

## Using `kubectl`:

**1\. Basic Syntax:**

```bash
kubectl create configmap <configmap-name> --from-literal=<key1>=<value1> --from-literal=<key2>=<value2>
```

**2\. Create from File:**

```bash
kubectl create configmap <configmap-name> --from-file=<path-to-file>
```

OR

```bash
kubectl create configmap <configmap-name> --from-file=<path-to-file1> --from-file=<path-to-file2>
```

**3\. Create from Directory:**

```bash
kubectl create configmap <configmap-name> --from-file=<path-to-directory>
```

**4\. Create from Environment File (`.env`):**

```bash
kubectl create configmap <configmap-name> --from-env-file=<path-to-env-file>
```

**5\. Display ConfigMap:**

```bash
kubectl get configmap <configmap-name>
```

**6\. Describe ConfigMap:**

```bash
kubectl describe configmap <configmap-name>
```

**7\. Displaying Data:**

It shows a yaml representaion of the congigmap.

```bash
kubectl get configmap <configmap-name> -o yaml
```

---

## ConfigMap with Docker Image

If you're pulling an image from Docker Hub and you want to create a ConfigMap with environment variables for that image.

- Create the ConfigMap **before** applying the deployment YAML file.
- The ConfigMap is a separate Kubernetes resource that contains the configuration data you want to inject into your pods.

Step 1:
: First create your configMap. Say `name: myconfigmap`

```bash
kubectl create configmap myconfigmap --from-file=<path-to-env-file-inside-container>
```

Step 2: ConfigMaps are in Pod level
: Create Deployment YAML

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
        - name: my-container
          image: docker.io/yourusername/yourimage:yourtag
          envFrom:
            - configMapRef:
                name: myconfigmap
```

Step 3:
: Apply the Deployment

```bash
kubectl apply -f mydeployment.yaml
```

This deployment uses the ConfigMap (`myconfigmap`) to inject environment variables into the container (`my-container`). The environment variables are specified in the environment file inside the ConfigMap.

---

## Best Practices:

- Organize configuration files in a directory structure that reflects the application's needs.
- Use subdirectories or file naming conventions for clarity.
- Be mindful of file formats (JSON, YAML) to maintain consistency.

---
