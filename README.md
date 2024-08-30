# Kubernetes Mastery Hub

## < --- In Progress --- >

### 0. Pre Kubernetes

- [0.1 Distributed system & CAP Theorem](./00-Pre-Kubernetes/0.1-Distributed-system.md)
- [0.2 Authentication & Authorization](./00-Pre-Kubernetes/0.2-Authentication-Authorization.md)
- [0.3 Key Value Store](./00-Pre-Kubernetes/0.3-Key-Value-Store.md)
- [0.4 API - RESTful APIs and gRPC APIs](./00-Pre-Kubernetes/0.4-API.md)
- [0.5 Basics YAML Syntax](./00-Pre-Kubernetes/0.5-Basics-YAML-Syntax.md)
- [0.6 Container - Docker, Podman, OCI, CRI](./00-Pre-Kubernetes/0.6-Container.md)
- [0.7 Service Discovery - client-side & server-side](./00-Pre-Kubernetes/0.7-Service-Discovery.md)
- [0.8 Networking Basis](./00-Pre-Kubernetes/0.8-Networking-Basis.md)

### 1. Introduction to Kubernetes

- [1.1 What is Kubernetes?](./01-Introduction-to-k8s/1.1-What-is-Kubernetes.md)
- [1.2 Kubernetes Architecture](./01-Introduction-to-k8s/1.2-kubernetes-architecture.md)
- [1.3 Kubernetes Workflow](./01-Introduction-to-k8s/1.3-Kubernetes-Workflow.md)
- [1.4 `Kubeconfig` File](./01-Introduction-to-k8s/1.4-Kubeconfig-File.md)
- [1.5 Kubernetes Object](./01-Introduction-to-k8s/1.5-Kubernetes-Object.md)
- [1.6 Common `kubectl` commands](./01-Introduction-to-k8s/1.6-common-commands.md)
- [1.7 Namespaces](./01-Introduction-to-k8s/1.7-Namespaces.md)
- [1.8 Common types of Errors](./01-Introduction-to-k8s/1.8-Errors.md)
- [1.9 Annotations and Labels](./01-Introduction-to-k8s/1.9-Annotations-Labels.md)

- [P.1 Setting up a K8s Cluster (local)](./01-Introduction-to-k8s/P.1-Kubernetes-Installation-using-Minikube.md)
- [P.2 Setting up a K8s Cluster (kubeadm)](./01-Introduction-to-k8s/P.2-Kubernetes-Installation-using-kubeadm.md)

### 2. Pods

- [Everything about Pods](./02-Pods/Readme.md)

### 3. Kubernetes Networking

- [3.1. Kubernetes Networking Model](./03-Kubernetes-Networking/01-Kubernetes-Networking-Model.md)
- [3.2. CNI Plugins: Calico, Flannel, Weave, etc.](./03-Kubernetes-Networking/02-CNI-Plugins.md)
- [3.3. Service Discovery and CoreDNS](./03-Kubernetes-Networking/03-Service-Discovery-CoreDNS.md)
- [3.4. Network Policies and Security](./03-Kubernetes-Networking/04-Network-Policies-Security.md)

---

#### 3.1. Service

- [1. What's & Why's of Services](./Module-3/01-Service/1-Service.md)
- [2. Types of Kubernetes Services](./Module-3/01-Service/2-Types-of-Service.md)
- [3. DNS in Kubernetes and Service Discovery](./Module-3/01-Service/3-DNS-K8s-svc-Discovery.md)

- [4. Future Topics.md](./Module-3/01-Service/4-Future-Topics.md)

- [5.4 "NetworkPolicies" & Security with "Ingress"](./Module-3/01-Service/5.4-NetworkPolicies-Ingress.md)

---

### 4. Workloads Objects / Resource Management

#### [4.0. Generating k8s manifest files with `kubectl create` command](./04-Workloads-Resource/01-creating-manifest.md)

#### 4.1. Deployment

##### [4.1.1. Introduction to Deployments](./04-Workloads-Resource/01-Deployment/01-Introduction-Deployments.md)

- What's & Why's of Deployments
- Deployment YAML Structure
- Replicas: Set and manage replicas for high availability.

##### [4.1.2. Rolling Updates and Rollbacks](./04-Workloads-Resource/01-Deployment/02-Rolling-Up-Rollbacks.md)

- Rolling Update Strategy
- `MaxUnavailable` & `MaxSurge`
- Rollback
- Versioning: Version your Deployments for easier rollback and management.

##### [4.1.3. Advanced Deployment Strategies](./04-Workloads-Resource/01-Deployment/03-Adv-Deployment-Strat.md)

- Blue-Green Deployments
- Canary Deployments
- Other Strategies

##### [P.4.1 Scaling with ReplicaSets](./04-Workloads-Resource/01-Deployment/P.1-Scaling-ReplicaSets.md)

##### [P.4.2 Rolling Updates and Rollbacks](./04-Workloads-Resource/01-Deployment/P.2-Rolling-Updates-Rollbacks.md)

#### 4.2. StatefulSets

- [1. What's and Why's StatefulSets](./04-Workloads-Resource/02-StatefulSets/01-Introduction-StatefulSets.md)
- [2. Stable Network Identifiers](./04-Workloads-Resource/02-StatefulSets/9.2-Stable-Network-Identifiers.md)
- [3. Role of Persistent Storage in StatefulSets](./04-Workloads-Resource/02-StatefulSets/9.3-Persistent-Storage-StatefulSets.md)
- [4. Creating StatefulSets](./04-Workloads-Resource/02-StatefulSets/9.4-Creating-StatefulSets.md)
- [5. Headless Services](./04-Workloads-Resource/02-StatefulSets/9.5-Headless-Services.md)
- [6. Interview Questions](./04-Workloads-Resource/02-StatefulSets/9.6-Interview-Questions.md)

- [P.0 Project Topics](./04-Workloads-Resource/02-StatefulSets/P.9.0-Project-Topics.md)

#### 4.3. DaemonSets

- [1. What's and Why's DaemonSets](./04-Workloads-Resource/03-DaemonSets/01-Introduction-DaemonSets.md)
- [2. Creating DaemonSet](./04-Workloads-Resource/03-DaemonSets/10.2-creating-DaemonSets.md)
- [3. Interview Questions](./04-Workloads-Resource/03-DaemonSets/10.4-Interview-Questions.md)

#### 4.4. ReplicaSets

- [1. ReplicaSets](./04-Workloads-Resource/04-ReplicaSets/01-Introduction-ReplicaSets.md)
- [2. Interview Questions](./04-Workloads-Resource/04-ReplicaSets/02-Interview-Questions.md)

#### 4.5. **Jobs and CronJobs**

- [1. Introduction to Jobs](./04-Workloads-Resource/05-Jobs-and-CronJobs/01-Introduction-Jobs.md)

- [2. Introduction to Cronjobs](./04-Workloads-Resource/05-Jobs-and-CronJobs/02-Introduction-Cronjobs.md)

### 5. Configuration Management

#### [5.1. ConfigMaps](./05-Configuration-Management/01-ConfigMaps.md)

- Creating and managing ConfigMaps
- Injecting ConfigMaps into Pods
- Updating ConfigMaps
- Best Practices
- ConfigMap as Command Line Arguments

#### [5.2. Secret](./05-Configuration-Management/02-Secret.md)

- Creating and managing Secrets
- Injecting Secrets into Pods securely
- Security Considerations
- Secret Types
- Updating and Rolling Secrets
- Best Practices

#### [5.3. Environment Variables](./05-Configuration-Management/03-Environment-Variables.md)

- Basics of Environment Variables
- Setting environment variables in Pods
- Using Environment Variables from ConfigMaps and Secrets
- Environment Variable Substitution

### 6. Security and Compliance

#### 6.1. RBAC (Role-Based Access Control)

##### [**6.1.1. Roles, RoleBindings, ClusterRoles, and ClusterRoleBindings**](./06-Security-and-Compliance/01-RBAC/01-All-types-of-roles.md)

- Creating RBAC
- Automating RBAC configurations with tools like kubectl and kustomize.
- Best practices for designing RBAC policies.
- Auditing and monitoring RBAC permissions.

##### [**6.1.2. Service Accounts and Permissions**](./06-Security-and-Compliance/01-RBAC/02-Service-Accounts-and-Permissions.md)

- Managing Service Accounts at scale.

#### 6.2. Secrets Management

##### [6.2.1. Integrating External Secrets Managers (e.g., HashiCorp Vault)](./06-Security-and-Compliance/02-Secrets-Management/01-External-Secrets-Managers.md)  

- Automating secret rotation and renewal.
- Using Kubernetes External Secrets or Secrets Store CSI Driver.

##### [6.2.2. Securing Secrets with Encryption](./06-Security-and-Compliance/02-Secrets-Management/02-Securing-Secrets-with-Encryption.md)

- Encrypting secrets at rest using KMS providers.
- Best practices for managing secrets in CI/CD pipelines.

#### [More Topics](./06-Security-and-Compliance/More-topics.md)

### **7. Service Mesh, Load Balancing and Ingress Controllers**

#### **7.1. Service Mesh**

##### [**7.1.1. Service Mesh Overview**](./07-Service-Mesh-Ingress-Controllers/01-Service-Mesh/01-Service-Mesh-Intro.md)

- Introduction to Service Mesh
- Introduction to Istio, Linkerd, and Consul
- Service Mesh Use Cases

##### [**7.1.2. Service Mesh Features**](./07-Service-Mesh-Ingress-Controllers/01-Service-Mesh/02-Service-Mesh-Features.md)

- Traffic Management, Load Balancing, and Failover
- Circuit Breaking and Retries

##### [**7.1.3. Secure Service Communication (mTLS)**](./07-Service-Mesh-Ingress-Controllers/01-Service-Mesh/03-Secure-service-communication.md)

- **Security Standards**
  - mTLS Implementation
  - Certificate Management
  - Policy Enforcement

#### **7.2. Ingress and Ingress Controllers**

##### [**7.2.1. Ingress Controllers Overview**](./07-Service-Mesh-Ingress-Controllers/02-Ingress-Controller/01-Ingress-Controller-Intro.md)

- Introduction to Ingress Controller
- Selection Criteria NGINX, Traefik, and other Ingress Controllers
- Ingress Controllers for Cloud Providers

##### [**7.2.2. Ingress Resource**](./07-Service-Mesh-Ingress-Controllers/02-Ingress-Controller/02-Ingress-Resource-Configuration.md)

- Introduction to Ingress or Ingress Resource
- Configure advanced Ingress resources
- Integrate Ingress with Service Mesh

##### [**7.2.3. SSL/TLS Termination and HTTPS Routing**](./07-Service-Mesh-Ingress-Controllers/02-Ingress-Controller/03-ssl-tsl-routing.md)

- **Security Practices**
  - Configure SSL/TLS termination in Ingress Controllers.
  - Set up automated certificate management using tools like cert-manager.
  - Ensure compliance with security standards by enforcing HTTPS routing.

### **8. Kubernetes Performance and Optimization**

#### **8.1. Resource Management**

- CPU and Memory Resource Requests and Limits
- Quality of Service (QoS) Classes

#### **8.2. Horizontal Pod Autoscaler (HPA)**

- Scaling Pods Based on Metrics
- Custom Metrics for Autoscaling

#### **8.3. Vertical Pod Autoscaler (VPA)**

- Automatically Adjusting Resource Requests

#### **8.4. Cluster Autoscaler**

- Scaling the Kubernetes Cluster Nodes

#### **8.5. Performance Tuning**

- Node and Cluster Level Performance Optimization
- Pod Scheduling and Resource Optimization

---

## Tools

- [List of all most used tools](./Module-T/Everything-about-Tools.md)

### T1. **Helm Charts:**

- [T1.0 Helm Syllabus](./Module-T/Module-T1/T1.0-Helm-Syllabus.md)
- [T1.1 Introduction to Helm](./Module-T/Module-T1/T1.1-Introduction-Helm.md)
- [T1.2 Installation and Setup](./Module-T/Module-T1/T1.2-Helm-Installation-Setup.md)
- [T1.3 Commands & Structure](./Module-T/Module-T1/T1.3-Helm-Basics.md)
- [T1.4 Creating Custom Helm Chart](./Module-T/Module-T1/T1.4-Creating-Custom-Helm-Chart.md)
- [T1.5 Helmfile](./Module-T/Module-T1/T1.5-Helmfile.md)
- [T1.6 Helm Repo](./Module-T/Module-T1/T1.6-Helm-repo.md)
- [T1.7 Helm Hooks and Helm Test](./Module-T/Module-T1/T1.7-Helm-hook-test.md)

### T2. **Kustomize:**

- **Theory:**

  - Explore Kustomize, a built-in customization mechanism in Kubernetes, for creating and managing manifests more efficiently.

- **Project: Custom Manifests with Kustomize**
  - Description: Use Kustomize to customize Kubernetes manifests for different environments without modifying the original files.

---

## Cloud kubernetes

### AWS - EKS

### Azure - AKS

### GCP - GKE

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

### Advanced Kubernetes Learning Syllabus for Industry-Level Knowledge

#### **3. Configuration Management**

- **ConfigMaps and Secrets**
  - Managing Configuration Data
  - Using Secrets for Sensitive Information
- **Helm**
  - Helm Charts: Creating, Using, and Managing
  - Templating and Customizing Deployments
- **Kustomize**
  - Overlay and Patch Kubernetes Resources
  - Custom Resource Definitions (CRDs)

#### **7. Monitoring, Logging, and Tracing**

- **Monitoring**
  - Prometheus and Grafana Setup
  - Alerting with Prometheus Alertmanager
  - Advanced Monitoring Techniques
- **Logging**
  - Centralized Logging with ELK/EFK Stack (Elasticsearch, Logstash/Fluentd, Kibana)
  - Loki and Promtail for Logging
- **Tracing**
  - Distributed Tracing with Jaeger and Zipkin
  - Integrating Tracing with Service Mesh

#### **8. Kubernetes Performance and Optimization**

- **Resource Management**
  - CPU and Memory Resource Requests and Limits
  - Quality of Service (QoS) Classes
- **Horizontal Pod Autoscaler (HPA)**
  - Scaling Pods Based on Metrics
  - Custom Metrics for Autoscaling
- **Vertical Pod Autoscaler (VPA)**
  - Automatically Adjusting Resource Requests
- **Cluster Autoscaler**
  - Scaling the Kubernetes Cluster Nodes
- **Performance Tuning**
  - Node and Cluster Level Performance Optimization
  - Pod Scheduling and Resource Optimization

#### **9. CI/CD Pipelines with Kubernetes**

- **Continuous Integration (CI)**
  - Integrating Jenkins with Kubernetes
  - GitLab CI/CD with Kubernetes
- **Continuous Deployment (CD)**
  - Spinnaker for Kubernetes Deployments
  - ArgoCD for GitOps-based Deployment
- **Testing in CI/CD Pipelines**
  - Automated Testing in Kubernetes
  - Canary Releases and Blue-Green Deployments

#### **10. Advanced Kubernetes Ecosystem**

- **Operator Framework**
  - Building and Managing Operators
  - Advanced Operator Patterns
- **Custom Resource Definitions (CRDs)**
  - Extending Kubernetes Functionality
  - Developing and Using CRDs
- **Multi-Cluster Management**
  - Federation and Cluster API
  - Managing Clusters Across Different Environments

#### **11. Kubernetes Security Best Practices**

- **Supply Chain Security**
  - Image Scanning with Trivy, Clair, etc.
  - Securing Container Images
- **Pod Security Standards**
  - Least Privilege, No Root Containers
  - Securing Pod-to-Pod Communication
- **Compliance and Auditing**
  - Implementing CIS Benchmarks
  - Auditing Kubernetes Clusters for Compliance

#### **12. Disaster Recovery and High Availability**

- **Disaster Recovery Strategies**
  - Backup and Restore Workloads
  - Cluster-level Disaster Recovery
- **High Availability (HA)**
  - HA for Control Plane Components
  - HA for Stateful Applications

#### **13. Advanced Kubernetes Troubleshooting**

- **Pod-Level Troubleshooting**
  - Debugging Pod Failures, CrashLoopBackOff, ImagePullBackOff, etc.
- **Node-Level Troubleshooting**
  - Node Resource Issues, Disk Pressure, Network Issues
- **Cluster-Level Troubleshooting**
  - etcd Failures, API Server Downtime, Scheduler Issues

#### **14. Kubernetes on Cloud Providers**

- **Managed Kubernetes Services**
  - GKE (Google Kubernetes Engine), EKS (Amazon Elastic Kubernetes Service), AKS (Azure Kubernetes Service)
- **Hybrid and Multi-Cloud Kubernetes**
  - Using Kubernetes Across Multiple Cloud Providers
  - Kubernetes on Bare Metal

#### **15. Real-World Projects and Case Studies**

- **Project 1: Building a Scalable Microservices Architecture**
- **Project 2: Implementing CI/CD Pipelines with Kubernetes**
- **Project 3: Advanced Monitoring and Logging Setup**
- **Project 4: Building and Deploying a Custom Operator**
- **Project 5: Multi-Cluster Management and Disaster Recovery**

---
