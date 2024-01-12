# 3. Creating Secrets

### 3.1 Intro

**1\. Basic Syntax:**

```bash
kubectl create secret generic <secret-name> --from-literal=<key1>=<value1> --from-literal=<key2>=<value2>
```

**2\. Create from File:**

```bash
kubectl create secret generic <secret-name> --from-file=<path-to-file>
```

**3\. Create from Literal (Interactive):**

```bash

kubectl create secret generic <secret-name> --from-literal=<key1>=<value1> --dry-run=client -o yaml | kubectl apply -f -
```

**4\. Display Secret:**

```bash
kubectl get secret <secret-name>
```

**5\. Describe Secret:**

```bash
kubectl describe secret <secret-name>
```

**Demonstrating Syntax and Options:**

- Explain the `--from-literal` and `--from-file` options for adding data to the secret.
- Discuss the `--dry-run=client -o yaml` method for creating secrets without applying them immediately.

---

## 3.1.2 Types of Secrets:

**1\. Generic Secrets:**

- **Use Case:** Storing arbitrary key-value pairs.
- **Example:**

  ```bash
  kubectl create secret generic my-generic-secret --from-literal=username=admin --from-literal=password=secretpassword
  ```

**2\. Docker Registry Secrets:**

- **Use Case:** Authenticating with private Docker registries.
- **Example:**

  ```bash
  kubectl create secret docker-registry my-docker-secret --docker-server=<registry-server> --docker-username=<username> --docker-password=<password> --docker-email=<email>
  ```

**3\. TLS Secrets:**

- **Use Case:** Storing TLS certificates for secure communication.
- **Example:**

  ```bash
  kubectl create secret tls my-tls-secret --cert=<path-to-cert-file> --key=<path-to-key-file>
  ```

---

## 3.1.3. Handling Sensitive Information:

**1\. Best Practices:**

- Store secrets in a dedicated namespace with restricted access.
- Rotate secrets regularly.
- Use tools like Sealed Secrets for additional encryption.

**2\. Guidelines for Password and Key Generation:**

- Encourage strong password policies.
- Utilize tools for secure key generation (e.g., OpenSSL).

**3\. Avoid Hardcoding Sensitive Information:**

- Discourage hardcoding passwords or keys in configuration files or scripts.
- Use secrets to inject sensitive information into pods.

---

## 3.2. Managing Secrets:

### 3.2.1. **Viewing and Updating <u>Existing</u> Secrets:**

**1\. View Existing Secrets:**

```bash
kubectl get secret
```

**2\. Display Secret Data:**

```bash
kubectl get secret <secret-name> -o jsonpath='{.data}'
```

**Note:** When you run this command, the output will be the base64-encoded data from the specified secret.

```bash
kubectl get secret <secret-name> -o jsonpath='{.data}' | base64 --decode
```

This will decode the base64-encoded data and display it in its original form.

**3\. Update Secrets Dynamically:**

- **Edit Secret:**

  ```bash
  kubectl edit secret <secret-name>
  ```

- **Apply Changes:**

  ```bash
  kubectl apply -f <modified-secret-file.yaml>
  ```

---

### 3.2.2. Adding, Removing, and Rotating Secrets:

**1\. Adding New Data:**

- **Using kubectl edit:**

  ```bash
  kubectl edit secret <secret-name>
  ```

- **Using kubectl apply:**

  ```bash
  kubectl create secret generic <secret-name> --from-literal=<new-key>=<new-value> --dry-run=client -o yaml | kubectl apply -f -
  ```

**2\. Removing Data:**

- **Using kubectl edit:**

  ```bash
  kubectl edit secret <secret-name>
  ```

  - Remove the unwanted key-value pairs and save the changes.

- **Using kubectl apply:**

  ```bash
  `kubectl create secret generic <secret-name> --from-literal=<key-to-remove>- --dry-run=client -o yaml | kubectl apply -f -
  ```

**3\. Rotating Secrets:**

- **Generate New Secrets:**
  - Create new secrets with updated credentials.
- **Update Pods:**
  - Ensure that applications referencing the secrets are updated to use the new secrets.
- **Delete Old Secrets:**

  - Once confirmed, delete the old secrets.

  ```bash
  kubectl delete secret <old-secret-name>
  ```

### Best Practices:

- Regularly rotate secrets to minimize the risk of compromise.
- Use automation for secret rotation where applicable.

---

## 3.3. Pod Configuration with Secrets

#### **3.3.1 Mounting Secrets into Pods:**

**1\. Integrating Secrets into Pod Specifications:**

- In the Pod manifest, define a volume for the Secret.

```yaml
volumes:
  - name: my-secret-volume
    secret:
      secretName: my-secret
```

**2\. Mounting Paths:**

- Specify the mount path within the containers.

```yaml
containers:
  - name: my-container
    volumeMounts:
      - name: my-secret-volume
        mountPath: "/path/to/mount"
```

**Example:**

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: mypod
spec:
  volumes:
    - name: my-secret-volume
      secret:
        secretName: my-secret
  containers:
    - name: my-container
      image: my-image
      volumeMounts:
        - name: my-secret-volume
          mountPath: "/etc/secrets"
```

**3.3.2 Using Secrets as Environment Variables:**

**1\. Reference Secret in Environment Variables:**

```yaml
containers:
  - name: my-container
    env:
      - name: SECRET_USERNAME
        valueFrom:
          secretKeyRef:
            name: my-secret
            key: username
      - name: SECRET_PASSWORD
        valueFrom:
          secretKeyRef:
            name: my-secret
            key: password
```

### **Best Practices:**

- Keep the volume paths and environment variable names consistent across containers.
- Ensure that sensitive information is securely accessed within the Pod.

---

### Secrets with Docker Image

**Same as configMaps**

1. First create your secrets.
2. Then apply you Pod or Deployments.

---
