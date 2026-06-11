# Kubernetes Creation Practice

## Overview

This repository demonstrates hands-on implementation of core Kubernetes concepts and objects used to deploy, expose, scale, and secure containerized applications. The project focuses on practical experience with Kubernetes resource definitions using YAML manifests and command-line operations through `kubectl`.

The objective of this project was to gain a strong understanding of Kubernetes architecture, workload management, service exposure, and access control mechanisms commonly used in production environments.

---

## Key Features

* Created and managed Kubernetes Pods using declarative YAML manifests.
* Exposed applications internally and externally using Kubernetes Services.
* Implemented ReplicaSets to maintain desired pod availability.
* Built Deployments for declarative application rollout and updates.
* Practiced workload scaling and self-healing capabilities.
* Configured Service Accounts for workload identity management.
* Implemented Role-Based Access Control (RBAC) using Roles and RoleBindings.
* Managed Kubernetes resources using `kubectl`.
* Developed a foundational understanding of Kubernetes object relationships and cluster operations.

---

## Repository Structure

```
.
├── k8s objects and concepts/
├── kubectl/
├── my-pod.yml
├── my-service.yml
├── REPLICA-DEPLOYMENT/
│   ├── replicaset.yml
│   └── deployment.yml
└── RBAC/
    ├── service-account.yml
    ├── role.yml
    └── role-binding.yml
```

---

## Kubernetes Concepts Covered

### Workload Management

* Pods
* ReplicaSets
* Deployments
* Desired State Management
* Rolling Updates

### Networking

* Services
* Service Discovery
* Cluster Networking Basics

### Security and Access Control

* Service Accounts
* Roles
* RoleBindings
* Principle of Least Privilege
* RBAC Authorization

### Cluster Operations

* Resource Creation and Inspection
* Declarative Resource Management
* YAML-Based Configuration
* `kubectl` Commands

---

## Technologies Used

* Kubernetes
* YAML
* kubectl
* Linux Command Line

---

## Learning Outcomes

Through this project, I developed practical experience in:

* Deploying and managing containerized workloads on Kubernetes.
* Understanding how Kubernetes maintains application availability.
* Implementing access control using RBAC.
* Working with declarative infrastructure definitions.
* Operating Kubernetes resources using industry-standard tooling.

---

## How to Use

Clone the repository:

```bash
git clone https://github.com/Bikramjit2212/kubernetes-creation-practice.git
cd kubernetes-creation-practice
```

Apply Kubernetes manifests:

```bash
kubectl apply -f my-pod.yml
kubectl apply -f my-service.yml
kubectl apply -f REPLICA-DEPLOYMENT/
kubectl apply -f RBAC/
```

Verify resources:

```bash
kubectl get pods
kubectl get deployments
kubectl get replicasets
kubectl get services
kubectl get roles
kubectl get rolebindings
```

---

## Project Outcome

This project strengthened my understanding of Kubernetes fundamentals by providing hands-on experience with application deployment, scaling, service exposure, and security configuration using real Kubernetes manifests and operational workflows.
