# Sales Order System 2.0: Kubernetes Platform Configuration

This project is a spin-off from the main [Sales Order System 2.0](https://github.com/colinbut/sales-order-system-2.git) project. Whereas that project showcases the theme of __Application Development__ - this project demonstrates in particular the __Infrastructure as Code__ concept of __Platform Configuration__ and is the sister project of: [Sales Order System 2.0: Infrastructure EKS](https://github.com/colinbut/sales-order-system-2-infrastructure-eks).

For a typical application deployed onto Kubernetes you would have a set of application/platform configuration files which defines the application components as Kubernetes resources. This is what this project is all about, managing the configuration of those.

# Table of Contents

  - [Prerequisites](#prerequisites)
    - [Provision Kubernetes Cluster](#provision-kubernetes-cluster)
    - [Install NGINX Ingress Controller](#install-nginx-ingress-controller)
  - [Platform Architecture](#platform-architecture)
    - [User Service](#user-service)
    - [Customer Service](#customer-service)
    - [Order Service](#order-service)
    - [Product Service](#product-service)
      - [Configuration and Sensitive Data](#configuration--sensitive-data)
  - [Roadmap](#roadmap)

## Prerequisites

### Provision Kubernetes Cluster
Provision the Kubernetes Cluster using - [Sales Order System 2.0: Infrastructure EKS](https://github.com/colinbut/sales-order-system-2-infrastructure-eks)

### Install NGINX Ingress Controller

For this platform, I have chosen to operate a [Kubernetes Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/) and as such require an Ingress Controller to be installed.

I have chosen the [NGINX Ingress](https://kubernetes.github.io/ingress-nginx/) as I wanted to replicate the architecture as defined in the spin off project: [Sales Order System 2.0 - Application Platform](https://github.com/colinbut/sales-order-system-2-infrastructure#application-platform)

See: [NGINX Ingress on AWS](https://kubernetes.github.io/ingress-nginx/deploy/#aws) for instructions to install it.

*CAUTION  
Manually creating the NGINX Ingress will auto provision an AWS ELB that is out of control of Terraform therefore if adopting IAC then should use with caution. I've only used above method due to time contraints for this particular demo project.  

## Platform Architecture
The configured platform would look like the following:

![Platform Architecture](https://images-for-github-colinbut.s3.eu-west-2.amazonaws.com/sales-order-system-2/SalesOrderSystem-2-K8.png)

### User Service
UserService uses an in-memory embedded database (H2) hence only create 1 single pod.

### Customer Service
CustomerService is scaled to 3 replica pods which connects to the MySQL database where it is a singleton instance - managed by a `ReplicaSet` of 1.

### Order Service
Similar to CustomerService, this microservices uses 3 replica `pods` be default. Backing datastore MongoDB is a 3 replicaset cluster with 1 primary (master) and 2 secondaries (slaves). The MongoDB instance is managed by a `StatefulSet`.

### Product Service
Likewise, ProductService is also scaled to 3 replca pods with its backing Redis datastore being managed by a 3 replica cluster `StatefulSet` (similar to OrderService's MongoDB).

#### Configuration & Sensitive Data
Most microservices's configuration is injected into the pods via Environment Variables using a `Configmap` and their sensitive configs (username/passwords etc) are injected the same way using `secrets`.


## Roadmap

Future exercises include:

- Manage secrets in a secure storage mechanism such as [Vault](https://www.vaultproject.io/) or [AWS SSM Parameter Store](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter-store.html)
- Put in place Persistence Volumes (PV) & Persistence Volume Claims (PVC) for the databases (MySQL) and/or datastores (MongoDB, Redis)
- Configure HPA (Horizontal Pod Autoscaling) to dynamically elastically scale up/down the pods of the microservices


