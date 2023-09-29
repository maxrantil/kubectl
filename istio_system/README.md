# Istio System Cleanup Commands

These commands help you perform cleanup tasks related to Istio in your Kubernetes cluster, including deleting Istio gateways, virtual services, pods, and the Istio system namespace.

---

**Delete an Istio gateway:**

```bash
$ kubectl delete gateway kiada-gateway -n istio-system
```

This command deletes the Istio gateway named "kiada-gateway" in the "istio-system" namespace. Gateways are used for defining ingress and egress points for traffic in Istio.

**Delete an Istio virtual service:**

```bash
$ kubectl delete virtualservice kiada -n istio-system
```

Use this command to delete the Istio virtual service named "kiada" in the "istio-system" namespace. Virtual services define routing rules for traffic in Istio.

**Delete all pods in the Istio system namespace:**

```bash
$ kubectl delete pods --all -n istio-system
```

This command deletes all pods in the "istio-system" namespace. Be cautious when using this command, as it removes all Istio-related pods, which may affect the functionality of Istio in your cluster.

**Delete the Istio system namespace:**

```bash
$ kubectl delete namespace istio-system
```

Use this command to delete the entire "istio-system" namespace, which includes all Istio-related resources and configurations. Be careful when deleting namespaces, as it can lead to data loss.

**List Istio Gateways and Virtual Services:**

```bash
$ kubectl get gateway,virtualservice -n istio-system
```

You can use this command to list Istio gateways and virtual services in the "istio-system" namespace before performing deletions.

---

These commands allow you to perform cleanup tasks in your Istio system, such as removing gateways, virtual services, pods, and even the entire Istio system namespace. Use them carefully to manage your Istio configuration and resources.

# Istio System Namespace

In a Kubernetes environment, the "istio-system" namespace is a dedicated namespace used by Istio, an open-source service mesh platform, to manage and deploy its control plane components. The Istio control plane includes various components responsible for traffic management, security, telemetry, and policy enforcement within a Kubernetes cluster.

Here's a brief overview of the components typically found in the "istio-system" namespace:

1. **Istio Pilot:** This component is responsible for configuring the proxy sidecars and managing their policies and routing rules. It ensures that traffic is correctly routed between services.

2. **Istio Citadel:** Citadel handles certificate issuance and management for securing communication between services using mutual TLS (mTLS). It issues and rotates certificates for service-to-service authentication.

3. **Istio Galley:** Galley is responsible for validating and processing Istio configuration files (e.g., virtual services, destination rules) and distributing them to the appropriate components.

4. **Istio Ingress Gateway:** The Ingress Gateway manages external traffic entering the cluster. It acts as the entry point for incoming requests and enforces Istio's routing and security policies.

5. **Istio Egress Gateway:** Similar to the Ingress Gateway but for outgoing traffic, the Egress Gateway controls how services in the cluster access external services.

6. **Telemetry Components:** Istio also includes components like Prometheus and Grafana for collecting and visualizing telemetry data (e.g., metrics, traces) related to service communication.

7. **Policy Enforcement Components:** Istio can enforce policies related to security, access control, and rate limiting. These policies are configured and enforced by components like Mixer.

The "istio-system" namespace provides isolation for Istio's control plane components, separating them from the application services running in other namespaces within the Kubernetes cluster. It helps manage and maintain the Istio infrastructure separately from application workloads, simplifying upgrades, configuration changes, and troubleshooting.

Overall, Istio simplifies complex microservices architectures by providing features like traffic routing, load balancing, security, and observability while utilizing the "istio-system" namespace to manage its core components.
