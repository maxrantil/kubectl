# kubectl

Kubernetes Logs using kubectl

Logs are a critical component for debugging and monitoring applications in Kubernetes. The kubectl logs command is essential for retrieving these logs from pods and containers.

---
### Basic Log Retrieval

**Fetch logs of a specific pod:**
**To retrieve the logs of a specific pod:**

```bash
$ kubectl logs [POD_NAME]
```

    Example: $ kubectl logs kiada

**Fetch logs of a specific container within a pod:**
**If a pod has multiple containers, specify the container name to fetch its logs:**

```bash
$ kubectl logs [POD_NAME] -c [CONTAINER_NAME]
```

    Examples:
        $ kubectl logs kiada-ssl -c kiada
        $ kubectl logs kiada-ssl -c envoy

---
### Streaming Logs

**Stream logs in real-time:**
**The -f or --follow flag allows you to stream logs:**

```bash
$ kubectl logs [POD_NAME] -f
```

    Examples:
        $ kubectl logs kiada -f
        $ kubectl logs kiada-ssl -c kiada -f

---
### Advanced Log Retrieval

**Add timestamps to logs:**

```bash
$ kubectl logs [POD_NAME] --timestamps=true
```

    Example: $ kubectl logs kiada --timestamps=true

**Retrieve logs since a specific time duration:**

```bash
$ kubectl logs [POD_NAME] --since=[DURATION]
```

    Example: $ kubectl logs kiada --since=2m

**Retrieve logs since a specific timestamp:**

```bash
$ kubectl logs [POD_NAME] --since-time=[TIMESTAMP]
```

    Example: $ kubectl logs kiada --since-time=2020-02-01T09:50:00Z

**Tail logs (show only the last few lines):**

```bash
$ kubectl logs [POD_NAME] --tail=[NUMBER_OF_LINES]
```

    Example: $ kubectl logs kiada --tail=10

**Retrieve logs from all containers within a pod:**

```bash
$ kubectl logs [POD_NAME] --all-containers
```

    Example: $ kubectl logs kiada-ssl --all-containers

**Retrieve logs from a previous instance of a container:**

```bash
$ kubectl logs [POD_NAME] -c [CONTAINER_NAME] -p
```

    Example: $ kubectl logs kiada-liveness -c envoy -p

---
### Fetching Logs Using Selectors and Resources

**Using label selectors:**
**Retrieve logs from pods with specific labels:**

```bash
$ kubectl logs -l [LABEL_SELECTOR] -c [CONTAINER_NAME]
```

    Examples:
      $ kubectl logs -l app=kiada -c envoy
      $ kubectl logs -l app=kiada --all-containers --prefix

**Fetching logs from specific resource types:**
**Retrieve logs from pods associated with specific Kubernetes resources like ReplicaSets (rs) or Jobs (job):**

```bash
$ kubectl logs [RESOURCE_TYPE]/[RESOURCE_NAME] -c [CONTAINER_NAME]
```

    Examples:
      $ kubectl logs rs/kiada -c kiada
      $ kubectl logs job/quiz-init --all-containers --prefix
