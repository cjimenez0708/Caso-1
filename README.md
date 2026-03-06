# DUA Streamliner
### Intelligent System for Automated Generation of the Costa Rican Single Customs Declaration (DUA)

**Authors:** Christopher Jiménez    
**Case #1**

## Project Overview

The preparation of the Single Customs Declaration (DUA) in Costa Rica requires interpreting multiple heterogeneous source documents such as commercial invoices, packing lists, certificates of origin, transport documents, insurance policies, and special permits. These documents are delivered in different formats including Excel, Word, PDF, and scanned images, and they do not follow standardized structures. Manual preparation of the DUA is repetitive, error-prone, and highly dependent on expert customs knowledge, increasing operational risk, delays, and potential penalties.

DUA Streamliner proposes an intelligent automated solution capable of reading multi-format documents, extracting semantically relevant customs information using AI-based processing, mapping extracted data to the official DUA template defined by the Ministry of Finance, and generating a pre-filled Word document with confidence indicators. The system is designed following modern software architecture principles and covers frontend, backend, data modeling, security, quality assurance, cloud deployment, and observability.

The expected outcome is a complete technical design specification that enables the implementation of a scalable, secure, and maintainable system. The solution aims to significantly reduce manual workload, transform customs professionals into strategic validators, and improve the accuracy, efficiency, and reliability of DUA generation.

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

## 1.2 UX UI Analysis

### Core Business Process

The system is designed to automate the generation of the Costa Rican Customs Single Administrative Document (DUA) from multiple heterogeneous input files.

The core business process follows these steps:

1. The user accesses the web application through the browser.
2. The user uploads a folder containing multiple source documents (Excel, Word, PDF, and images).
3. The system validates each uploaded file to ensure the format is supported and that the file is not empty or corrupted.
4. The system classifies the documents according to their type and content.
5. The system processes the documents using OCR and semantic extraction to identify relevant customs information such as importer, supplier, goods description, values, incoterms, and transportation data.
6. Extracted information is normalized and mapped to the official DUA template structure.
7. The system calculates validation confidence levels for the extracted data.
8. The generated DUA document is automatically pre-filled in a Word (.docx) template.
9. The system highlights extracted fields using color coding to indicate confidence levels.
10. The user reviews the generated document and downloads the final DUA file.

### Wireframes

The frontend interface will consist of the following main views:

**Login / Access Screen**

- Simple authentication interface for authorized users.
- Allows users to access the system securely.

**Main Dashboard**

- Central navigation interface after login.
- Displays options to create a new DUA generation process.
- Shows previous document processing history.

**Document Upload Screen**

- Interface for uploading a folder containing source files.
- Displays supported formats (Excel, Word, PDF, Images).
- Shows upload progress and validation feedback.

**Processing Status Screen**

- Displays the progress of document analysis and extraction.
- Shows steps such as validation, classification, OCR processing, and data extraction.

**DUA Review Screen**

- Displays the generated DUA document preview.
- Highlights extracted fields with color indicators representing confidence levels.
- Allows the user to review extracted data.

**Download Screen**

- Allows the user to download the generated DUA document in Word (.docx) format.
- Provides confirmation that the document generation process is complete.

