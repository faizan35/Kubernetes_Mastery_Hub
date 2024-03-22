# Persistent Volumes and Persistent Volume Claims

## Persistent Volumes (PVs)

#### What is Persistent Volumes?

- It is a storage unit, that exists beyond the lifecycle of Pods.
- cluster administrator is who decides how much space is available and what rules to apply to this storage.

#### How does it work?

- You have this storage space (PV) ready, and when your pod needs a place to store things permanently, it asks for a Persistent Volume Claim or PVC.
- The storage manager then assigns a locker (PV) to your program's request.

#### Characteristics of PVs:

- PVs have a unique identifier (UID) and a set of properties defining capacity, access modes, and more.
- PVs can be in one of the following phases: Available, Bound, Released, or Failed.

## Persistent Volume Claims (PVCs)

- A Persistent Volume Claim (PVC) is a **request for storage** by a user or a pod in Kubernetes.
- Think PVC as a "ticket", to get PV.

## Storage Classes

- Its like blueprints that specify the properties or specifications of the storage you want.

**Example:** A Storage Class might define storage on AWS EBS with certain performance characteristics.

---

### Manually Creating/Provisioned PVs:

- A typical PV definition includes specifications for capacity, access modes, host paths, and other attributes.

- **Example YAML:**

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv-example
spec:
  capacity:
    storage: 5Gi
  volumeMode: Filesystem
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: "/mnt/data"
```

- **Explanation:**

  - This example creates a PV named "pv-example" with a capacity of 5 gigabytes, ReadWriteOnce access mode, and a host path "/mnt/data."

#### Automatically Creating/Provisioned PVs Using Storage Classes:

Step 1: Write **Storage Class**

: With details such as the provisioner and any specific settings or features.

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: standard
provisioner: kubernetes.io/aws-ebs
```

Step 2: **Write PVC** and Link to Storage Class

: Create a PersistentVolumeClaim (PVC), specify the `storageClassName` field and link it to the StorageClass you defined.
: This tells Kubernetes to take rules or specs in storage class and create a PV.

```yaml
kind: PersistentVolumeClaim
apiVersion: v1
metadata:
  name: myclaim
spec:
  accessModes:
    - ReadWriteOnce
  storageClassName: standard
  resources:
    requests:
      storage: 5Gi
```

---
