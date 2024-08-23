# Kubernetes Pods

## **1. Introduction to Pods**

### [1.1 What is a Pod?](./01-Intro-to-Pods/1.1-what-is-pod.md)

- Definition and purpose of Pods
- Difference between Pods and containers
- Single vs. Multi-container Pods

### [1.2 Pod Lifecycle](./01-Intro-to-Pods/1.2-Pod-Lifecycle.md)

- Phases of a Pod (Pending, Running, Succeeded, Failed, etc.)
- Pod termination and cleanup
- Pod states and status fields

### [1.3 Creating and Managing Pods](./01-Intro-to-Pods/1.3-Creating-Managing-Pods.md)

- Basic `kubectl` commands to create, view, and manage Pods
- YAML configuration for Pods
- Labels, selectors, and annotations

## **2. Pod Networking**

### **2.1 Pod-to-Pod Communication**

- Understanding how Pods communicate within a cluster
- ClusterIP and networking models in Kubernetes
- DNS for Pods

### **2.2 Service Discovery**

- How Pods are discovered and exposed
- Role of Services in Pod communication

### **2.3 Networking Policies**

- Network isolation between Pods
- Creating and applying Network Policies

---

#### **3. Pod Storage**

- **3.1 Volumes in Pods**

  - Types of Volumes (emptyDir, hostPath, persistentVolume, etc.)
  - Mounting Volumes in Pods

- **3.2 Persistent Volumes (PVs) and Persistent Volume Claims (PVCs)**
  - Binding PVs to PVCs
  - Dynamic provisioning of storage

#### **4. Pod Configuration**

- **4.1 Environment Variables**

  - Setting environment variables in Pods
  - Configuring Secrets and ConfigMaps

- **4.2 ConfigMaps**

  - Creating and managing ConfigMaps
  - Injecting ConfigMaps into Pods

- **4.3 Secrets**
  - Creating and managing Secrets
  - Injecting Secrets into Pods securely

#### **5. Pod Scheduling**

- **5.1 Pod Affinity and Anti-affinity**

  - Scheduling Pods based on affinity rules
  - Soft and hard affinity/anti-affinity

- **5.2 Node Selectors and Taints**

  - Assigning Pods to specific nodes
  - Taints and tolerations for advanced scheduling

- **5.3 Resource Requests and Limits**
  - Setting CPU and memory requests/limits for Pods
  - Handling resource overcommitment and QoS (Quality of Service) classes

#### **6. Pod Monitoring and Logging**

- **6.1 Monitoring Pod Health**

  - Readiness and Liveness Probes
  - Pod health checks

- **6.2 Pod Logging**
  - Accessing and managing logs from Pods
  - Sidecar containers for logging

#### **7. Pod Scaling and Autoscaling**

- **7.1 Manual Scaling**

  - Scaling Pods manually using `kubectl`
  - Replication Controllers and ReplicaSets

- **7.2 Horizontal Pod Autoscaler (HPA)**
  - Setting up HPA for automatic scaling
  - Metrics used for scaling (CPU, memory, custom metrics)

#### **8. Advanced Pod Patterns**

- **8.1 Init Containers**

  - Role and use cases of Init Containers
  - Configuring Init Containers in Pods

- **8.2 Sidecar Containers**

  - Understanding Sidecar pattern
  - Implementing Sidecars for logging, monitoring, and proxies

- **8.3 Ephemeral Containers**
  - Debugging with Ephemeral Containers
  - Use cases and configuration

#### **9. Pod Security**

- **9.1 Security Contexts**

  - Configuring security contexts for Pods and containers
  - Setting user permissions and capabilities

- **9.2 Pod Security Policies**

  - Implementing Pod Security Policies (PSPs)
  - Restricting Pod creation based on security contexts

- **9.3 Securing Pod Communication**
  - TLS encryption between Pods
  - Role-based access control (RBAC) for Pods

#### **10. Troubleshooting Pods**

- **10.1 Common Issues**

  - Troubleshooting Pod startup failures
  - Dealing with OOM (Out of Memory) and CPU throttling

- **10.2 Debugging Techniques**

  - Using `kubectl describe` and `kubectl logs` for debugging
  - Attaching to Pods and inspecting containers

- **10.3 CrashLoopBackOff and Pending Pods**
  - Diagnosing and resolving CrashLoopBackOff issues
  - Analyzing Pending Pods and resolving scheduling issues

---
