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

- Singleton (Auth Service)
- Factory (Document processors)
- Observer (State updates)
- Strategy (File processing logic)
- Adapter (API integration)
- Facade (Service abstraction)
- Middleware (Security handling)
- Publisher-Subscriber (Event handling)

---

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

