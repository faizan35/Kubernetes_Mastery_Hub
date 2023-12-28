# Imp Questins

---

## Kubernetes Garbage Collection

### What is Garbage Collection in Kubernetes?

- Its like an automatic cleanup crew.
- When you create, update, or delete things like pods or containers, garbage collection ensures that any leftovers or unused items are automatically identified and removed.

### Why Do We Need It?

- We need it to keep Kubernetes environment clean and efficient by preventing unnecessary stuf and freeing up resources.

### How Does it Work?

When you delete something (let's say a pod), it doesn't vanish instantly. It goes into a "Terminating" phase. Garbage collection then kicks in, cleans up the leftover bits (containers), and ensures everything is properly removed.

### What About Orphaned Pods?

If the thing that created a pod (resources) is gone (like a parent), and the pod is left alone (orphaned), garbage collection takes care of it. It's like making sure no one is left behind.

### The Process in Simple Steps:

- You say, "I don't need this pod anymore" (mark it for deletion).
- The pod goes into a "Terminating" phase (like packing up stuff).
- The containers within the Pod are killed.
- The **kubelet** performs garbage collection, deleting the dead containers.
- It does another round, cleaning up the terminated pods.
- If an image is lonely and not used by any pod, it gets removed during the next cleanup.

### Customizing Cleanup:

- You can tell Kubernetes how often to clean up and what to focus on.
- It's like setting a schedule for someone to come and clean your room regularly.

---

### How external services connect to the cluster?

External services connect to a cluster through methods like load balancers, service discovery, Ingress controllers (in Kubernetes), NodePort, assigning external IPs, VPNs, direct connections, and API gateways. The choice depends on factors like security and scalability.

---
