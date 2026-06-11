# ☸️ Kubernetes Creation Practice

A hands-on Kubernetes practice repository demonstrating the creation and management of fundamental Kubernetes resources including Pods, Services, ReplicaSets, Deployments, Service Accounts, and Role-Based Access Control (RBAC).

This repository serves as a practical learning project to understand how Kubernetes workloads are deployed, exposed, scaled, and secured within a cluster.

---

## 📌 Project Overview

This project focuses on implementing essential Kubernetes concepts through YAML manifests.

The repository covers:

* Creating standalone Pods.
* Exposing applications using Services.
* Managing multiple Pod replicas with ReplicaSets.
* Deploying applications using Deployments.
* Configuring Service Accounts.
* Implementing Role-Based Access Control (RBAC).
* Associating Deployments with custom Service Accounts.

These exercises provide foundational experience required for Kubernetes administration and DevOps engineering roles.

---

## 🏗 Repository Structure

```
kubernetes-creation-practice-main/
├── my-pod.yml
├── my-service.yml
├── k8s objects and concepts/
│   ├── REPLICA-DEPLOYMENT/
│   │   ├── deployment.yml
│   │   └── replicaset.yml
│   └── RBAC/
│       ├── role.yml
│       ├── role-binding.yml
│       └── service-account.yml
└── README.md
```

---

## 🚀 Kubernetes Resources Implemented

### 1. Pod Creation

**File:**

```
my-pod.yml
```

Creates a standalone NGINX Pod.

#### Features

* Uses Kubernetes Pod resource.
* Deploys an NGINX container.
* Pulls image:

```
nginx:1.14.2
```

* Exposes container port:

```
80
```

#### Deploy

```bash
kubectl apply -f my-pod.yml
```

#### Verify

```bash
kubectl get pods
kubectl describe pod nginx
```

---

### 2. Service Creation

**File:**

```
my-service.yml
```

Exposes the NGINX Pod externally using a NodePort Service.

#### Features

* Service Type:

```
NodePort
```

* Selects Pods using label:

```yaml
app: nginx
```

* Service Port:

```
80
```

* Target Port:

```
80
```

#### Deploy

```bash
kubectl apply -f my-service.yml
```

#### Verify

```bash
kubectl get svc
```

---

### 3. ReplicaSet

**File:**

```
REPLICA-DEPLOYMENT/replicaset.yml
```

Demonstrates manual Pod replication using ReplicaSets.

#### Features

* Maintains:

```
3 replicas
```

* Automatically recreates failed Pods.
* Uses label selectors to manage Pods.
* Deploys NGINX containers.

#### Deploy

```bash
kubectl apply -f replicaset.yml
```

#### Verify

```bash
kubectl get rs
kubectl get pods
```

---

### 4. Deployment

**File:**

```
REPLICA-DEPLOYMENT/deployment.yml
```

Implements declarative application deployment.

#### Features

* Creates:

```
3 NGINX replicas
```

* Uses image:

```
nginx:1.16.1
```

* Supports rolling updates.
* Includes change-cause annotation:

```yaml
kubernetes.io/change-cause
```

* Associates Pods with a custom Service Account.

#### Deploy

```bash
kubectl apply -f deployment.yml
```

#### Verify

```bash
kubectl get deployments
kubectl rollout history deployment nginx-deployment
```

---

## 🔐 RBAC Implementation

The repository demonstrates Kubernetes Role-Based Access Control.

### Service Account

**File:**

```
RBAC/service-account.yml
```

Creates a custom Service Account:

```
dev-user
```

Deployments can use this account instead of the default Service Account.

Deploy:

```bash
kubectl apply -f service-account.yml
```

---

### Role

**File:**

```
RBAC/role.yml
```

Defines permissions for the Service Account.

Allowed resources:

* Pods
* Secrets

Allowed actions:

* get
* list
* watch

Example rule:

```yaml
resources:
  - pods
  - secrets

verbs:
  - get
  - list
  - watch
```

Deploy:

```bash
kubectl apply -f role.yml
```

---

### RoleBinding

**File:**

```
RBAC/role-binding.yml
```

Associates the Role with the Service Account.

Relationship:

```
ServiceAccount
        ↓
RoleBinding
        ↓
Role
```

This grants the `dev-user` Service Account the permissions defined in the Role.

Deploy:

```bash
kubectl apply -f role-binding.yml
```

---

## 📋 Deployment Order

Apply the manifests in the following sequence:

```bash
# Pod
kubectl apply -f my-pod.yml

# Service
kubectl apply -f my-service.yml

# RBAC Components
kubectl apply -f "k8s objects and concepts/RBAC/service-account.yml"
kubectl apply -f "k8s objects and concepts/RBAC/role.yml"
kubectl apply -f "k8s objects and concepts/RBAC/role-binding.yml"

# ReplicaSet
kubectl apply -f "k8s objects and concepts/REPLICA-DEPLOYMENT/replicaset.yml"

# Deployment
kubectl apply -f "k8s objects and concepts/REPLICA-DEPLOYMENT/deployment.yml"
```

---

## 🔍 Useful Verification Commands

### View Resources

```bash
kubectl get pods
kubectl get svc
kubectl get rs
kubectl get deployments
kubectl get sa
kubectl get roles
kubectl get rolebindings
```

### Describe Resources

```bash
kubectl describe pod nginx
kubectl describe deployment nginx-deployment
kubectl describe role dev-user
kubectl describe rolebinding dev-role-binding
```

### Rollout Commands

```bash
kubectl rollout history deployment nginx-deployment

kubectl rollout status deployment nginx-deployment
```

---

## 🧠 Key Kubernetes Concepts Practiced

* Pods
* Labels and Selectors
* Services
* NodePort Exposure
* ReplicaSets
* Deployments
* Rolling Updates
* Service Accounts
* RBAC
* Roles
* RoleBindings
* Declarative Infrastructure
* YAML-based Resource Definitions

---

## 🎯 Learning Outcomes

By completing this project, gaining practical experience with:

* Creating Kubernetes workloads.
* Exposing applications inside and outside the cluster.
* Scaling applications using ReplicaSets and Deployments.
* Managing application identities using Service Accounts.
* Implementing least-privilege access controls with RBAC.
* Using kubectl to deploy and inspect Kubernetes resources.


---

# 👨‍💻 Author

**Bikramjit Roy**

DevOps & Cloud Engineering Enthusiast passionate about automation, CI/CD, cloud-native practices, and building reliable software delivery pipelines.

GitHub:
https://github.com/Bikramjit2212

---

## ⭐ If you found this project useful, consider giving it a star.
