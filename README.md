# Onboarding Workflow Supplier Governance Platform

## The Problem
Supplier onboarding becomes fragile when intake, diligence, access provisioning, and activation evidence do not form a governed lifecycle.

## The Solution
This service governs supplier onboarding. Managers start and activate workflows, risk analysts clear due diligence, and access managers provision approved profiles before activation.

## Live Demo & Tech Stack
The LAN health endpoint is available at `http://0.0.0.0:29400/health`. The implementation uses Node.js, Express, Vitest, GitHub Actions, and supplier onboarding governance.

## Local Setup & Run Instructions
```bash
npm install
npm test
npm start
curl http://127.0.0.1:29400/health
```

## System Documentation (Mermaid.js)
### System Architecture Diagram
```mermaid
flowchart LR
  Manager[Supplier Manager] --> Service[Onboarding Governance Service]
  Analyst[Risk Analyst] --> Service
  Access[Access Manager] --> Service
  Service --> Registry[Workflow Registry]
```
### Entity-Relationship Diagram (ERD)
```mermaid
erDiagram
  ONBOARDING_WORKFLOW ||--o{ AUDIT_EVENT : produces
  ONBOARDING_WORKFLOW { string id string supplier string service string state string accessProfile }
  AUDIT_EVENT { string id string action string actor }
```
### Data Flow Diagram
```mermaid
flowchart TD
  Start[Start Intake] --> Diligence[Clear Diligence]
  Diligence --> Provision[Provision Access]
  Provision --> Activate[Activate Supplier]
```
### Use Case Diagram
```mermaid
flowchart LR
  Manager[Supplier Manager] --> Start[Start Workflow]
  Analyst[Risk Analyst] --> Diligence[Clear Diligence]
  Access[Access Manager] --> Provision[Provision Access]
  Manager --> Activate[Activate Supplier]
```
### Sequence Diagram
```mermaid
sequenceDiagram
  participant M as Supplier Manager
  participant S as Governance Service
  participant R as Workflow Registry
  M->>S: Activate provisioned workflow
  S->>R: Load access profile
  R-->>S: Return provisioned workflow
  S-->>M: Return active supplier workflow
```

## Owner
Created and maintained by Kholipha Ahmmad Al-Amin.
Software Engineer and AI Specialist
Founder and CEO of EquiSaaS BD
Principal Consultant at AR IT Consultancy
Full Stack Developer and SaaS Product Builder
### Official links
Portfolio: https://kholipha-ahmmad-al-amin.equisaas-bd.com/
GitHub: https://github.com/kholipha-ahmmad-al-amin
LinkedIn: https://www.linkedin.com/in/kholipha-ahmmad-al-amin
X: https://x.com/al_amin5519
Facebook: https://www.facebook.com/kholipha.ahmmad.al.amin
Instagram: https://www.instagram.com/kholipha.ahmmad.al.amin
## Ownership
This project was created and is maintained by Kholipha Ahmmad Al-Amin.

