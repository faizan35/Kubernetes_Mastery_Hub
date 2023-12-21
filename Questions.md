Q) what is the difference between lables and selectors.?
A) Lables is the identifications that you give to a pod or to a deployment to match the desired state.
Selectors are the criterias in which you are doing the matching.

CrashLoopBackOff

HELM internally kubeCTL ko call krta h , so master node pe chalta h.

Q) Explain the concept of a Pod in Kubernetes and why it is important.

A) This question assesses the candidate's understanding of fundamental Kubernetes concepts. Look for an answer that mentions how a Pod is the basic building block, representing the smallest deployable unit, and how it can host one or more containers that share the same network namespace.

Q) Describe the role and significance of Deployments in Kubernetes.

A) This question evaluates the candidate's knowledge of Kubernetes orchestration and scalability. A good response should cover how Deployments provide declarative updates to applications, manage the deployment lifecycle, and ensure high availability by allowing rolling updates and rollbacks.



Q) What is the role of a Service in Kubernetes, and how does it facilitate communication between different Pods?

A) This question assesses the candidate's understanding of networking in Kubernetes. A comprehensive answer should cover how Services provide a stable endpoint for accessing a set of Pods, enabling load balancing and discovery within the cluster. Discussing different types of Services, such as ClusterIP, NodePort, and LoadBalancer, would be a plus.

Q) Explain the concept of Persistent Volumes (PVs) and Persistent Volume Claims (PVCs) in Kubernetes. How do they contribute to data persistence in containerized environments?

A) This question delves into the candidate's knowledge of storage management in Kubernetes. A good response should touch upon how Persistent Volumes provide a way for Pods to access durable storage, and Persistent Volume Claims act as a request for storage resources. Look for an understanding of how these components enable data persistence across container restarts and rescheduling.



Q) Explain the concept of Kubernetes Secrets and ConfigMaps. How are they used to manage sensitive information and configuration in containerized applications?

A) This question evaluates the candidate's understanding of managing sensitive data and configuration in Kubernetes. A good answer should cover the purpose of Secrets for managing sensitive information like API keys or passwords and ConfigMaps for handling non-sensitive configuration data. Candidates should also discuss how these resources are mounted into Pods as volumes or environment variables and how they contribute to the separation of configuration from application code in a containerized environment.
