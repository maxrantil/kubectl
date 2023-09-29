# Secure Networking (SSL/TLS) Commands

These commands are useful for configuring and testing secure network connections with SSL/TLS in a Kubernetes environment.

---

**Forward ports for secure communication:**

```bash
$ kubectl port-forward kiada-ssl 8080 8443 9901
```

This command sets up port forwarding to enable secure communication. It forwards local port 8080 to the pod's port 8080, local port 8443 to the pod's port 8443, and local port 9901 to the pod's port 9901.

**Make a curl request to a locally forwarded port (secure):**

```bash
$ curl localhost:8080
```

After port forwarding, use this command to make a secure curl request to the locally forwarded port (8080).

**Make an insecure curl request to a locally forwarded port:**

```bash
$ curl https://localhost:8443 --insecure
```

This command makes an insecure curl request to the locally forwarded port (8443) by bypassing SSL/TLS certificate verification.

**Make a secure curl request to a locally forwarded port with custom CA certificate:**

```bash
$ curl https://example.com:8443 --resolve example.com:8443:127.0.0.1 --cacert kiada-ssl-proxy-0.1/example-com.crt
```

Here, you make a secure curl request to a locally forwarded port (8443) while resolving "example.com" to "127.0.0.1" and specifying a custom CA certificate ("kiada-ssl-proxy-0.1/example-com.crt") for certificate validation.

**Generate SSL/TLS Certificates:**

```bash
$ openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout example-com.key -out example-com.crt
```

Use this command to generate a self-signed SSL/TLS certificate and key pair for testing purposes. Customize the certificate details as needed.

**Create a Kubernetes Secret for SSL/TLS Certificates:**

```bash
$ kubectl create secret tls example-com-tls --cert=example-com.crt --key=example-com.key
```

This command creates a Kubernetes Secret using the SSL/TLS certificate and key pair. You can use this secret in your Kubernetes deployments to enable secure communication.

---
These commands help you configure and test secure network connections with SSL/TLS in Kubernetes, allowing you to forward ports, make secure and insecure requests, and generate SSL/TLS certificates for your applications.
