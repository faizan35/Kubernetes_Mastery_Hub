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

- **Theory:**

  - Discover how to define persistent storage in Kubernetes.
  - Learn about Persistent Volumes (PVs) and Persistent Volume Claims (PVCs).

- **Project: Persistent Storage for Database**
  - Description: Deploy a database with persistent storage using Persistent Volumes and Persistent Volume Claims.

**extra**

- **Project: Multi-Container Pod**
  - Description: Design a Pod that contains multiple containers that need to work together, demonstrating inter-container communication.

### 9. StatefulSets

- **Theory:**

  - Explore StatefulSets for stateful applications that require stable network identities and persistent storage.

- **Project: Stateful Application Deployment**
  - Description: Deploy a stateful application using StatefulSets, ensuring stable network identities and persistent storage.

### 10. DaemonSets

- **Theory:**

  - Understand DaemonSets, which ensure that all Nodes run a copy of a Pod, useful for system daemons.

- **Project: System Daemons Deployment**
  - Description: Deploy a DaemonSet to ensure that a specific Pod runs on every node in the cluster.

### 11. **Jobs and CronJobs:**

    - **Theory:**

      - Learn about Jobs for running one-off tasks and CronJobs for scheduled tasks.

    - **Project: Scheduled Tasks**
      - Description: Create a Job to perform a one-off task and a CronJob to schedule tasks at specified intervals.

### 12. **Resource Quotas and LimitRange:**

    - **Theory:**

      - Explore resource management in Kubernetes using Resource Quotas and LimitRange.

    - **Project: Resource Management**
      - Description: Set up Resource Quotas to limit resource usage in a Namespace. Experiment with LimitRange to restrict container resource limits.

### 13. **Annotations and Labels:**

    - **Theory:**

      - Understand the importance of annotations and labels for organizing and managing resources.

    - **Project: Resource Organization**
      - Description: Apply labels and annotations to various objects in your cluster for organizational purposes and observe their impact.

### 116. **RBAC (Role-Based Access Control):**

    - **Theory:**

      - Learn about RBAC to control access to resources within a cluster.

    - **Project: User Access Management**
      - Description: Implement RBAC to control user access to resources within a Namespace. Create roles and role bindings accordingly.

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

# Kubernetes Book Outline

## 1. Introduction to Containerization and Orchestration

- Overview of container technology
- Need for orchestration
- Introduction to Kubernetes

## 2. Getting Started with Kubernetes

- Installing and setting up Kubernetes
- Basic concepts: pods, nodes, clusters
- Interacting with Kubernetes using `kubectl`

## 3. Deploying Applications on Kubernetes

- Creating and managing pods
- Deploying a simple application
- Scaling applications in Kubernetes

## 4. Service Discovery and Load Balancing

- Services in Kubernetes
- Internal and external service communication
- Load balancing strategies

## 5. Persistent Storage in Kubernetes

- Storage options in Kubernetes
- Persistent Volumes (PV) and Persistent Volume Claims (PVC)
- StatefulSets for stateful applications

## 6. Configuring and Managing Deployments

- Managing configurations with ConfigMaps and Secrets
- Rolling updates and rollbacks
- Canary deployments and blue-green deployments

## 7. Monitoring and Logging in Kubernetes

- Prometheus for monitoring
- Logging with Fluentd and Elasticsearch
- Debugging and troubleshooting in Kubernetes

## 8. Security in Kubernetes

- RBAC (Role-Based Access Control)
- Network policies
- Securing container images

## 9. Custom Resources and Operators

- Understanding CustomResourceDefinitions (CRDs)
- Building and deploying custom controllers
- Extending Kubernetes with custom resources

## 10. Advanced Topics

- Helm for package management
- Kubernetes Federation for multi-cluster management
- Integrating with CI/CD pipelines

## 11. Best Practices and Tips

- Design principles for scalable applications
- Efficiency and resource management
- Upgrading Kubernetes and managing dependencies

## 12. Future Trends in Kubernetes

- Emerging technologies and extensions
- Kubernetes in edge computing
- Community and ecosystem developments
