# Deployments

- <h4 style="display: inline;">Deployments</h4> is a declarative way to <h5 style="display: inline;">automate and manage the containerized applications</h5> to maintain a specified desired state, through **ReplicaSet**.

- Its <u>**abstraction layer above ReplicaSets**</u>, providing declarative updates, rolling updates, and rollbacks.

Declarative and abstraction layer
: Describing the desired state, and Kubernetes takes care of achieving and maintaining that state.

---

### Benefits of Deployments:

**Self-healing:** Deployments automatically replace failed pods and maintain the desired state.

**Rolling Updates:** Easily update your application without downtime using rolling updates.

**Rollbacks:** If an update goes wrong, roll back to the previous version.

---

### Why need Deployments?

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

Understand What ReplicaSet do..?
: - ReplicaSet keep a specific number of replicas running at all times.
: - If one crashes, it quickly replaces it to maintain the desired number.

Deployments (boss):
: - is like a boss that watches over these replicas.
: - It make's sure these replicas are doing exactly what you want, even when you're making changes.

---

### Creating Deployments

- All same just chagne, `kind: ReplicaSet`.

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

---

### Scaling Deployments

One of the powerful features of Deployments in Kubernetes is the ability to scale the number of replicas (pods) up or down effortlessly.

##### Scaling Up:

- Use this command to increase the number of replicas:
  ```bash
  kubectl scale deployment my-deployment --replicas=5
  ```
- This command scales the Deployment named my-deployment to have 5 replicas.

##### Scaling Down:

- Similarly, you can scale down the Deployment:

  ```bash
  kubectl scale deployment my-deployment --replicas=3
  ```

- This scales the Deployment back to 3 replicas.

---
