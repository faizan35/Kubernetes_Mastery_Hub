# **3.3. Cluster Networking Basics**

## **Cluster DNS and CoreDNS**

- **What is Cluster DNS?**

  - Cluster DNS is a DNS service specifically for the Kubernetes cluster.
  - It automatically creates DNS records for Kubernetes services, making it easier for Pods to find and communicate with each other using service names instead of IP addresses.

- **What is CoreDNS?**

  - CoreDNS is the DNS server used by Kubernetes.
  - It handles DNS queries within the cluster, resolving service names to their corresponding IP addresses.

- **How Does CoreDNS Work?**

  - When a Pod tries to connect to a service, it uses the service’s name (like `my-service`).
  - CoreDNS receives this request and translates the service name into the correct IP address so the connection can be made.

- **Example:**
  - Imagine you’re trying to call a friend but don’t know their phone number. You call a directory service (CoreDNS), ask for your friend’s number (service IP), and then make the call.

## **Service Discovery in Kubernetes**

- **What is Service Discovery?**

  - Service discovery in Kubernetes is the process of automatically finding and connecting to services running in the cluster.

- **How Does it Work?**

  - When a service is created, Kubernetes assigns it a DNS name (like `my-service`).
  - Pods can then use this DNS name to discover and connect to the service.

- **Types of Service Discovery:**

  - **DNS-Based Discovery:**
    - Most common method, where services are discovered via DNS names handled by CoreDNS.
  - **Environment Variables:**
    - Kubernetes also injects environment variables into Pods that point to service IP addresses. This method is less flexible than DNS.

- **Why is Service Discovery Important?**

  - It allows Pods to connect to services without needing to know the IP addresses of those services, which can change over time.

- **Example:**
  - Think of service discovery like looking up the location of a restaurant. Instead of memorizing the address (IP address), you just remember the name of the restaurant (service name) and look it up when you need it.

## **External and Internal DNS Resolution**

- **What is DNS Resolution?**

  - DNS resolution is the process of translating a domain name (like `www.example.com`) into an IP address that computers can use to make connections.

- **Internal DNS Resolution:**

  - **What is it?**
    - This is DNS resolution for services and Pods within the Kubernetes cluster.
  - **How Does it Work?**
    - CoreDNS resolves the names of services and Pods inside the cluster to their internal IP addresses.
  - **Why is it Important?**
    - It enables communication between different parts of your application running within the Kubernetes cluster.

- **External DNS Resolution:**

  - **What is it?**
    - This is DNS resolution for domain names that exist outside the Kubernetes cluster (like public websites).
  - **How Does it Work?**
    - When a Pod needs to reach an external service, CoreDNS forwards the DNS request to an external DNS server, which resolves the domain name to its public IP address.
  - **Why is it Important?**
    - It allows your applications to connect to external resources, such as APIs or other services hosted outside your Kubernetes cluster.

- **Example:**
  - Internal DNS resolution is like asking for directions within your neighborhood (the cluster), while external DNS resolution is like asking for directions to a place in another city (outside the cluster).
