1. **Introduction to Kubernetes:**

   - **Theory:**

     - Understand the basics of Kubernetes, its architecture, and its role in container orchestration.

   - **Project: Setting up a Local Cluster**

     - Description: Create a small Kubernetes cluster using tools like Minikube or Kind on your local machine. Deploy a basic application to get a feel for Kubernetes.

   - [1.1 What is Kubernetes?](./Module-1/1.1-What-is-Kubernetes.md)
   - [1.2 Kubernetes Architecture](./Module-1/1.2-kubernetes-architecture.md)
   - [1.3 Kubernetes Workflow](./Module-1/1.3-Kubernetes-Workflow.md)

   - [1.4 Setting up a K8s Cluster (local)](./Module-1/1.4-Kubernetes-Installation-using-Minikube.md)
   - [1.5 Setting up a K8s Cluster (kubeadm)](./Module-1/1.5-Kubernetes-Installation-using-kubeadm.md)
   - [1.6 Kubernetes Garbage Collection](./Module-1/1.6-Kubernetes-Garbage-Collection.md)
   - [1.7 Some Imp Topics](./Module-1/1.7-Some-Imp-Topics.md)
     - How external services connect to the cluster

2. **Kubernetes Objects:**

   - **Theory:**

     - Learn about the fundamental building blocks in Kubernetes, known as objects.
     - Common examples of objects include Pods, Services, Deployments, ConfigMaps, Secrets, etc.

   - **Project: Basic Pod Deployment**

     - Description: Deploy a simple web server using a Pod manifest. Experiment with different configurations such as environment variables and commands.

   - [2.1 Basics of YAML Syntax](./Module-2/2.1-Basics-of-YAML-Syntax.md)

3. **YAML Syntax:**

   - **Theory:**

     - Familiarize yourself with YAML syntax, as Kubernetes manifests are typically written in YAML.

   - **Project: YAML Configuration Practice**
     - Description: Create various YAML files for different Kubernetes objects, ensuring correct syntax and understanding indentation and key-value pairs.

4. **Pods:**

   - **Theory:**

     - Start with Pods, which are the smallest deployable units in Kubernetes.
     - Learn how to define a Pod manifest, including containers, volumes, and labels.

   - **Project: Multi-Container Pod**
     - Description: Design a Pod that contains multiple containers that need to work together, demonstrating inter-container communication.

5. **ReplicaSets:**

   - **Theory:**

     - Explore ReplicaSets, which ensure a specified number of replicas for a Pod are running at all times.
     - Understand how to create and manage ReplicaSets.

   - **Project: Scaling with ReplicaSets**
     - Description: Deploy an application with ReplicaSets and observe how Kubernetes maintains the specified number of replicas.

6. **Deployments:**

   - **Theory:**

     - Introduce Deployments, a higher-level abstraction over ReplicaSets, providing declarative updates to applications.
     - Learn about rolling updates, rollbacks, and other deployment strategies.

   - **Project: Rolling Updates and Rollbacks**
     - Description: Deploy a sample app, make changes to the deployment manifest, and observe rolling updates. Practice rollbacks in case of issues.

7. **Services:**

   - **Theory:**

     - Understand Services, which enable communication between different parts of your application within a cluster.
     - Explore ClusterIP, NodePort, and LoadBalancer types.

   - **Project: Microservices Communication**
     - Description: Deploy two separate applications and create services to enable communication between them. Explore different service types.

8. **ConfigMaps and Secrets:**

   - **Theory:**

     - Learn how to use ConfigMaps for configuration data and Secrets for sensitive information.
     - Understand how to reference them in Pod configurations.

   - **Project: Configuring Applications**
     - Description: Externalize configuration using ConfigMaps and store sensitive information such as database credentials using Secrets.

9. **Namespaces:**

   - **Theory:**

     - Explore Namespaces to create isolated environments within a cluster.
     - Understand how to organize and segregate resources using Namespaces.

   - **Project: Multi-Environment Cluster**
     - Description: Use Namespaces to create distinct environments (e.g., development, staging, production) within a single Kubernetes cluster.

10. **Persistent Volumes and Persistent Volume Claims:**

- **Theory:**

  - Discover how to define persistent storage in Kubernetes.
  - Learn about Persistent Volumes (PVs) and Persistent Volume Claims (PVCs).

- **Project: Persistent Storage for Database**
  - Description: Deploy a database with persistent storage using Persistent Volumes and Persistent Volume Claims.

11. **StatefulSets:**

    - **Theory:**

      - Explore StatefulSets for stateful applications that require stable network identities and persistent storage.

    - **Project: Stateful Application Deployment**
      - Description: Deploy a stateful application using StatefulSets, ensuring stable network identities and persistent storage.

12. **DaemonSets:**

    - **Theory:**

      - Understand DaemonSets, which ensure that all Nodes run a copy of a Pod, useful for system daemons.

    - **Project: System Daemons Deployment**
      - Description: Deploy a DaemonSet to ensure that a specific Pod runs on every node in the cluster.

13. **Jobs and CronJobs:**

    - **Theory:**

      - Learn about Jobs for running one-off tasks and CronJobs for scheduled tasks.

    - **Project: Scheduled Tasks**
      - Description: Create a Job to perform a one-off task and a CronJob to schedule tasks at specified intervals.

14. **Resource Quotas and LimitRange:**

    - **Theory:**

      - Explore resource management in Kubernetes using Resource Quotas and LimitRange.

    - **Project: Resource Management**
      - Description: Set up Resource Quotas to limit resource usage in a Namespace. Experiment with LimitRange to restrict container resource limits.

15. **Annotations and Labels:**

    - **Theory:**

      - Understand the importance of annotations and labels for organizing and managing resources.

    - **Project: Resource Organization**
      - Description: Apply labels and annotations to various objects in your cluster for organizational purposes and observe their impact.

16. **RBAC (Role-Based Access Control):**

    - **Theory:**

      - Learn about RBAC to control access to resources within a cluster.

    - **Project: User Access Management**
      - Description: Implement RBAC to control user access to resources within a Namespace. Create roles and role bindings accordingly.

17. **Helm Charts:**

    - **Theory:**

      - Introduce Helm, a package manager for Kubernetes, and understand how to use Helm charts to define, install, and upgrade even the most complex Kubernetes applications.

    - **Project: Helm Chart for Application**
      - Description: Package your application using Helm charts. Include configurations, dependencies, and versioning in the Helm chart.

18. **Kustomize:**

    - **Theory:**

      - Explore Kustomize, a built-in customization mechanism in Kubernetes, for creating and managing manifests more efficiently.

    - **Project: Custom Manifests with Kustomize**
      - Description: Use Kustomize to customize Kubernetes manifests for different environments without modifying the original files.

19. **Custom Resource Definitions (CRDs):**

    - **Theory:**

      - Understand how to extend Kubernetes API using Custom Resource Definitions to define custom resources and controllers.

    - **Project: Custom Resource and Controller**
      - Description: Define a custom resource using CRDs and implement a controller to manage the lifecycle of the custom resource.

20. **Monitoring and Logging:**

    - **Theory:**

      - Learn how to set up monitoring and logging for your Kubernetes cluster, exploring tools like Prometheus and Grafana.

    - **Project: Monitoring Setup with Prometheus and Grafana**
      - Description: Set up Prometheus for monitoring and Grafana for visualization. Create dashboards to monitor key metrics of your applications.

21. **Network Policies:**

    - **Theory:**

      - Explore Network Policies to control the communication between Pods in a cluster.

    - **Project: Network Segmentation**
      - Description: Implement Network Policies to control the flow of traffic between Pods in different Namespaces, ensuring a secure network environment.
