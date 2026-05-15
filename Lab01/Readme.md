# CST8918 Lab 01 - Weather App Kubernetes Deployment

## Student Information

**Name:** Khalid Amchat  

**Student ID**: 041125350

**Semester**: Spring 2026

**Course:** CST8918-DevOps: Infrastructure as Code  

---
## Overview

This repository contains the Kubernetes deployment files and final screenshot for **Lab 01** of CST8918 - DevOps: Infrastructure as Code.

The lab demonstrates how to containerize a weather web application using Docker and deploy it to a local Kubernetes cluster.

The original application code is provided in the lab repository:

[Lab Repository-cst8918-lab01](https://github.com/KhalidAlgonquin/cst8918-lab01)

---

## Repository Contents

```text
.
├── README.md
├── screenshot.png
└── k8s/
    ├── a01_namespace.yaml
    ├── a01_deployment.yaml
    └── a01_service.yaml
```

---

## Kubernetes Resources

The `k8s` folder contains the required Kubernetes configuration files:

| File | Description |
|---|---|
| [a01_namespace.yaml](k8s/a01_namespace.yaml) | Creates the `cst8918` namespace |
| [a01_deployment.yaml](k8s/a01_deployment.yaml) | Deploys the weather application with 2 replicas |
| [a01_service.yaml](k8s/a01_service.yaml) | Exposes the application using a LoadBalancer service |

---

## Secret Configuration

The OpenWeather API key was stored using a Kubernetes Secret:

```bash
kubectl create secret generic weather \
  --from-literal=api-key="YOUR_API_KEY" \
  -n cst8918
```

The API key is not included in this repository for security reasons.

---

## Deployment Commands

```bash
kubectl apply -f ./k8s/a01_namespace.yaml

kubectl apply -f ./k8s/a01_deployment.yaml -n cst8918

kubectl apply -f ./k8s/a01_service.yaml -n cst8918
```

---

## Verification Commands

```bash
kubectl get namespaces
kubectl get pods -n cst8918
kubectl get services -n cst8918
kubectl get secrets -n cst8918
```

---

## Screenshot

Final deployment screenshot:

![Lab 01 Screenshot](./screenshot-lab01.png)

---
