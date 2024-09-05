### **7.2.2. Ingress Resource Configuration**

## What is Ingress or Ingress Resource?

- It is an API object
- **used** to manage **external access** to services within a cluster.
- It provides HTTP and HTTPS routing to services based on hostnames and paths.
- Ingress **sits between** the external traffic and the services running in a Kubernetes cluster, acting as a traffic controller.

##### OR

- An Ingress Resource is defined in YAML files as manifests that represent the desired state for routing external traffic to services in a Kubernetes cluster.
- It dictates how incoming requests should be directed to the appropriate services based on defined rules.

---

### **Configure Advanced Ingress Resources**

**Ingress Resources** are API objects in Kubernetes that define how external HTTP/HTTPS traffic should be routed to services within the cluster. While basic configurations handle simple routing, advanced configurations allow for more complex traffic management and customization.

#### **Key Advanced Configurations:**

1. **Path-Based Routing:**

   - **Overview:** Routes traffic to different services based on the request path.
   - **Example:** You can route `/api/*` requests to a backend service and `/web/*` requests to a frontend service.
   - **Use Case:** Ideal for microservices architectures where different services handle different parts of the application.

   ```yaml
   apiVersion: networking.k8s.io/v1
   kind: Ingress
   metadata:
     name: my-ingress
   spec:
     rules:
       - host: myapp.example.com
         http:
           paths:
             - path: /api/
               pathType: Prefix
               backend:
                 service:
                   name: api-service
                   port:
                     number: 80
             - path: /web/
               pathType: Prefix
               backend:
                 service:
                   name: web-service
                   port:
                     number: 80
   ```

2. **Host-Based Routing:**

   - **Overview:** Directs traffic to services based on the host or domain name in the request.
   - **Example:** Requests to `api.example.com` are routed to the `api-service`, while requests to `web.example.com` are routed to the `web-service`.
   - **Use Case:** Useful for running multiple services under different subdomains.

   ```yaml
   apiVersion: networking.k8s.io/v1
   kind: Ingress
   metadata:
     name: host-ingress
   spec:
     rules:
       - host: api.example.com
         http:
           paths:
             - path: /
               pathType: Prefix
               backend:
                 service:
                   name: api-service
                   port:
                     number: 80
       - host: web.example.com
         http:
           paths:
             - path: /
               pathType: Prefix
               backend:
                 service:
                   name: web-service
                   port:
                     number: 80
   ```

3. **TLS/SSL Configuration:**

   - **Overview:** Secures traffic by configuring HTTPS with TLS certificates.
   - **Example:** You can specify which TLS certificate to use for a given host.
   - **Use Case:** Essential for securing sensitive data and meeting compliance requirements.

   ```yaml
   apiVersion: networking.k8s.io/v1
   kind: Ingress
   metadata:
     name: tls-ingress
   spec:
     tls:
       - hosts:
           - secure.example.com
         secretName: tls-secret
     rules:
       - host: secure.example.com
         http:
           paths:
             - path: /
               pathType: Prefix
               backend:
                 service:
                   name: secure-service
                   port:
                     number: 443
   ```

4. **Custom Annotations:**

   - **Overview:** Use annotations to customize the behavior of the Ingress Controller, such as enabling specific features or optimizations.
   - **Example:** Annotations can be used to enable HTTP/2, set timeouts, or redirect HTTP to HTTPS.
   - **Use Case:** Tailoring the Ingress behavior to meet specific application needs.

   ```yaml
   apiVersion: networking.k8s.io/v1
   kind: Ingress
   metadata:
     name: annotated-ingress
     annotations:
       nginx.ingress.kubernetes.io/rewrite-target: /
       nginx.ingress.kubernetes.io/ssl-redirect: "true"
   spec:
     rules:
       - host: myapp.example.com
         http:
           paths:
             - path: /old-path
               pathType: Prefix
               backend:
                 service:
                   name: new-service
                   port:
                     number: 80
   ```

5. **Rate Limiting and Throttling:**

   - **Overview:** Control the rate of requests to prevent abuse or overloading of services.
   - **Example:** Use annotations to set rate limits on requests per second.
   - **Use Case:** Protects your services from excessive traffic, especially important in public-facing APIs.

   ```yaml
   apiVersion: networking.k8s.io/v1
   kind: Ingress
   metadata:
     name: rate-limit-ingress
     annotations:
       nginx.ingress.kubernetes.io/limit-connections: "20"
       nginx.ingress.kubernetes.io/limit-rpm: "60"
   spec:
     rules:
       - host: myapi.example.com
         http:
           paths:
             - path: /
               pathType: Prefix
               backend:
                 service:
                   name: api-service
                   port:
                     number: 80
   ```

#### **Why These Configurations Matter for DevOps:**

- **Security:** Ensures that only authorized traffic reaches your services and that sensitive data is encrypted.
- **Performance:** Optimizes the way traffic is routed and managed, reducing latency and improving user experience.
- **Flexibility:** Allows for detailed control over how traffic is handled, enabling complex scenarios like blue-green deployments, A/B testing, or multi-tenant environments.

---

### **Integrate Ingress with Service Mesh**

Integrating Ingress Controllers with a Service Mesh combines the benefits of both, allowing you to manage external traffic while also controlling internal service-to-service communication.

#### **Key Integration Points:**

1. **Unified Traffic Management:**

   - **Overview:** Use the Ingress Controller to manage external traffic and the Service Mesh to handle internal traffic between services.
   - **Example:** An incoming request is routed by the Ingress Controller to a specific service, and the Service Mesh handles subsequent requests between microservices.
   - **Use Case:** Enables consistent policies for both external and internal traffic, such as load balancing, security enforcement, and traffic splitting.

2. **Security Integration:**

   - **Overview:** The Service Mesh can enforce mutual TLS (mTLS) for internal traffic, while the Ingress Controller handles TLS termination for incoming external traffic.
   - **Example:** An Ingress Controller terminates an HTTPS request, then passes it through the Service Mesh where mTLS ensures secure internal communication.
   - **Use Case:** Enhances security by ensuring encrypted communication both at the edge and within the cluster.

3. **Observability:**
   - **Overview:** Both the Ingress Controller and Service Mesh provide metrics and logs, which can be integrated into a single observability stack.
   - **Example:** Monitor the performance of traffic as it moves from the Ingress Controller through the Service Mesh to the final service.
   - **Use Case:** Comprehensive monitoring helps identify bottlenecks, latency issues, or failures in the traffic flow.

#### **Why Integration Matters for DevOps:**

- **Consistency:** Ensures that traffic policies are consistent across both external and internal traffic, reducing the complexity of managing different systems.
- **Enhanced Security:** Provides a layered security approach, protecting both the edge and internal communications.
- **Simplified Operations:** Streamlines traffic management and observability, making it easier to troubleshoot issues and optimize performance.

---

### **Summary for DevOps Engineers**

Configuring advanced Ingress resources and integrating them with a Service Mesh allows you to:

- **Control and Optimize Traffic:** Fine-tune how external requests are routed and handled, ensuring efficiency and performance.
- **Secure Communications:** Enforce SSL/TLS at the edge and within the cluster, protecting data and meeting compliance requirements.
- **Simplify Complex Scenarios:** Manage traffic across multiple services and environments with ease, supporting complex deployments and testing strategies.

Mastering these configurations is key to ensuring that your Kubernetes applications are secure, resilient, and performant.
