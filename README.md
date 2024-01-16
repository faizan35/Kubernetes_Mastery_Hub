# KubernetesMasteryHub

## < --- In Progress --- >

### 0. Prerequisites

- [0.0 Topics](./Module-0/0.0-Topics.md)

### 1. Introduction to Kubernetes

**Theory**

- [1.1 What is Kubernetes?](./Module-1/1.1-What-is-Kubernetes.md)
- [1.2 Kubernetes Architecture](./Module-1/1.2-kubernetes-architecture.md)
- [1.3 Kubernetes Workflow](./Module-1/1.3-Kubernetes-Workflow.md)
- [1.4 Kubernetes Object](./Module-1/1.4-Kubernetes-Object.md)
- [1.5 Basics YAML Syntax.md](./Module-1/1.5-Basics-YAML-Syntax.md)

**Practical**

- [P.1 Setting up a K8s Cluster (local)](./Module-1/P.1-Kubernetes-Installation-using-Minikube.md)
- [P.2 Setting up a K8s Cluster (kubeadm)](./Module-1/P.2-Kubernetes-Installation-using-kubeadm.md)

### 2. Pods

**Theory**

- [2.1 Kubernetes Pods](./Module-2/2.1-Kubernetes-Pod.md)
- [2.2 Learn to write Manifests](./Module-2/2.2-write-Manifests.md)
- [2.3 Steps to run ANY Manifest file](./Module-2/2.3-steps-to-Run-Manifests.md)
- [2.4 Pod Topics for FUTURE](./Module-2/2.4-Pod-FUTURE.md)

**Annotations and Labels:**

- **Theory:**

  - Understand the importance of annotations and labels for organizing and managing resources.

- **Project: Resource Organization**
  - Description: Apply labels and annotations to various objects in your cluster for organizational purposes and observe their impact.

**Practical**

- [P.1 Simple Nginx Pod](./Module-2/P.1-Simple-Nginx-Pod.md)
- [P.2 Multi-Container Pod](./Module-2/P.2-Multi-container-pods.md)

### 3. Scaling of Pods

#### 3.1 ReplicaSets

**Theory**

- [3.1.1 What's & Why's of ReplicaSets](./Module-3/3.1.1-what-why-ReplicaSets.md)
- [3.1.2 Key Components of ReplicaSets](./Module-3/3.1.2-Key-Components-ReplicaSets.md)
- [3.1.3 Creating ReplicaSet Manifest](./Module-3/3.1.3-Creating-ReplicaSet.md)

#### 3.2 Horizontal Pod Autoscaling (HPA)

- [3.2.1 Everything about HPA](./Module-3/3.2.1-what-is-HPA.md)

#### 3.3 Future Topics realted to Scalling

- [3.3 Future Topics](./Module-3/3.3-Future-Topics.md)

### 4. Deployments

**Theory:**

- [4.1 What's & Why's of Deployments](./Module-4/4.1-what-why-Deployments.md)
- [4.2 Rolling Updates and Rollbacks in Deployments](./Module-4/4.2-Rolling-Up-Rollbacks.md)
- [4.3 Health Checks with Probes](./Module-4/4.3-Health-Checks-Probes.md)
- [4.4 Advanced Strategies & Use Cases](./Module-4/4.4-Adv-Deployment-Strat.md)

**Practical**

- [P.4.1 Scaling with ReplicaSets](./Module-4/P.4.1-Scaling-ReplicaSets.md)
- [P.4.2 Rolling Updates and Rollbacks](./Module-4/P.4.2-Rolling-Updates-Rollbacks.md)

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

### 9. StatefulSets

**Theory:**

- [9.1 What's and Why's StatefulSets](./Module-9/9.1-What-StatefulSets.md)
- [9.2 Stable Network Identifiers](./Module-9/9.2-Stable-Network-Identifiers.md)
- [9.3 Role of Persistent Storage in StatefulSets](./Module-9/9.3-Persistent-Storage-StatefulSets.md)
- [9.4 Creating StatefulSets](./Module-9/9.4-Creating-StatefulSets.md)
- [9.5 Headless Services](./Module-9/9.5-Headless-Services.md)

**Practical**

- [P.9.0 Project Topics](./Module-9/P.9.0-Project-Topics.md)

### 10. DaemonSets

**Theory:**

- [10.1 What's and Why's DaemonSets](./Module-10/10.1-What-DaemonSets.md)
- [10.2 Creating DaemonSet](./Module-10/10.2-creating-DaemonSets.md)

- **Project: System Daemons Deployment**
  - Description: Deploy a DaemonSet to ensure that a specific Pod runs on every node in the cluster.

### 11. **Jobs and CronJobs:**

**Theory:**

- [11.1 Introduction to Jobs](./Module-11/11.1-Introduction-Jobs.md)

  - Learn about Jobs for running one-off tasks and CronJobs for scheduled tasks.

**Practical**

- [P.11.1 Practical Exercises - Jobs](./Module-11/P.11.1-Practical-Jobs.md)

### 119. **Custom Resource Definitions (CRDs):**

- **Theory:**

  - Understand how to extend Kubernetes API using Custom Resource Definitions to define custom resources and controllers.

- **Project: Custom Resource and Controller**
  - Description: Define a custom resource using CRDs and implement a controller to manage the lifecycle of the custom resource.

### 120. **Monitoring and Logging:**

- **Theory:**

  - Learn how to set up monitoring and logging for your Kubernetes cluster, exploring tools like Prometheus and Grafana.

- **Project: Monitoring Setup with Prometheus and Grafana**
  - Description: Set up Prometheus for monitoring and Grafana for visualization. Create dashboards to monitor key metrics of your applications.

### 121. **Network Policies:**

- **Theory:**

  - Explore Network Policies to control the communication between Pods in a cluster.

- **Project: Network Segmentation**
  - Description: Implement Network Policies to control the flow of traffic between Pods in different Namespaces, ensuring a secure network environment.

---

## Tools

### 117. **Helm Charts:**

- **Theory:**

  - Introduce Helm, a package manager for Kubernetes, and understand how to use Helm charts to define, install, and upgrade even the most complex Kubernetes applications.

- **Project: Helm Chart for Application**
  - Description: Package your application using Helm charts. Include configurations, dependencies, and versioning in the Helm chart.

### 118. **Kustomize:**

- **Theory:**

  - Explore Kustomize, a built-in customization mechanism in Kubernetes, for creating and managing manifests more efficiently.

- **Project: Custom Manifests with Kustomize**
  - Description: Use Kustomize to customize Kubernetes manifests for different environments without modifying the original files.

---

## Extra

### 12. **Resource Quotas and LimitRange:**

- **Theory:**

  - Explore resource management in Kubernetes using Resource Quotas and LimitRange.

- **Project: Resource Management**
  - Description: Set up Resource Quotas to limit resource usage in a Namespace. Experiment with LimitRange to restrict container resource limits.

### 116. **RBAC (Role-Based Access Control):**

- **Theory:**

  - Learn about RBAC to control access to resources within a cluster.

- **Project: User Access Management**
  - Description: Implement RBAC to control user access to resources within a Namespace. Create roles and role bindings accordingly.

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

### 1. Introduction to Kubernetes

### 2. Pods

### 3. Scalling of Pods

### 4. Deployments

### 5. Services

### 6. ConfigMaps and Secrets

### 7. Namespaces

### 8. Persistent Volumes and Persistent Volume Claims

### 9. StatefulSets

### 10. DaemonSets

### 11. **Jobs and CronJobs:**

### 12. **Resource Quotas and LimitRange:**

### 13. **Annotations and Labels:**

### 116. **RBAC (Role-Based Access Control):**

### 117. **Helm Charts:**

### 118. **Kustomize:**

### 119. **Custom Resource Definitions (CRDs):**

### 120. **Monitoring and Logging:**

### 121. **Network Policies:**

---
