# Kubernetes

> Kubernetes is a portable, extensible, open source platform for managing containerized
> workloads and services.

## Components

When you deploy Kubernetes, you get a cluster.

A cluster kubernetes consist of a set of nodes and control plane(s).

- Node: host the Pods that are the components of the application workload
- Control plane: manages the nodes and the Pods in the cluster

![The components of a Kubernetes cluster](./docs//images/components-of-kubernetes.svg)

### Control Plane Components

Control plane components can be run on any machine in the cluster. However, 
for simplicity, set up scripts typically start all control plane components
on the same machine, and do not run user containers on this machine.

#### kube-apiserver

The API server exposes the Kubernetes API. It's the front end fo the Kubernetes
control plane.

kube-apiserver is designed to scale horizontally.

#### etcd

Consistent and highly-available key value store used as Kubernetes' backing store
for all cluster data.

#### kube-scheduler

It watches for newly created Pods with no assigned node, and selects a node for them
to run on.

#### kube-controller-manager

It runs controller processes.

There are many different types of controllers. Some examples of them are:

- Node controller: responsible for noticing and responding when nodes go down
- Job controller: watches for job objects that represent one-of tasks, then creates
  Pods to run those tasks to completion
- EndpointSlice controller: populates EndpointSlice objects (to provide a link between
  services and pods)
- ServiceAccount controller: create default ServiceAccount for new namespaces.

#### cloud-controller-manager

It embeds cloud-specific control logic.

The following controllers can have cloud provider dependencies:

- Node controller: for checking the cloud provider to determine if a node has been deleted
- Route controller: for setting up routes in the underlying cloud infrastructure
- Service controller: for creating, updating and deleting cloud provider load balancers
