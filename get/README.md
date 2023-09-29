```markdown
# Kubernetes Resource Retrieval using kubectl

The `kubectl get` command allows you to retrieve various Kubernetes resources, such as nodes, deployments, pods, services, and more.

---

### Nodes

**Retrieve all nodes:**

```bash
$ kubectl get nodes
```

    Examples:
    $ kubectl get nodes
    $ kind get nodes

**Detailed information about a specific node:**

```bash
$ kubectl get node [NODE_NAME] -o [OUTPUT_FORMAT]
```

    Examples:
    $ kubectl get node kind-control-plane -o yaml

---

### Deployments

**Retrieve all deployments:**

```bash
$ kubectl get deployments
```

    Examples:
    $ kubectl get deployments
    $ kubectl get deploy

---

### Pods

**Retrieve all pods:**

```bash
$ kubectl get pods
```

    Examples:
    $ kubectl get pods
    $ kubectl get po

**Detailed information about a specific pod:**

```bash
$ kubectl get pod [POD_NAME] -o [OUTPUT_FORMAT]
```

    Examples:
    $ kubectl get po kiada -o yaml

**Retrieve pods with additional information:**

```bash
$ kubectl get pods -o wide
```

    Example: $ kubectl get pods -o wide

**Watch pods in real-time:**

```bash
$ kubectl get pods -w
```

    Examples:
    $ kubectl get pods -w
    $ kubectl get po -w

---

### Services (svc)

**Retrieve all services:**

```bash
$ kubectl get svc
```

    Examples:
    $ kubectl get svc
    $ kubectl get svc -A

**Retrieve a specific service:**

```bash
$ kubectl get svc [SERVICE_NAME]
```

    Example: $ kubectl get svc kiada

---

### Events (ev)

**Retrieve all events:**

```bash
$ kubectl get events
```

    Examples:
    $ kubectl get ev
    $ kubectl get events

**Retrieve events with specific criteria:**

```bash
$ kubectl get events --field-selector [CRITERIA]
```

    Example: $ kubectl get ev --field-selector type=Warning

---

### Persistent Volumes (pv) and Persistent Volume Claims (pvc)

**Retrieve all persistent volumes:**

```bash
$ kubectl get pv
```

**Retrieve a specific persistent volume:**

```bash
$ kubectl get pv [PV_NAME]
```

**Retrieve all persistent volume claims:**

```bash
$ kubectl get pvc
```

---

### Namespaces

**Retrieve all namespaces:**

```bash
$ kubectl get namespaces
```

    Examples:
    $ kubectl get ns
    $ kubectl get namespaces

---

### Advanced Retrievals

**Retrieve resources with specific labels:**

```bash
$ kubectl get [RESOURCE] -l [LABEL_SELECTOR]
```

**Retrieve resources with specific field selectors:**

```bash
$ kubectl get [RESOURCE] --field-selector [FIELD_SELECTOR]
```

**Retrieve resources across all namespaces:**

```bash
$ kubectl get [RESOURCE] -A
```

---

### Other Resources

The `kubectl get` command can be used to retrieve a variety of other resources, such as ReplicaSets (rs), DaemonSets (ds), ConfigMaps (cm), Jobs, CronJobs (cj), and more.
