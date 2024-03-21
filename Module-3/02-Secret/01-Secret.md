## What are Secrets?

- Designed for storing sensitive information, like passwords, API keys, and certificates, OAuth tokens, and SSH keys.
- Data is Base64 encoded for obfuscation(making something difficult to understand), <u>though it's not a form of secure encryption</u>.
- Provides a more secure way to handle confidential information within Kubernetes.
- Secrets are stored in **etcd** encrypted at rest and only accessible to the nodes or users that have the necessary permissions.

## Types of Secrets:

1.  **Opaque Secrets**: These are the most common type of secrets. They can store arbitrary data, such as JSON, XML, or binary data.
2.  **Docker Registry Secrets**: Used to authenticate with Docker registries to pull private images.
3.  **TLS Secrets**: Used to store SSL/TLS certificates and keys.
4.  **Service Account Tokens**: Automatically created by Kubernetes for pods to authenticate with the API server.

## Creating and Managing Secrets:

Secrets can be created and managed using either imperative commands or declarative YAML manifests.

#### 1. **Imperative Commands**:

```bash
# Create a generic secret
kubectl create secret generic my-secret --from-literal=password=mysupersecretpassword

# Create a secret from a file
kubectl create secret generic tls-secret --from-file=cert.pem --from-file=key.pem

# Display the details of a secret
kubectl get secret my-secret -o yaml
```

#### 2. **Declarative YAML Manifests**:

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: my-secret
type: Opaque
data:
  username: dXNlcm5hbWU= # base64 encoded username
  password: cGFzc3dvcmQ= # base64 encoded password
```

- To **encode** data: `echo -n "hello" | base64`
- To **decode** data: `echo "aGVsbG8=" | base64 --decode`

## Consuming Secrets in Pods ( ):

Use sensetive information stored in secrets in:

#### 1. **Environment Variables**:

```yaml
env:
  - name: DB_USERNAME
    valueFrom:
      secretKeyRef:
        name: my-secret
        key: username
```

#### 2. Volume Mounts:

```yaml
volumes:
  - name: secret-volume
    secret:
      secretName: my-secret
containers:
  - name: my-container
    volumeMounts:
      - name: secret-volume
        mountPath: /etc/secret-volume
        readOnly: true
```

### Best Practices for Secrets Management:

1.  **Avoid Hardcoding Secrets**: Never hardcode sensitive information in the YAML files or the Docker images.
2.  **Use RBAC**: Restrict access to Secrets using Kubernetes Role-Based Access Control (RBAC) to only necessary users or service accounts.
3.  **Regularly Rotate Secrets**: Rotate sensitive data such as passwords and keys periodically.
4.  **Encrypt Communication**: Ensure that all communication within the cluster and with external systems is encrypted to protect secret data in transit.
5.  **Monitor Access**: Implement auditing and monitoring to track access to Secrets and detect any unauthorized access attempts.
6.  **Consider External Solutions**: For more advanced use cases or compliance requirements, consider using external secret management solutions like **HashiCorp Vault** or Azure Key Vault.

## Secrets Use Cases:

**1\. Database Credentials:**

- **Scenario:** Your application needs to connect to a database, and you want to secure the database credentials.
- **Use Case:** Store the database username, password, and connection details in a Secret. Mount the Secret as files or environment variables in the application pods securely.

**2\. API Keys:**

- **Scenario:** Your application interacts with external APIs and requires API keys.
- **Use Case:** Instead of hardcoding API keys in your application code or configuration files, use Kubernetes Secrets to manage and securely inject API keys into your pods.

**3\. SSL/TLS Certificates:**

- **Scenario:** Securing communication between services or exposing your application over HTTPS.
- **Use Case:** Store SSL/TLS certificates as Secrets. Mount these certificates into your pods, enabling secure communication without exposing sensitive information in your application code.

**4\. Configuration Files with Sensitive Data:**

- **Scenario:** Your application uses sensitive configuration files.
- **Use Case:** Store the sensitive configuration files (e.g., for authentication or authorization) in Secrets. Mount these files into your pods to ensure secure access and handling of sensitive information.

---
