# Deployments

**Official k8s Docs:** https://kubernetes.io/docs/concepts/workloads/controllers/deployment/

### 1. What is a Deployment?

- <h4 style="display: inline;">Deployments</h4> is a declarative way to <h5 style="display: inline;">automate and manage the containerized applications</h5> to maintain a specified desired state, through ReplicaSet.

- Its <u>**abstraction layer above ReplicaSets**</u>, providing declarative updates, rolling updates, and rollbacks.

abstraction layer above ReplicaSets
: You just describing/write the desired state, and Kubernetes takes care of achieving and maintaining that state.

---

### 2. Benefits of Deployments:

- **Declarative Updates**: You describe the desired state, and K8s ensures that the current state matches that desired state.

- **Self-healing:** Deployments automatically replace failed pods and maintain the desired state.

- **Rolling Updates:** Easily update your application without downtime using rolling updates.

- **Rollbacks:** If an update goes wrong, roll back to the previous version.

### 3. How Deployments Work.?

##### This deployment manifest file looks same as repplicaSet, so why do we need it?

```yaml
apiVersion: apps/v1
kind: Deployment # ONLY CHANAGE = kind: ReplicaSet
metadata:
  name: my-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: web
  template:
    metadata:
      labels:
        app: web
    spec:
      containers:
        - name: my-container
          image: nginx:latest
          ports:
            - containerPort: 80
```

- When you create a **Deployment**, Kubernetes creates a **ReplicaSet**, which in turn manages the Pods.

- The **Deployment controller** continually **monitors** the state of the ReplicaSet, to match the desired state specified in the Deployment manifest.

#### 3.2 What ReplicaSet do..?

: - ReplicaSet keep a specific number of replicas running at all times.
: - If one crashes, it quickly replaces it to maintain the desired number.

#### 3.3 Deployments (boss):

: - is like a boss that watches over these replicas.
: - It make's sure these replicas are doing exactly what you want, even when you're making changes.

### 4. Creating a Deployments

- All same just chagne, `kind: ReplicaSet`.

- Once you apply the YAML manifest, K8s creates the necessary resources (ReplicaSet, Pods) to match the desired state.

##### Apply the Deployment:

```bash
kubectl apply -f deployment.yaml
```

##### Check the Deployment:

```bash
kubectl get deployment
```

##### Observe ReplicaSets:

```bash
kubectl get replicaset
```

### 5. Updating a Deployment - Rolling Update:

- To update a Deployment, you modify the YAML manifest file and apply the changes using `kubectl apply`.

- Kubernetes will perform a **rolling update**.

- **Rolling Update**: K8s creates the new Pods and gradually replaces the old pods, ensuring zero downtime during the update process.

### 6. Rollback - Handle error in Rolling Update:

- If an update causes issues, you can perform a rollback to revert to the previous stable version.

- Kubernetes retains the history of Deployment revisions, allowing you to rollback to a specific revision using `kubectl rollout undo`.

### 7. Scaling a Deployments

- You can scale a Deployment horizontally by adjusting the number of replicas in the Deployment manifest.
- Kubernetes will automatically adjust the number of Pods to match the desired number of replicas.

### 8. Health Checks and Liveness Probes:

- Deployments can be configured with health checks and liveness probes to ensure the application's health.

- Health checks determine if a pod is ready to serve traffic, while liveness probes determine if a pod is alive and healthy.

### 9. Cleaning Up:

- Deleting a Deployment removes all the resources it manages (ReplicaSet, Pods, etc.).
- You can delete a Deployment using `kubectl delete deployment <deployment_name>`.

### 10. Best Practices:

- Use declarative configurations stored in version control.
- Utilize labels effectively to organize and manage Deployments.
- Regularly test your Deployment updates and rollback procedures.

---

## Interview Questions

Q) How does Kubernetes manage resource cleanup in Deployments? **OR** What policies or configurations can be set to manage old ReplicaSets and ensure resource efficiency?

A) By allowing configuration of the `revisionHistoryLimit` field to specify how many old ReplicaSets should be retained. This ensures efficient resource utilization and prevents cluttering of resources.

Q) Can you discuss any best practices or recommendations for optimizing Deployments in Kubernetes? How would you ensure the efficient management and operation of Deployments in a production environment?

A) Best practices for optimizing Deployments in Kubernetes include defining resource limits and requests, using **liveness** and **readiness** probes effectively, monitoring resource utilization, implementing health checks, and automating deployments with CI/CD pipelines. Additionally, ensuring proper configuration of scaling policies and cleanup strategies contributes to efficient management of Deployments in a production environment.

---
