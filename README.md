# Sales Order System 2.0: Kubernetes Platform Configuration

This project is a spin-off from the main [Sales Order System 2.0](https://github.com/colinbut/sales-order-system-2.git) project. Whereas that project showcases the theme of __Application Development__ - this project demonstrates in particular the __Infrastructure as Code__ concept of __Platform Configuration__ and is the sister project of: [Sales Order System 2.0: Infrastructure EKS](https://github.com/colinbut/sales-order-system-2-infrastructure-eks).

For a typical application deployed onto Kubernetes you would have a set of application/platform configuration files which defines the application components as Kubernetes resources. This is what this project is all about, managing the configuration of those.

# Table of Contents

  - [Prerequisites](#prerequisites)
    - [Provision Kubernetes Cluster](#provision-kubernetes-cluster)
    - [Install NGINX Ingress Controller](#install-nginx-ingress-controller)

## Prerequisites

### Provision Kubernetes Cluster
Provision the Kubernetes Cluster using - [Sales Order System 2.0: Infrastructure EKS](https://github.com/colinbut/sales-order-system-2-infrastructure-eks)

### Install NGINX Ingress Controller

For this platform, I have chosen to operate a [Kubernetes Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/) and as such require an Ingress Controller to be installed.

I have chosen the [NGINX Ingress](https://kubernetes.github.io/ingress-nginx/) as I wanted to replicate the architecture as defined in the spin off project: [Sales Order System 2.0 - Application Platform](https://github.com/colinbut/sales-order-system-2-infrastructure#application-platform)

See: [NGINX Ingress on AWS](https://kubernetes.github.io/ingress-nginx/deploy/#aws) for instructions to install it.


