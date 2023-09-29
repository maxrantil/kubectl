# Kubernetes Cluster Commands

Kubernetes clusters are essential for deploying and managing containerized applications. Below are common Kubernetes cluster-related commands:

---

### Create a Kubernetes Cluster

**Create a Kubernetes cluster:**

```bash
$ kubectl create cluster
```

This command creates a new Kubernetes cluster using the default configuration.

**Create a Kubernetes cluster with a specific configuration:**

```bash
$ kubectl create cluster --config kind-multi-node.yaml
```

Here, the "kind-multi-node.yaml" configuration file is used to create a Kubernetes cluster with custom settings. You can provide your own configuration file for cluster customization.

---

### Cluster Management

**Execute a bash shell in the control plane node of a cluster:**

```bash
$ kubectl exec -it kind-control-plane bash
```

This command allows you to access a bash shell in the control plane node of a Kubernetes cluster created using "kind." You can use this shell for debugging or administrative tasks within the cluster.

**Manage Cluster Nodes:**

```bash
$ kubectl get nodes
```

This command lists all nodes in the Kubernetes cluster, providing information about their status and resources.

**Access Cluster Information:**

```bash
$ kubectl cluster-info
```

This command displays essential information about the Kubernetes cluster, including the API server and dashboard URLs.

**View Cluster Configuration:**

```bash
$ kubectl config view
```

Use this command to view the current Kubernetes configuration, including the clusters, contexts, and users configured on your system.

**Switch Kubernetes Contexts:**

```bash
$ kubectl config use-context [CONTEXT_NAME]
```

If you have multiple Kubernetes clusters or contexts, use this command to switch between them. Replace `[CONTEXT_NAME]` with the desired context.

**Create a Namespace:**

```bash
$ kubectl create namespace [NAMESPACE_NAME]
```

You can create namespaces to organize and isolate resources within your cluster. Replace `[NAMESPACE_NAME]` with your chosen namespace name.

**Delete a Namespace and Its Resources:**

```bash
$ kubectl delete namespace [NAMESPACE_NAME]
```

Be cautious when using this command, as it permanently deletes the specified namespace and all resources within it.

**Scale Deployments:**

```bash
$ kubectl scale deployment [DEPLOYMENT_NAME] --replicas=[NUMBER]
```

This command allows you to scale a deployment to a desired number of replicas. Replace `[DEPLOYMENT_NAME]` with the deployment you want to scale and `[NUMBER]` with the desired replica count.

**Apply Configuration Changes:**

```bash
$ kubectl apply -f [CONFIG_FILE]
```

When you make changes to your Kubernetes configuration, use this command to apply those changes to the cluster. Replace `[CONFIG_FILE]` with the path to your configuration file.

**Inspect Cluster Resources:**

```bash
$ kubectl describe [RESOURCE_TYPE] [RESOURCE_NAME]
```

Use this command to get detailed information about a specific Kubernetes resource. Replace `[RESOURCE_TYPE]` with the type of resource (e.g., pod, service) and `[RESOURCE_NAME]` with the resource's name.

**Access Kubernetes Dashboard:**

```bash
$ kubectl proxy
```

Once the proxy is running, you typically access the dashboard by navigating to: `http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/` in your web browser.


**List Available Kubernetes Plugins:**

```bash
$ kubectl plugin list
```

Kubectl supports various plugins for extending its functionality. Use this command to list the available plugins.
