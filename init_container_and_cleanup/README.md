# Kubernetes Init Container and Cleanup Commands

These commands are useful for working with Kubernetes init containers and managing pods.

---

**Deploy a pod with an init container:**

```bash
$ kubectl apply -f pod.kiada-init.yaml
```

This command deploys a pod with an init container using the configuration specified in the "pod.kiada-init.yaml" file. Init containers are executed before the main container starts and are often used for setup tasks.

**Start an interactive shell in an init container:**

```bash
$ kubectl exec -it kiada-init-slow -c init-demo -- sh
```

This command starts an interactive shell in the "init-demo" init container within the "kiada-init-slow" pod. It allows you to troubleshoot or perform tasks within the init container.

**Delete a pod:**

```bash
$ kubectl delete pod kiada
```

Use this command to delete the "kiada" pod. Deleting pods can be helpful for cleaning up resources or restarting pods with updated configurations.

**View Pod Logs:**

```bash
$ kubectl logs kiada
```

You can use this command to view the logs of the "kiada" pod, which includes logs from both the main container and any init containers.

**Describe a Pod:**

```bash
$ kubectl describe pod kiada
```

This command provides detailed information about the "kiada" pod, including its current status, events, and associated containers, including init containers.

**Force Delete a Pod:**

```bash
$ kubectl delete pod kiada --grace-period=0 --force
```

In some cases, you may need to forcefully delete a pod without waiting for graceful termination. Use this command with caution, as it terminates the pod immediately.

**List Pods in a Namespace:**

```bash
$ kubectl get pods -n [NAMESPACE]
```

Replace "[NAMESPACE]" with the desired namespace name. This command lists all pods in the specified namespace, including their status and other details.

---

These commands allow you to work with Kubernetes init containers, troubleshoot pods, and manage pod lifecycle by creating, deleting, and inspecting pods.
