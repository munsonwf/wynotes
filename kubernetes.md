# Kubernetes

Kubernetes is a container orchistration platform.

## Core Concepts

### Deployment

Set things like:

- replicas
- Update strategy: rolling update, ect.
- environment variables,
- Image location
- Healthcheck and liveliness probe endpoints

### Pods

Like a pod of whales, one or more containers that should be treated as a single application. A pod encapsulates application containers, storage resrouces, a unique network Id, and configuration on how to run the containers.

### Service

Logical set of pods that acts as a gateway for the client to send requests to the pods. Pods are volatile in k8s. The replication controller may kill pods. Service abstracts the finding of the physical pods and acts as a gateway.

Set configurations like what port the service listens on and what port that maps to the port the container is listening on.

### Namespace

Analgous to an Amazon VPC, a namspace is a virtual cluster. A physical cluster can run multiple namespaces (virtual clusters) to isolate components, projects, or secure access.

## kubctl

`kubectl` is a command line interface tool that interacts with the `kube-apiserver` (in the master node).

Add your EKS cluster to your local kubeconfig

```bash
# add EKS cluster to local kubeconfig
$ aws eks --region us-east-1 update-kubeconfig --name cluster-name-in-eks-ce548264
```

Namespaces

```bash
kubectl create namespace finance-qa
kubectl delete namepsaces finance-qa # note extra "s"
```

### Creating Resrouces

```bash
$ kubectl apply -f ./deploy-dev.yaml        # create resrouce from file
$ kubectl apply -f ./dev.yaml ./prod.yaml   # from two files
$ kubectl apply -f ./dir                    # from an entire directory

```

### Viewing Created Resrouces

```bash
$ kubectl get services
$ kubectl get pods -A       # get pods all namespaces
$ kubectl get pods -o wide      # list pods with more details
$ kubectl get deployment dev-dep    # get deployment dev-dep
$ kubectl get pods
$ kubectl get pod ui-pod -o yaml    # get ui-pod's YAML
$ kubectl get  --export #list pod without cluster specific information

```

### Kubectx & Kubens

Kubectx is a command line tool to help you quickly swtich clusters. Use Kubens for namespaces.

Install kubectx here: https://github.com/ahmetb/kubectx

Use kubectl here:

```bash
USAGE:
  kubectx                       : list the contexts
  kubectx <NAME>                : switch to context <NAME>
  kubectx -                     : switch to the previous context
  kubectx <NEW_NAME>=<NAME>     : rename context <NAME> to <NEW_NAME>
  kubectx <NEW_NAME>=.          : rename current-context to <NEW_NAME>
  kubectx -d <NAME> [<NAME...>] : delete context <NAME> ('.' for current-context)
                                  (this command won't delete the user/cluster entry
                                  that is used by the context)
```
