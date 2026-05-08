# DUA Streamliner
### Intelligent System for Automated Generation of the Costa Rican Single Customs Declaration (DUA)

**Authors:** Christopher Jiménez  
**Case #1**

---

## Project Overview

The preparation of the Single Customs Declaration (DUA) in Costa Rica requires interpreting multiple heterogeneous source documents such as commercial invoices, packing lists, certificates of origin, transport documents, insurance policies, and special permits. These documents are delivered in different formats including Excel, Word, PDF, and scanned images, and they do not follow standardized structures. Manual preparation of the DUA is repetitive, error-prone, and highly dependent on expert customs knowledge, increasing operational risk, delays, and potential penalties.

DUA Streamliner proposes an intelligent automated solution capable of reading multi-format documents, extracting semantically relevant customs information using AI-based processing, mapping extracted data to the official DUA template defined by the Ministry of Finance, and generating a pre-filled Word document with confidence indicators. The system is designed following modern software architecture principles and covers frontend, backend, data modeling, security, quality assurance, cloud deployment, and observability.

The expected outcome is a complete technical design specification that enables the implementation of a scalable, secure, and maintainable system. The solution aims to significantly reduce manual workload, transform customs professionals into strategic validators, and improve the accuracy, efficiency, and reliability of DUA generation.

---

# 1. Frontend Design

## 1.1 Tech Stack

- Application type:
  - Cloud-based SaaS Web Application

- Web framework:
  - React 19.2

- Web server:
  - Node.js 21 (Express 4.19.x)

- Coding language:
  - TypeScript 5.9.3

- Unit testing framework:
  - Jest 30.2.0

- Data validation framework:
  - Yup 1.x
  - React Hook Form 7.x

- Code prettier framework:
  - Prettier 3.2.x

- Code style framework:
  - ESLint 9.x
  - Airbnb TypeScript Config 19.x

- Integration testing tools:
  - Playwright 1.58.2

- Cloud service:
  - Microsoft Azure

- Hosted services within the cloud service:
  - Azure App Service
  - Azure Static Web Apps
  - Azure Blob Storage
  - Azure Key Vault
  - Azure Application Insights

- Code repositories service:
  - GitHub

- Code automation task tool:
  - npm scripts
  - GitHub Actions

- CI CD pipelines technology:
  - GitHub Actions Workflows (YAML-based pipelines)

- Environments:
  - Development
  - QA
  - Staging
  - Production

- Environment deployment tools:
  - Azure App Service Deployment Slots
  - Azure Resource Groups
  - GitHub Actions Deployment Jobs

- Observability framework:
  - Azure Application Insights
  - Sentry 7.x
  - OpenTelemetry

---

## 1.2 UX UI Analysis

### Usability Attributes

- Simplicity
- Clarity
- Feedback
- Efficiency
- Error Prevention
- Visibility of System Status
- Learnability
- Consistency

---

### Core Business Process

1. User logs into the system.
2. User uploads a folder containing source documents.
3. System validates files.
4. System classifies documents.
5. System processes documents (OCR + semantic extraction).
6. Data is mapped to DUA template.
7. Confidence levels are calculated.
8. DUA document is generated.
9. User reviews the document.
10. User downloads final DUA.

---

### Wireframes

#### Login Screen

```
Email: [__________]
Password: [_______]

[ Login ]
```

---

#### Dashboard

```
[ New DUA Process ]

Recent Processes:
- Completed
- Processing
- Error
```

---

#### Upload Screen

```
Drag & Drop Folder

Supported:
- Excel
- Word
- PDF
- Images

[ Upload ]
```

---

#### Processing Screen

```
Processing...

✔ Validation
✔ Classification
[ ] OCR
[ ] Extraction

Progress: 60%
```

---

#### Review Screen

```
Importer: (Green)
Supplier: (Yellow)
Origin: (Red)

Legend:
Green = High
Yellow = Medium
Red = Review
```

---

#### UX Validation Evidence

- Users understood workflow without guidance
- Progress feedback increased trust
- Color coding was intuitive

---

## 1.3 Component Design Strategy

- Component-based architecture using React functional components
- Reusable UI components (buttons, forms, modals)
- Centralized styling using global theme configuration
- Responsive design using flexible layouts
- Internationalization-ready structure
- Separation between presentation and logic
- Form handling using React Hook Form
- Validation using Yup schemas

---

## 1.4 Security

- Authentication:
  - Azure Active Directory (OAuth 2.0 / OpenID Connect)

- Authorization:
  - Role-Based Access Control (RBAC)

- Session Management:
  - JWT tokens

- Multi-Factor Authentication:
  - Supported via Azure AD

- Token Handling:
  - Access tokens stored in memory
  - Refresh tokens handled securely

- Sensitive Data Management:
  - Azure Key Vault

- Environment Variables:
  - Managed via Azure configuration and GitHub Secrets

---

## 1.5 Layered Design

- Presentation Layer
- Components Layer
- State Management Layer
- Service Layer
- API Communication Layer
- Security Layer

---

## 1.6 Design Patterns

The system architecture follows multiple software design patterns to ensure scalability, maintainability, extensibility, and separation of concerns.

### Builder Pattern

The Builder Pattern is used to construct different document processors and document generation pipelines.

This pattern allows flexible creation of processors for multiple supported formats:

- DOCX Processor
- XLSX Processor
- PDF Processor
- JPG Processor
- PNG Processor

Each processor follows a standardized construction workflow while allowing format-specific implementations.

---

### Strategy Pattern

The Strategy Pattern is implemented to dynamically select the appropriate processing strategy depending on the uploaded file type.

Examples:
- OCR extraction strategy
- Semantic parsing strategy
- Validation strategy
- File classification strategy

This pattern reduces coupling and allows future support for additional formats without modifying the core processing workflow.

The Strategy Pattern is also used to create the different document processors such as:
- Word Processor
- XLSX Processor
- PDF Processor
- JPG Processor
- PNG Processor

---

### Observer Pattern

The Observer Pattern is used within the `NotificationService`.

Subscribers listen for important backend events such as:
- Upload completed
- OCR completed
- Extraction failed
- DUA generated
- Validation warnings

This allows asynchronous notification handling and decouples event producers from consumers.

NotificationService subscriptions work using the Observer Pattern architecture.

---

### Adapter Pattern

The Adapter Pattern is used to abstract output formatting and document writing logic.

`FormatAdapters` transform extracted semantic information into standardized document structures.

Concrete format implementations include:
- Paragraph
- Bullets
- Table
- Label
- Amount

This architecture enables future support for additional export formats without affecting business logic.

---

### Singleton Pattern

The Singleton Pattern is used for globally shared services and utilities to ensure centralized state consistency and optimized resource usage.

Singleton services include:
- ExceptionHandling
- DocumentParsers
- Utils
- StateManagement
- API Clients
- Settings classes

---

# Backend Design

## Technology Stack

- Architecture style:
  - REST API
  - HTTPS communication

- API Gateway:
  - Azure API Management

- Hosting platform:
  - Azure App Service

- API standard:
  - OpenAPI Specification (Swagger)

- Backend language:
  - C#
  - .NET 9
  - ASP.NET Core

- Repository architecture:
  - Monorepo architecture

- Backend folder:
  - `/duabusiness`

- Communication style:
  - Service-oriented modular architecture
  - Lightweight services instead of fully distributed microservices

- Asynchronous operations and notifications:
  - Azure Notification Hubs

- Cloud provider:
  - Microsoft Azure

---

## Backend Layered Design

The backend follows a layered architecture design:

- API Layer
- Authentication Layer
- Application Services Layer
- Business Logic Layer
- AI Processing Layer
- Document Processing Layer
- Persistence Layer
- Integration Layer
- Storage Layer
- Observability Layer

---

## Security

Frontend and backend security configurations are designed to work in synchronization.

### Communication Security

- HTTPS enforced for all environments
- TLS 1.3 required
- HSTS enabled

---

### Encryption

- Database encryption algorithm:
  - AES-256 encryption at rest

- Secrets management:
  - Azure Key Vault

- Authentication tokens:
  - JWT tokens with expiration and refresh strategy

---

### Payload Restrictions

General API payload limits:

- Standard endpoints:
  - Maximum payload size: 25 MB

- File upload endpoints:
  - Maximum payload size: 250 MB

Streaming upload processing is required to avoid memory overconsumption.

---

### Rate Limiting

- Maximum concurrent connections per client:
  - 100 concurrent requests

- Rate limiting policy:
  - Configured through Azure API Management

- DDoS protection:
  - Azure native protection services

---

### Data Retention Policy

- Production data retention:
  - 90 days active storage

- Archive strategy:
  - Automatic migration to Azure Archive Storage after 90 days

- Audit logs retention:
  - 1 year

---

# Observability

Frontend and backend observability configurations are integrated.

## Registered Events

The platform logs the following events:

- User login attempts
- Authentication failures
- File uploads
- File validation failures
- OCR processing results
- Semantic extraction events
- DUA generation events
- API failures
- Infrastructure exceptions
- Processing duration metrics
- Confidence score generation
- Notification delivery events

---

## Observability Platforms

- Azure Application Insights
- OpenTelemetry
- Azure Monitor
- Sentry

---

## Analytics Dashboards

Dashboards and monitoring visualizations are generated using:

- Azure Dashboard
- Grafana

---

# Infrastructure (DevOps)

## CI/CD Automation

- GitHub Actions
- YAML-based workflows

---

## Deployment Strategy

### Development Environment

- Azure App Service Deployment Slots

### Staging Environment

- Terraform-managed Azure infrastructure

### Production Environment

- Terraform-managed Azure infrastructure

Infrastructure provisioning is fully Infrastructure-as-Code (IaC).

---

# Availability

## Availability Target

- Target uptime:
  - 99.99%

Maximum estimated downtime per year:
- Approximately 52 minutes annually

---

## Recovery Strategy

All critical infrastructure components must be evaluated for Single Points of Failure (SPOF).

For every infrastructure component:
- Recovery guarantees must be documented
- Native Azure SLA must be verified
- Redundancy strategies must be specified

Examples:
- Geo-redundant storage
- Multi-zone deployment
- Automated backup policies
- Health probes and auto-restart mechanisms

Any service that cannot natively achieve the required uptime target must include additional recovery and redundancy mechanisms.

---

# Scalability

The following architectural components scale according to request volume:

- API Gateway instances
- Azure App Service instances
- File processing workers
- OCR processing queues
- Notification services
- Database throughput
- Blob storage operations

Horizontal scaling is prioritized over vertical scaling whenever possible.

---

# Backend Key Workflows

## Upload Files to Generate DUA

1. User uploads files from the frontend.
2. Backend receives file metadata.
3. Backend opens streaming transfer for each file.
4. Files are processed sequentially in raw binary format.
5. Files are stored in Azure Blob Storage.
6. File references are mapped into the database.
7. Validation service verifies supported formats.
8. Classification service identifies document type.
9. OCR service extracts textual content.
10. Semantic extraction service identifies customs information.
11. Data mapping service transforms extracted information into DUA structure.
12. Confidence calculation service evaluates extraction reliability.
13. DUA generation service produces final document.
14. Notification service updates frontend status.
15. User downloads generated DUA document.

---

## Setup DUA Template Workflow

1. Administrator uploads official DUA template.
2. Backend validates template structure.
3. Template metadata is registered.
4. Template fields are mapped to extraction entities.
5. Template versioning is stored.
6. Validation rules are associated with template sections.
7. Template becomes available for generation workflows.

---

# Architecture Diagrams

Architecture diagrams follow the C4 Model standard.

Included diagrams:
- Context Diagram
- Container Diagram
- Code Diagram

The Components Diagram is intentionally excluded for this project scope.

Reference material:
- Week #6
- Week #7

---

# Design Considerations

- System configurations, parameters, and policies must be fully documented and maintained within the source code.
- Resource allocations including memory, server specifications, networking configurations, and load balancing parameters must be documented.
- Algorithm selection and configuration parameters used in business logic and AI extraction must be documented.
- Agent prototypes and AI orchestration flows must be defined.
- Interfaces, proxies, and external integration points must be documented.
- Architectural decisions must maintain traceability and version control.

---

# Source Code

A specialized AI agent will generate the backend project skeleton based on this technical specification.

The agent must:
- Generate folder structures
- Generate interfaces
- Generate DTOs
- Generate service contracts
- Generate controller skeletons
- Generate configuration files

The agent must NOT implement production business logic.

The backend directory structure must align with the monorepo architecture.

Example backend structure:

```text
/duabusiness
  /api
  /application
  /domain
  /infrastructure
  /integrations
  /workers
  /storage
  /observability
  /tests
```

Key folders and primary classes must be referenced throughout this README documentation.

## 1.7 Project Scaffold

The frontend project structure is generated based on the defined architecture and design principles.

```
/src
  /api
  /components
  /config
  /hooks
  /pages
  /services
  /store
  /styles
  /types
  /utils
```

### Folder Description

- api:
  API client configuration and HTTP request handling.

- components:
  Reusable UI components such as buttons, inputs, modals, and layout elements.

- config:
  Application configuration (environment variables mapping, constants, endpoints).

- hooks:
  Custom React hooks for state management, authentication handling, and reusable logic.

- pages:
  Application views representing main screens (Dashboard, Upload, Processing, Review).

- services:
  Business logic abstraction and interaction with backend services.

- store:
  Global state management (application state, user session, processing status).

- styles:
  Global styles, themes, and design tokens for consistent UI branding.

- types:
  TypeScript interfaces and type definitions used across the application.

- utils:
  Helper functions and shared utilities (formatting, validation helpers).

---

The scaffold is available in the repository:

- /src folder: ./src

