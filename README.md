# Kubernetes Mastery Hub

## < --- In Progress --- >

### 0. Pre Kubernetes

- [0.1 Distributed system & CAP Theorem](./Module-0/0.1-Distributed-system.md)
- [0.2 Authentication & Authorization](./Module-0/0.2-Authentication-Authorization.md)
- [0.3 Key Value Store](./Module-0/0.3-Key-Value-Store.md)
- [0.4 API - RESTful APIs and gRPC APIs](./Module-0/0.4-API.md)
- [0.5 Basics YAML Syntax](./Module-0/0.5-Basics-YAML-Syntax.md)
- [0.6 Container - Docker, Podman, OCI, CRI](./Module-0/0.6-Container.md)
- [0.7 Service Discovery - client-side & server-side](./Module-0/0.7-Service-Discovery.md)
- [0.8 Networking Basis](./Module-0/0.8-Networking-Basis.md)

### 1. Introduction to Kubernetes

- [1.1 What is Kubernetes?](./Module-1/1.1-What-is-Kubernetes.md)
- [1.2 Kubernetes Architecture](./Module-1/1.2-kubernetes-architecture.md)
- [1.3 Kubernetes Workflow](./Module-1/1.3-Kubernetes-Workflow.md)
- [1.4 Kubeconfig File](./Module-1/1.4-Kubeconfig-File.md)
- [1.5 Kubernetes Object](./Module-1/1.5-Kubernetes-Object.md)
- [1.6 Steps to run ANY Manifest file](./Module-1/1.6-steps-to-Run-Manifests.md)

- [P.1 Setting up a K8s Cluster (local)](./Module-1/P.1-Kubernetes-Installation-using-Minikube.md)
- [P.2 Setting up a K8s Cluster (kubeadm)](./Module-1/P.2-Kubernetes-Installation-using-kubeadm.md)

### 2. Workloads Objects

#### 2.1. Pods

- [1. Pods](./Module-2/01-Pods/01-Pod.md)

- [P.1 Simple Nginx Pod](./Module-2/01-Pods/P.1-Simple-Nginx-Pod.md)
- [P.2 Multi-Container Pod](./Module-2/01-Pods/P.2-Multi-container-pods.md)

#### 2.2. ReplicaSets

- [1. ReplicaSets](./Module-2/02-ReplicaSets/01-ReplicaSets.md)
- [2. Interview Questions](./Module-2/02-ReplicaSets/02-Interview-Questions.md)

#### 2.3. Deployment

- [1. What's & Why's of Deployments](./Module-2/03-Deployment/01-what-why-Deployments.md)
- [2. Rolling Updates and Rollbacks in Deployments](./Module-2/03-Deployment/02-Rolling-Up-Rollbacks.md)
- [3. Health Checks with Probes](./Module-2/03-Deployment/03-Health-Checks-Probes.md)
- [4. Advanced Strategies & Use Cases](./Module-2/03-Deployment/04-Adv-Deployment-Strat.md)

- [P.4.1 Scaling with ReplicaSets](./Module-2/03-Deployment/P.1-Scaling-ReplicaSets.md)
- [P.4.2 Rolling Updates and Rollbacks](./Module-2/03-Deployment/P.2-Rolling-Updates-Rollbacks.md)

#### 2.4. StatefulSets

- [1. What's and Why's StatefulSets](./Module-2/04-StatefulSets/9.1-What-StatefulSets.md)
- [2. Stable Network Identifiers](./Module-2/04-StatefulSets/9.2-Stable-Network-Identifiers.md)
- [3. Role of Persistent Storage in StatefulSets](./Module-2/04-StatefulSets/9.3-Persistent-Storage-StatefulSets.md)
- [4. Creating StatefulSets](./Module-2/04-StatefulSets/9.4-Creating-StatefulSets.md)
- [5. Headless Services](./Module-2/04-StatefulSets/9.5-Headless-Services.md)
- [6. Interview Questions](./Module-2/04-StatefulSets/9.6-Interview-Questions.md)

- [P.0 Project Topics](./Module-2/04-StatefulSets/P.9.0-Project-Topics.md)

### 2.5. DaemonSets

- [1. What's and Why's DaemonSets](./Module-2/05-DaemonSets/10.1-What-DaemonSets.md)
- [2. Creating DaemonSet](./Module-2/05-DaemonSets/10.2-creating-DaemonSets.md)
- [3. Node Affinity and Anti-Affinity](./Module-2/05-DaemonSets/10.3-Node-Affinity-Anti-Affinity.md)
- [4. Interview Questions](./Module-2/05-DaemonSets/10.4-Interview-Questions.md)

### 2.6. **Jobs**

- [1. Introduction to Jobs](./Module-2/06-Jobs/11.1-Introduction-Jobs.md)

### 2.7. **CronJobs**

- [1. Introduction to Cronjobs](./Module-2/07CronJobs/11.2-Introduction-Cronjobs.md)

---

### Configuration Objects

### Network Objects

### Storage Objects

### Access Control Objects

---

### 3. Scaling of Pods

#### 3.1 ReplicaSets

#### 3.2 Horizontal Pod Autoscaling (HPA)

- [3.2.1 Everything about HPA](./Module-3/3.2.1-what-is-HPA.md)

#### 3.3 Future Topics realted to Scalling

- [3.3 Future Topics](./Module-3/3.3-Future-Topics.md)

### 5. Services

**Theory:**

- [5.1 What's & Why's of Services](./Module-5/5.1-what-why-Services.md)
- [5.2 Types of Kubernetes Services](./Module-5/5.2-Types-of-Services.md)
- [5.3 DNS in Kubernetes and Service Discovery](./Module-5/5.3-DNS-svc-discovery.md)
- [5.4 "NetworkPolicies" & Security with "Ingress"](./Module-5/5.4-NetworkPolicies-Ingress.md)
- [5.5 Future Topics](./Module-5/5.5-Future-Topics.md)

**Practical**

- [P.5.0 Project Topics](./Module-5/P.5.0-Project-Topics.md)
- [P.5.1 cc](./Module-5/P.5.1-cc.md)

### 6. ConfigMaps and Secrets

**Theory:**

- [6.1 Intro](./Module-6/6.1-intro.md)
- [6.2 Creating ConfigMaps](./Module-6/6.2-ConfigMaps.md)
- [6.3 Creating Secrets](./Module-6/6.3-Secrets.md)

**Practical**

- [P.6.0 Project Topics](./Module-6/P.6.0-Project-Topics.md)

### 7. Namespaces

**Theory:**

- [7.1 Overview of Namespaces](./Module-7/7.1-Overview-Namespaces.md)
- [7.2 Creating Namespaces](./Module-7/7.2-Creating-Namespaces.md)

**Practical**

- [P.7.0 Project Topics](./Module-7/P.7.0-Project-Topics.md)

### 8. Persistent Volumes and Persistent Volume Claims

**Theory:**

- [8.1 Volumes in Kubernetes](./Module-8/8.1-Storage-Kubernetes.md)
- [8.2 PVs, PVCs and Storage Classes](./Module-8/8.2-PVs-PVCs.md)
- [8.3 Advanced Topics](./Module-8/8.3-Advanced-Topics.md)

**Practical**

- [P.8.0 Project Topics](./Module-8/P.8.0-Project-Topics.md)

### 12. **Custom Resource Definitions (CRDs):**

**Theory:**

- [12.1 Introduction to CRDs](./Module-12/12.1-Introduction-CRDs.md)

  - Understand how to extend Kubernetes API using Custom Resource Definitions to define custom resources and controllers.

- **Project: Custom Resource and Controller**
  - Description: Define a custom resource using CRDs and implement a controller to manage the lifecycle of the custom resource.

### 13. **Resource Quotas and LimitRange:**

- **Theory:**

  - Explore resource management in Kubernetes using Resource Quotas and LimitRange.

- **Project: Resource Management**
  - Description: Set up Resource Quotas to limit resource usage in a Namespace. Experiment with LimitRange to restrict container resource limits.

### 14. **RBAC (Role-Based Access Control):**

- **Theory:**

  - Learn about RBAC to control access to resources within a cluster.

- **Project: User Access Management**
  - Description: Implement RBAC to control user access to resources within a Namespace. Create roles and role bindings accordingly.

---

## Tools

- [List of all most used tools](./Everything-about-Tools.md)

### T1. **Helm Charts:**

**Theory:**

- [T1.0 Helm Syllabus](./Module-T1/T1.0-Helm-Syllabus.md)
- [T1.1 Introduction to Helm](./Module-T1/T1.1-Introduction-Helm.md)
- [T1.2 Installation and Setup](./Module-T1/T1.2-Helm-Installation-Setup.md)
- [T1.3 Commands & Structure](./Module-T1/T1.3-Helm-Basics.md)
- [T1.4 Chart Repositories](./Module-T1/T1.4-Chart-Repositories.md)

- **Project: Helm Chart for Application**
  - Description: Package your application using Helm charts. Include configurations, dependencies, and versioning in the Helm chart.

### T2. **Kustomize:**

- **Theory:**

  - Explore Kustomize, a built-in customization mechanism in Kubernetes, for creating and managing manifests more efficiently.

- **Project: Custom Manifests with Kustomize**
  - Description: Use Kustomize to customize Kubernetes manifests for different environments without modifying the original files.

---

## Contribution

We welcome contributions from the community! If you'd like to contribute, follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Make your changes and submit a pull request.
4. Provide a detailed description of your changes.

## Guidelines for Contributors

- Follow the existing coding style and structure.
- Test your changes thoroughly before submitting a pull request.
- Ensure that your contribution adds value to the guide.

## Code of Conduct

Please adhere to our [Code of Conduct](CODE_OF_CONDUCT.md) to ensure a positive and inclusive environment for all contributors.

## License

This project is licensed under the [MIT License](LICENSE).

Happy learning!

---
