# Advanced Topics

## Volume Expansion: Resize PVs and PVCs

### Expanding Persistent Volumes (PVs):

- **Steps:**

  1.  Identify the PV to be resized.
  2.  Update the capacity field in the PV definition.
  3.  Trigger a rolling update of pods using the PV to apply the changes.

- **Example PV Expansion:**

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv-example
spec:
  capacity:
    storage: 10Gi   # Updated capacity
  ...
```

### Expanding Persistent Volume Claims (PVCs):

- PVCs can be resized to claim more storage from the PV.

- **Steps:**

  1.  Identify the PVC to be resized.
  2.  Update the capacity field in the PVC definition.
  3.  Trigger a rolling update of pods using the PVC to apply the changes.

- **Example PVC Expansion:**

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
      storage: 10Gi # Updated storage request
```

### **Handling Volume Expansion for Dynamic Storage Needs:**

- **Dynamic Provisioning:**

  - If using dynamic provisioning with Storage Classes, resizing PVs and PVCs is more straightforward.
  - The storage class can dynamically adjust the size of provisioned volumes based on changes to PVCs.

- **Automated Volume Expansion:**

  - Some storage classes and systems support automated volume expansion without manual intervention.
  - Check the documentation for the specific storage provider for details.

## Snapshot and Restore

### Volume Snapshots

#### What is Snapshort.?

- A snapshot is a **point-in-time copy of the data** in a storage volume or file system.
- This copy captures the **state of the data** at the specific moment the snapshot is created.
- It captures how everything looks at that exact moment.
- Example:- in Windows OS its like creating a "Restore Point".

#### Kubernetes Snapshot API:

- Kubernetes provides a Snapshot API for managing volume snapshots.

**Using Volume Snapshots for Data Backup and Recovery:**

- **Creating a Volume Snapshot:**

  - Identify the PV and PVC to snapshot.
  - Use the Kubernetes API to create a snapshot.

- **Example Snapshot Creation:**

```yaml
apiVersion: snapshot.storage.k8s.io/v1
kind: VolumeSnapshot
metadata:
  name: my-snapshot
spec:
  source:
    name: myclaim # PVC name
    kind: PersistentVolumeClaim
```

- This creates the snapshot.

### Restoring from a Snapshot:

- Use the snapshot to restore data to a new PVC.

- **Example Snapshot Restore:**

```yaml
kind: PersistentVolumeClaim
apiVersion: v1
metadata:
  name: restored-claim
spec:
  accessModes:
    - ReadWriteOnce
  storageClassName: standard
  dataSource:
    name: my-snapshot
    kind: VolumeSnapshot
    apiGroup: snapshot.storage.k8s.io
```

Volume snapshots provide a powerful mechanism for backup and recovery in Kubernetes. They enable administrators and developers to create reliable copies of data, facilitating disaster recovery and other data management scenarios.

---
