### **4.1 Environment Variables**

Environment variables are a fundamental way to configure the behavior of applications running inside containers. In Kubernetes, you can set environment variables in Pods to provide configuration data, secrets, or other dynamic settings that your application might need.

#### **Setting Environment Variables in Pods**

There are several ways to set environment variables for containers in a Pod:

1. **Static Environment Variables**:

   - You can define environment variables directly in the Pod specification using the `env` field. These variables have static values that are hard-coded in the YAML configuration.

   Example:

   ```yaml
   apiVersion: v1
   kind: Pod
   metadata:
     name: my-pod
   spec:
     containers:
       - name: my-container
         image: nginx
         env:
           - name: ENV_VAR_NAME
             value: "value1"
   ```

   In this example:

   - `ENV_VAR_NAME` is set to `"value1"` in the `my-container` container.

2. **Environment Variables from ConfigMaps**:

   - Environment variables can be sourced from a `ConfigMap`, allowing you to manage configuration separately from the application code.

   Example:

   ```yaml
   apiVersion: v1
   kind: ConfigMap
   metadata:
     name: my-config
   data:
     ENV_VAR_NAME: "value1"

   apiVersion: v1
   kind: Pod
   metadata:
     name: my-pod
   spec:
     containers:
     - name: my-container
       image: nginx
       envFrom:
       - configMapRef:
           name: my-config
   ```

   In this example:

   - The `ENV_VAR_NAME` environment variable is loaded from the `my-config` ConfigMap.

3. **Environment Variables from Secrets**:

   - Similar to ConfigMaps, environment variables can be sourced from `Secrets` for sensitive data like passwords, tokens, or keys.

   Example:

   ```yaml
   apiVersion: v1
   kind: Secret
   metadata:
     name: my-secret
   type: Opaque
   data:
     ENV_SECRET_NAME: c2VjcmV0VmFsdWU=  # base64 encoded value

   apiVersion: v1
   kind: Pod
   metadata:
     name: my-pod
   spec:
     containers:
     - name: my-container
       image: nginx
       envFrom:
       - secretRef:
           name: my-secret
   ```

   In this example:

   - The `ENV_SECRET_NAME` environment variable is loaded from the `my-secret` Secret.

4. **Environment Variables from Downward API**:

   - Kubernetes provides the ability to expose Pod and container metadata (like the Pod's name, namespace, or labels) as environment variables using the Downward API.

   Example:

   ```yaml
   apiVersion: v1
   kind: Pod
   metadata:
     name: my-pod
   spec:
     containers:
       - name: my-container
         image: nginx
         env:
           - name: MY_POD_NAME
             valueFrom:
               fieldRef:
                 fieldPath: metadata.name
   ```

   In this example:

   - `MY_POD_NAME` is set to the name of the Pod using the Downward API.

#### **Configuring Secrets and ConfigMaps**

- **Secrets**:
  - Used to store sensitive information such as passwords, OAuth tokens, and SSH keys.
  - Stored in base64-encoded format and can be used as environment variables or mounted as files in a container.
  - Example creation command:
    ```bash
    kubectl create secret generic my-secret --from-literal=key1=supersecret
    ```
- **ConfigMaps**:
  - Used to store non-sensitive configuration data in key-value pairs or configuration files.
  - Can be injected into Pods as environment variables or mounted as files.
  - Example creation command:
    ```bash
    kubectl create configmap my-config --from-literal=key1=value1
    ```

Would you like to explore ConfigMaps or Secrets in more detail, or should we move on to the next section?

---

### **4.2 ConfigMaps**

ConfigMaps in Kubernetes are used to store non-sensitive configuration data in key-value pairs. They allow you to decouple configuration artifacts from the container image content, making it easier to manage and change configurations without altering the container image.

#### **Creating and Managing ConfigMaps**

1. **Creating ConfigMaps**:

   - **From Literal Values**:
     You can create a ConfigMap directly from the command line using literal key-value pairs.

     Example:

     ```bash
     kubectl create configmap my-config --from-literal=key1=value1 --from-literal=key2=value2
     ```

     This command creates a ConfigMap named `my-config` with two key-value pairs: `key1=value1` and `key2=value2`.

   - **From a File**:
     You can also create a ConfigMap from a configuration file.

     Example:

     ```bash
     kubectl create configmap my-config --from-file=config.properties
     ```

     This creates a ConfigMap where the contents of `config.properties` become the data of the ConfigMap.

   - **From Multiple Files**:
     You can create a ConfigMap from multiple files.

     Example:

     ```bash
     kubectl create configmap my-config --from-file=config1.properties --from-file=config2.properties
     ```

     This creates a ConfigMap with data from both `config1.properties` and `config2.properties`.

2. **Viewing ConfigMaps**:

   - You can view the details of a ConfigMap using the `kubectl get` and `kubectl describe` commands.

   Example:

   ```bash
   kubectl get configmap my-config
   kubectl describe configmap my-config
   ```

   The `describe` command provides detailed information about the ConfigMap, including all key-value pairs it contains.

3. **Editing ConfigMaps**:

   - ConfigMaps can be edited directly in the cluster.

   Example:

   ```bash
   kubectl edit configmap my-config
   ```

   This command opens the ConfigMap in a text editor, allowing you to make changes.

4. **Deleting ConfigMaps**:

   - ConfigMaps can be deleted when they are no longer needed.

   Example:

   ```bash
   kubectl delete configmap my-config
   ```

   This removes the ConfigMap from the cluster.

#### **Injecting ConfigMaps into Pods**

ConfigMaps can be injected into Pods in several ways, depending on how you want the application to access the configuration data.

1. **Injecting as Environment Variables**:

   - You can use ConfigMaps to populate environment variables in a container.

   Example:

   ```yaml
   apiVersion: v1
   kind: Pod
   metadata:
     name: my-pod
   spec:
     containers:
       - name: my-container
         image: nginx
         envFrom:
           - configMapRef:
               name: my-config
   ```

   In this example:

   - The environment variables in the `my-container` container are populated with key-value pairs from the `my-config` ConfigMap.

   Alternatively, you can specify individual keys as environment variables:

   ```yaml
   env:
     - name: CONFIG_VALUE
       valueFrom:
         configMapKeyRef:
           name: my-config
           key: key1
   ```

2. **Injecting as Files**:

   - ConfigMaps can also be mounted as files in a container’s filesystem.

   Example:

   ```yaml
   apiVersion: v1
   kind: Pod
   metadata:
     name: my-pod
   spec:
     containers:
       - name: my-container
         image: nginx
         volumeMounts:
           - mountPath: /etc/config
             name: config-volume
     volumes:
       - name: config-volume
         configMap:
           name: my-config
   ```

   In this example:

   - The `my-config` ConfigMap is mounted into the `/etc/config` directory in the container, with each key in the ConfigMap creating a corresponding file.

3. **Using ConfigMaps with Command-Line Arguments**:

   - ConfigMaps can be used to provide configuration data as command-line arguments to a container.

   Example:

   ```yaml
   apiVersion: v1
   kind: Pod
   metadata:
     name: my-pod
   spec:
     containers:
       - name: my-container
         image: nginx
         args:
           - "--config=$(CONFIG_PATH)"
         env:
           - name: CONFIG_PATH
             valueFrom:
               configMapKeyRef:
                 name: my-config
                 key: configPath
   ```

   In this example:

   - The `CONFIG_PATH` environment variable is populated from the `my-config` ConfigMap and passed as an argument to the container.

#### **Best Practices for Using ConfigMaps**

- **Decouple Configuration from Code**: Keep your configurations in ConfigMaps to ensure that application code remains unchanged even when configurations change.
- **Use ConfigMaps for Non-Sensitive Data**: Since ConfigMaps are not encrypted by default, they should only be used for non-sensitive configuration data.
- **Version Control**: Keep ConfigMap definitions in version control to manage changes over time.

Would you like to move on to Secrets in the next section, or do you want to explore ConfigMaps further?

---

### **4.3 Secrets**

Kubernetes Secrets are objects used to store sensitive information, such as passwords, tokens, or keys. Unlike ConfigMaps, Secrets are intended to keep this data confidential. Secrets can be used in Pods to provide secure access to sensitive information.

#### **Creating and Managing Secrets**

1. **Creating Secrets**:

   - **From Literal Values**:
     You can create a Secret directly from the command line using literal key-value pairs. The values are base64 encoded by Kubernetes.

     Example:

     ```bash
     kubectl create secret generic my-secret --from-literal=username=myUser --from-literal=password=myPassword
     ```

     This command creates a Secret named `my-secret` with two key-value pairs: `username=myUser` and `password=myPassword`.

   - **From Files**:
     You can create a Secret from files where the file contents become the Secret's data.

     Example:

     ```bash
     kubectl create secret generic my-secret --from-file=path/to/username.txt --from-file=path/to/password.txt
     ```

     This creates a Secret where the contents of `username.txt` and `password.txt` become the data of the Secret.

   - **From YAML**:
     You can define Secrets directly in a YAML file and apply them with `kubectl apply`.

     Example:

     ```yaml
     apiVersion: v1
     kind: Secret
     metadata:
       name: my-secret
     type: Opaque
     data:
       username: bXlVc2Vy
       password: bXlQYXNzd29yZA==
     ```

     In this YAML file:

     - The `username` and `password` values are base64-encoded strings. The original values can be decoded using `echo bXlVc2Vy | base64 --decode`.

2. **Viewing Secrets**:

   - By default, Secrets are not displayed in plain text for security reasons.

   Example:

   ```bash
   kubectl get secret my-secret
   kubectl describe secret my-secret
   ```

   The `describe` command shows metadata about the Secret but not the actual values.

   - To view the base64-encoded values, use:
     ```bash
     kubectl get secret my-secret -o yaml
     ```
   - To decode a specific value:
     ```bash
     echo $(kubectl get secret my-secret -o jsonpath="{.data.username}") | base64 --decode
     ```

3. **Editing Secrets**:

   - While you can edit Secrets, it's generally safer to delete and recreate them with updated values to avoid exposing sensitive information.

   Example:

   ```bash
   kubectl delete secret my-secret
   kubectl create secret generic my-secret --from-literal=username=newUser --from-literal=password=newPassword
   ```

4. **Deleting Secrets**:

   - You can delete a Secret when it is no longer needed.

   Example:

   ```bash
   kubectl delete secret my-secret
   ```

#### **Injecting Secrets into Pods Securely**

There are several ways to inject Secrets into Pods:

1. **Injecting as Environment Variables**:

   - Secrets can be exposed as environment variables to containers in a Pod.

   Example:

   ```yaml
   apiVersion: v1
   kind: Pod
   metadata:
     name: my-pod
   spec:
     containers:
       - name: my-container
         image: nginx
         env:
           - name: USERNAME
             valueFrom:
               secretKeyRef:
                 name: my-secret
                 key: username
           - name: PASSWORD
             valueFrom:
               secretKeyRef:
                 name: my-secret
                 key: password
   ```

   In this example:

   - The `USERNAME` and `PASSWORD` environment variables are populated from the `my-secret` Secret.

2. **Injecting as Files (Mounted Volumes)**:

   - Secrets can be mounted as files in the container’s filesystem. This method is often used for files like TLS certificates or SSH keys.

   Example:

   ```yaml
   apiVersion: v1
   kind: Pod
   metadata:
     name: my-pod
   spec:
     containers:
       - name: my-container
         image: nginx
         volumeMounts:
           - name: secret-volume
             mountPath: "/etc/secret"
             readOnly: true
     volumes:
       - name: secret-volume
         secret:
           secretName: my-secret
   ```

   In this example:

   - The `my-secret` Secret is mounted into the `/etc/secret` directory in the container. Each key in the Secret creates a file with the corresponding value as its content.

3. **Using Secrets with Kubernetes Service Accounts**:

   - Kubernetes automatically uses Secrets to manage credentials for Service Accounts, allowing Pods to securely interact with the Kubernetes API server.

   Example:

   - Service Account tokens are stored as Secrets and mounted into Pods at `/var/run/secrets/kubernetes.io/serviceaccount`.

#### **Security Considerations**

- **RBAC Controls**: Ensure that access to Secrets is restricted using Kubernetes Role-Based Access Control (RBAC) to prevent unauthorized access.
- **Encryption at Rest**: Enable encryption at rest for etcd, the data store for Kubernetes, to protect Secrets.
- **Audit Logs**: Monitor audit logs for access to Secrets to detect any unauthorized attempts.

Would you like to review any of these concepts further, or should we move on to another topic?
