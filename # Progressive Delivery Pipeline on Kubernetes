# Kubernetes Progressive Delivery Pipeline

A production-style release workflow demonstrating safe application rollout using Kubernetes canary deployment and automated CI/CD.

The project focuses on deployment reliability and controlled failure exposure rather than application complexity.

## Architecture

### System Flow

A code change follows this lifecycle:

Developer → Source Control → CI Pipeline → Container Image → Kubernetes → Users

The application logic is intentionally minimal.  
The objective of this project is to demonstrate controlled release behaviour rather than feature complexity.

---

### Component Roles

Service (Go)  
Provides a minimal HTTP server exposing `/` and `/healthz` endpoints used for traffic eligibility checks.

Container (Docker)  
Packages the application into an immutable runtime artifact ensuring identical execution across environments.

CI/CD Pipeline (Jenkins)  
Automatically builds, tests and publishes the container image after a change is introduced.

Orchestrator (Kubernetes)  
Maintains desired state, schedules instances and manages rollout behaviour.

Release Strategy (Canary Deployment)  
Introduces a new version gradually while the previous version continues serving users.

---

### Deployment Behaviour

1. A new version is deployed alongside the existing version
2. Kubernetes checks instance readiness using health probes
3. Traffic is allowed only to healthy instances
4. A small percentage of requests reach the new version
5. If stable, rollout continues
6. If unstable, rollback occurs

### System Flow

A code change follows this lifecycle:

Developer → Source Control → CI Pipeline → Container Image → Kubernetes → Users

The application logic is intentionally minimal.  
The objective of this project is to demonstrate controlled release behaviour rather than feature complexity.

---

### Component Roles

Service (Go)  
Provides a minimal HTTP server exposing `/` and `/healthz` endpoints used for traffic eligibility checks.

Container (Docker)  
Packages the application into an immutable runtime artifact ensuring identical execution across environments.

CI/CD Pipeline (Jenkins)  
Automatically builds, tests and publishes the container image after a change is introduced.

Orchestrator (Kubernetes)  
Maintains desired state, schedules instances and manages rollout behaviour.

Release Strategy (Canary Deployment)  
Introduces a new version gradually while the previous version continues serving users.

---

### Deployment Behaviour

1. A new version is deployed alongside the existing version
2. Kubernetes checks instance readiness using health probes
3. Traffic is allowed only to healthy instances
4. A small percentage of requests reach the new version
5. If stable, rollout continues
6. If unstable, rollback occurs

## Reliability Controls

This system focuses on reducing deployment risk rather than simply automating deployment.

Readiness Probes  
Traffic is routed only to instances that successfully pass health checks.

Rolling Updates  
Existing instances remain active while new instances start, avoiding downtime.

Canary Rollout  
Only a subset of users receive the new version during validation.

Automatic Rollback  
Failed instances are removed from service automatically.

Resource Limits  
CPU and memory constraints prevent a faulty container from affecting the node.

## Operational Workflow

Build the service container image  
Deploy manifests to the cluster  
Observe rollout status using pod readiness  
Introduce a new application version  
Verify gradual traffic shift to updated instances  
Confirm stable rollout completion

## Observed Behaviour

During deployment, both old and new versions run simultaneously.

New instances do not receive traffic until health checks pass.

A portion of requests are served by the new version during rollout.

If a container fails readiness checks, traffic continues to flow to stable instances.

Rollout completes only after all instances become healthy.


## Engineering Objective

Modern outages often occur during software releases rather than normal operation.

This project demonstrates a deployment strategy that limits user impact during updates by validating new versions before full exposure.

The goal is to reduce deployment blast radius while maintaining service availability.
