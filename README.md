# Kubernetes Deployment and Networking Commands

These commands are essential for deploying, networking, and interacting with pods in a Kubernetes cluster.

---

### Deploying Pods

**Deploy a Kubernetes pod:**

```bash
$ kubectl apply -f pod.kiada.yaml
```

This command deploys a Kubernetes pod using the configuration specified in the "pod.kiada.yaml" file.

**Run a client pod to make a curl request:**

```bash
$ kubectl run --image=curlimages/curl -it --restart=Never --rm client-pod curl 10.244.2.4:8080
```

This command launches a client pod that makes a curl request to the specified IP and port.

---

### Port Forwarding

**Forward a local port to a pod's port:**

```bash
$ kubectl port-forward kiada 8080
```

Use this command to create a port-forwarding tunnel from your local machine to a pod's port.

**Make a curl request to a local forwarded port:**

```bash
$ curl localhost:8080
```

After port-forwarding, use this command to make a curl request to the locally forwarded port, which is connected to the pod.

---

### Copying Files

**Copy a file from a pod to the local filesystem:**

```bash
$ kubectl cp kiada:html/index.html /tmp/index.html
```

This command copies a file named "index.html" from the "kiada" pod to your local "/tmp" directory.

**Copy a file from the local filesystem to a pod:**

```bash
$ kubectl cp /tmp/index.html kiada:html/
```

Use this command to copy a file named "index.html" from your local "/tmp" directory to the "kiada" pod.

---

### Executing Commands

**Execute a command in a running pod:**

```bash
$ kubectl exec kiada -- ps aux
```

This command runs the "ps aux" command inside the running "kiada" pod, displaying information about running processes.

**Execute a curl command in a pod:**

```bash
$ kubectl exec kiada -- curl -s localhost:8080
```

This command executes a "curl" command within the "kiada" pod to make a request to a local port.

```bash
$ kubectl exec kiada curl -s localhost:8080
```

Alternatively, you can execute a "curl" command directly within the "kiada" pod without specifying the shell.

**Start an interactive bash shell in a pod:**

```bash
$ kubectl exec -it kiada -- bash
```

Use this command to open an interactive bash shell within the "kiada" pod, allowing you to run commands interactively.

**Attach to a running pod:**

```bash
$ kubectl attach kiada
```

This command attaches to a running "kiada" pod, allowing you to interact with its console.

---

# Port Forwarding and Networking Commands

These commands are useful for port forwarding and networking-related tasks in a Kubernetes cluster.

---

### Port Forwarding

**Forward a local port to a pod's port:**

```bash
$ kubectl port-forward kiada-stdin 8888:8080
```

This command creates a port-forwarding tunnel, forwarding local port 8888 to a pod's port 8080.

**Make a curl request to a locally forwarded port:**

```bash
$ curl localhost:8888
```

After port-forwarding, use this command to make a curl request to the locally forwarded port (8888), which is connected to the specified pod.
