---
options:
  implicit_slide_ends: true

title: Kubernetes meets Rust

author: Shawn Wang @ TOOCON 2402

---

# Outline
 
* What is Kubernetes?
  * Some Rust Kubernetes utilities
* Why Rust is good for Kubernetes? (kube.rs)
* Rust for other parts of Kubernetes.

<!-- end_slide -->

# kubernetes overview


* k8s - **container orchestration engine** [](https://kubernetes.io/docs)
  - automating deployment / scaling
  - management containerized applications

```
      ┌┬─────────────────────────┬─┬────┬────────────┐
      ││  Control Plane          │ │Node│kube-proxy┌─┴─────┐
      ││   ┌──────────┐          │ │   ┌┴──────┬─┬─│Network│
      ││   │  etcd    │          │ │   │kubelet│ │ └─┬──.──┘
      ││   └──────────┘          │ └───┴────┬──┴─┘   │  .. 
─────┐││             ┌────── ◄───┼┬─────────┘        │┌─.───
Admin├┼┼─────────────►  Api  │   ││┌─────────────┐   ││Users
kubectl│             └───────┘   │└┤ Node        │   │└─────
─────┘││   ┌────────────────┐    │ │   ┌─────────┴─┐ │
      ││   │ kube-scheduler │    │ └───┤ Node      │ │
      ││┌──┴────────────────┴───┐│     └───────────┘ │
      │││kube-controller-manager││                   │
      └┴┴───────────────────────┴┴───────────────────┘
```

<!-- end_slide -->

Componenents
---

<!-- column_layout: [1, 1] -->
<!-- column: 0 -->
## Control Plane
- kube-scheduler - assigns Pods to Nodes
- kube-controller-manager
- etcd
- kube-api

## Node
- kubelet - kube agent
- kube-proxy
<!-- column: 1 -->
## Admin

- kubectl

<!-- end_slide -->

# k8s quick start

- [](https://kind.sigs.k8s.io/)
- prepare docker or podman
  - dnf/apt install podman
- kind 
  - kind create cluster
- kubectl
- prepare kubecfg
  - $KUBECONFIG
  - kubectl config view
  - kubectl config view --raw

<!-- end_slide -->

# Objects In Kubernetes

- Object spec and status 

API / Resource

watch



<!-- end_slide -->

kubectl / restful

<!-- end_slide -->

## yaml

```
❯ kubectl get pod nginx-deployment-848dd6cfb5-2qnjk -o yaml
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: "2024-01-28T13:30:15Z"
  generateName: nginx-deployment-848dd6cfb5-
  labels:
    app: nginx
    pod-template-hash: 848dd6cfb5
  name: nginx-deployment-848dd6cfb5-2qnjk
  namespace: default
spec:
  containers:
  - image: nginx:1.16.1
status:
  conditions:
...
```

<!-- end_slide -->

## Why Rust

- no gc / safe
- cargo
- cli
- kube.rs

<!-- end_slide -->                                                                                                                                     

# my shell env for k8s

- starship - cross shell prompt
- kbs
- kdash
- k8s-insider


<!-- end_slide -->


- kube.rs
  - https://tembo.io/blog/tembo-stacks-intro/
  - https://github.com/stackabletech
  - https://openobserve.ai/blog/understanding-kubernetes-resource-management-using-rust-in-containers/
  - https://medium.com/the-polyglot-programmer/rust-on-kubernetes-a-beginners-guide-to-developing-and-deploying-rust-applications-825bd7b5df66
- sidecar
  - Linkerd
    linkerd2 (Linkerd is a service mesh for Kubernetes.)
- utils
- kubectl plugins
- container related projects

<!-- end_slide -->

mirrord

<!-- end_slide -->


Stackable

helm related

Qovery - Enable Developers Self-Service:  Terraform, Helm, Kubectl, and Docker




<!-- end_slide -->

kubert

<!-- end_slide -->

# Linkerd

SBTB 2023: Alex Leong, Five Years of Cloud Native Rust.
- kubert

# krustlet/krator
Leveraging State Machines to Build Operators in Rust -
 Kevin Flansburg, Moose Consulting


<!-- end_slide -->

# kube.rs

- core Rust ecosystem for building applications against Kubernetes.
- accepted to CNCF on November 16, 2021 at the Sandbox maturity level ...



conmon-rs

<!-- end_slide -->

# hello

metrics -> prometheus
telemetry -> OpenTelemetry

<!-- end_slide -->

## sidecar

- Linkerd

<!-- end_slide -->

## kubectl plugins
- kubectl-watch




<!-- end_slide -->
# Rust for other parts of Kubernetes.

* container / vmm
* wasm


<!-- end_slide -->

k8sfwd
k8s-insider

kubetui
kdash
kubectl-view-allocations

kubeconfig-bikeshed / kbs
kubesess
kubie

krew-wasm
krew-wasm-plugin-sdk-rust

ksnotify
