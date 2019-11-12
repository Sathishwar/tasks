## Prerequisites

- Kubernetes 1.8+ with Beta APIs enabled
- PV provisioner support in the underlying infrastructure

# Redis Deployment

```bash
$ helm install --name redis redis-ha -f redis-ha/values.yaml
```
For More info - [click here](https://github.com/Sathishwar/tasks/redis-ha/README.MD)

# Application Deployment

1.Create deployment with kubectl deployment

```bash
$ kubectl create -f deployment.yaml
```
2. Create Service with type as Loadbalancer

```bash
$ kubectl create -f svc.yaml
```
3. Once app successfully running. Get the application IP

```bash
$ kubectl get svc <svc-name> --output jsonpath='{.status.loadBalancer.ingress[0].ip}'
```