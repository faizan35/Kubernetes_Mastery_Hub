# 6.1.2. Service Accounts and Permissions

## Story

Imagine Kubernetes is like a big office building. **RBAC** is like the rulebook that says what each employee is allowed to do—like which rooms they can enter and what equipment they can use.

Now, the **Service Account** is like the ID badge you give to a specific robot working in the building. This robot (your application running in a Pod) needs an ID badge to get around and do its job.

- **RBAC** sets the rules (e.g., “Anyone with a ‘Cleaning Staff’ badge can enter the cleaning supplies room”).
- **Service Account** is the ID badge you give to the robot so it knows which rules apply to it.

Why do you need the Service Account? Because without it, your robot doesn’t have an ID badge and can’t access anything. The Service Account tells Kubernetes, “This is who I am,” and RBAC then checks what that identity is allowed to do.

So, Service Accounts are just the way to give your applications a "badge" so they can follow the rules set by RBAC.

## **Overview**

A **Service Account** in Kubernetes provides an identity for processes running in a Pod, allowing them to interact with the Kubernetes API and other resources securely. Service Accounts are especially useful for managing permissions and ensuring that applications running in your cluster have the appropriate access to resources.

### **Key Concepts**

- **Default Service Account:** Every namespace in Kubernetes has a default Service Account that is automatically assigned to Pods unless a different Service Account is specified.
- **Custom Service Account:** You can create custom Service Accounts with specific permissions to control what a Pod can access.

### **1. Default Service Account**

By default, Kubernetes automatically assigns a Service Account to every Pod in a namespace. This default Service Account has limited permissions.

#### **Example: Using the Default Service Account**

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-default-pod
  namespace: default
spec:
  containers:
    - name: my-container
      image: nginx
```

**Explanation:**

- **Namespace:** `default` – The Pod is created in the `default` namespace.
- **Service Account:** If not specified, Kubernetes assigns the default Service Account in the `default` namespace.

**Use Case:**
This setup is suitable for simple applications that don't require specific API access or where security requirements are minimal. The Pod will use the default Service Account with minimal permissions.

### **2. Custom Service Account**

You can create a custom Service Account when you need to provide specific permissions to a Pod. This is useful when the Pod needs to interact with the Kubernetes API or other cluster resources with more granular control.

#### **Example: Creating a Custom Service Account**

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: custom-sa
  namespace: dev-namespace
```

**Explanation:**

- **Namespace:** `dev-namespace` – The Service Account is created in the `dev-namespace` namespace.
- **Name:** `custom-sa` – The name of the custom Service Account.

#### **Example: Using the Custom Service Account in a Pod**

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-custom-pod
  namespace: dev-namespace
spec:
  serviceAccountName: custom-sa
  containers:
    - name: my-container
      image: nginx
```

**Explanation:**

- **Service Account:** `custom-sa` – The Pod uses the `custom-sa` Service Account instead of the default one.

**Use Case:**
This setup is ideal when you need to provide specific permissions to a Pod. For example, if the Pod needs to interact with certain resources like ConfigMaps or Secrets, you can assign the necessary permissions to the `custom-sa` Service Account.

### **3. Granting Permissions to a Service Account**

To grant specific permissions to a Service Account, you use RoleBindings or ClusterRoleBindings.

#### **Example: Granting Permissions to a Custom Service Account**

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  namespace: dev-namespace
  name: secret-reader
rules:
  - apiGroups: [""]
    resources: ["secrets"]
    verbs: ["get", "list"]
```

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: bind-secret-reader
  namespace: dev-namespace
subjects:
  - kind: ServiceAccount
    name: custom-sa
    namespace: dev-namespace
roleRef:
  kind: Role
  name: secret-reader
  apiGroup: rbac.authorization.k8s.io
```

**Explanation:**

- **Role:** `secret-reader` – Grants read access to Secrets in the `dev-namespace`.
- **RoleBinding:** `bind-secret-reader` – Binds the `secret-reader` Role to the `custom-sa` Service Account.

**Use Case:**
This setup is useful when a Pod running with the `custom-sa` Service Account needs to access Secrets in the `dev-namespace`. For example, if the Pod needs to read database credentials stored in Secrets, you would use this configuration.

### **4. Disabling Service Account Token Automounting**

By default, Kubernetes mounts the Service Account token into Pods. If a Pod does not need to interact with the Kubernetes API, you can disable this token mounting to reduce the attack surface.

#### **Example: Disabling Service Account Token Automounting**

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-secure-pod
  namespace: dev-namespace
spec:
  automountServiceAccountToken: false
  containers:
    - name: my-container
      image: nginx
```

**Explanation:**

- **automountServiceAccountToken:** `false` – Prevents the Service Account token from being automatically mounted into the Pod.

**Use Case:**
This is useful for workloads that do not need to communicate with the Kubernetes API, such as static content servers or isolated microservices. By disabling token automounting, you reduce the risk of token misuse if the Pod is compromised.

### **Summary of Use Cases**

- **Default Service Account:** Use when your Pod doesn’t require specific API access or when security concerns are minimal.
- **Custom Service Account:** Create and use when your Pod needs specific permissions to interact with Kubernetes resources. It gives you more granular control over what the Pod can do.

- **Granting Permissions:** Use RoleBindings or ClusterRoleBindings to assign specific permissions to your Service Accounts. This is necessary when your application needs to interact with resources like ConfigMaps, Secrets, or Pods.

- **Disabling Automounting:** Disable the automatic mounting of the Service Account token when your Pod doesn’t need to interact with the Kubernetes API, enhancing security.

## **Managing Service Accounts at Scale**

1. **Custom Service Accounts:**

   - Instead of using the default Service Account, create custom Service Accounts for different applications or components to better control their permissions.
   - Example:
     ```yaml
     apiVersion: v1
     kind: ServiceAccount
     metadata:
       name: my-service-account
       namespace: my-namespace
     ```
   - Specify the custom Service Account in your Pod definition:
     ```yaml
     apiVersion: v1
     kind: Pod
     metadata:
       name: my-pod
     spec:
       serviceAccountName: my-service-account
       ...
     ```

2. **Namespace Segmentation:**

   - Use different namespaces to segment your workloads, and create namespace-specific Service Accounts. This adds another layer of security and simplifies management.

3. **Limit Permissions with RBAC:**

   - Assign minimal RBAC permissions to each Service Account using Roles or ClusterRoles to adhere to the principle of least privilege.
   - Example:
     ```yaml
     apiVersion: rbac.authorization.k8s.io/v1
     kind: Role
     metadata:
       namespace: my-namespace
       name: pod-reader
     rules:
       - apiGroups: [""]
         resources: ["pods"]
         verbs: ["get", "list"]
     ```

4. **Use Service Accounts for External Integrations:**
   - When integrating external systems or services with your Kubernetes cluster, create specific Service Accounts with the necessary permissions to interact with the cluster securely.

## **Security Best Practices**

1. **Rotate Tokens Regularly:**

   - Implement policies to rotate Service Account tokens periodically to reduce the risk of compromised credentials.

2. **Monitor Service Account Usage:**

   - Monitor the usage of Service Accounts and their associated tokens. Alert on any suspicious activity, such as unauthorized API calls.

3. **Limit Service Account Scope:**

   - Avoid granting wide-ranging permissions to Service Accounts. If possible, use multiple Service Accounts with different permissions for different tasks or components.

4. **Disable Token Automounting:**
   - By default, Kubernetes mounts the Service Account token into Pods. If a Pod does not need to interact with the Kubernetes API, disable token automounting to reduce attack surface.
   - Example:
     ```yaml
     apiVersion: v1
     kind: Pod
     metadata:
       name: my-pod
     spec:
       automountServiceAccountToken: false
       ...
     ```

These practices help in managing Service Accounts effectively while ensuring that the Kubernetes environment remains secure and compliant with industry standards.
