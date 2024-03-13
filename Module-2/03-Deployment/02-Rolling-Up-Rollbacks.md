# Rolling Updates and Rollbacks

## Rolling Updates in Deployments

- Rolling Updates in Deployments is a strategy for updating your application without causing downtime.
- It allows you to gradually replace old instances of your application with new ones.

#### What User dose to update?

1. Update the Deployment YAML, to change the container image or any other specifications.

2. Apply the Update, Use `kubectl apply -f filename.yaml` to apply the changes.
3. **Done**, monitor the updates `kubectl get deployment`.

Observe **AVAILABLE** column gradually increase as the new pods are created, and the old ones are terminated.

#### What k8s dose to update?

1. Kubernetes creats a new `ReplicaSet` with the updated pod template while gradually scaling down the old ReplicaSet.

---

## Rollbacks in Deployments

#### If update dosent works

- Lets say, your update doesn't go as planned.
- Rollbacks allows you to revert to a previous working version.

#### Steps to perform a rollback

###### **1.** View Deployment History to identify the desired revision you want to rollback to:

```bash
kubectl rollout history deployment my-deployment
```

###### **2.** Rollback to a Specific Revision, Eg:- roll back to revision 2

```bash
kubectl rollout undo deployment my-deployment --to-revision=2
```

###### **3.** Monitor Rollback:

```bash
kubectl rollout status deployment my-deployment
```

###### **4.** Confirm Rollback:

```bash
kubectl get deployment
```

---
