# 🇪🇺 European Medicines Verification System (EMVS) Serialization Project

## 📌 Project Overview

This repository outlines the technical architecture, implementation framework, and execution roadmap for aligning pharmaceutical manufacturing operations with:

- EU Falsified Medicines Directive (FMD) – Directive 2011/62/EU  
- Delegated Regulation (EU) 2016/161  
- European Medicines Verification System (EMVS)  

The objective is to enable secure serialization, regulatory reporting, and real-time medicine verification across 30+ EEA member states.

---

# 1️⃣ Problem Statement

Counterfeit medicines posed a significant threat to public health in the European Union. Prior to mandatory serialization, the pharmaceutical supply chain lacked a unified, real-time verification mechanism from manufacturer to pharmacy.

## 🔎 Key Challenges

### 1. Data Fragmentation
- Disconnected data flows between:
  - Manufacturers (OBPs)
  - National Medicines Verification Systems (NMVS)
  - Parallel Distributors
- No centralized synchronization layer

### 2. Compliance Complexity
Mandatory 2D Data Matrix encoding:
- GTIN
- Unique Serial Number
- Batch
- Expiry
Strict adherence to GS1 standards.

### 3. Latency Requirements
- Sub-second response required for pharmacy decommissioning events
- Zero tolerance for patient-care delays

### 4. Interoperability
- Diverse IT ecosystems across 30+ EEA countries
- Single harmonized technical standard across markets
---


<img width="959" height="544" alt="57253F3E-EA3F-4958-98BE-4BDC4CC9F2AC" src="https://github.com/user-attachments/assets/be309a64-af9b-46f5-8238-88ff3dbbed91" />


---

<img width="1866" height="1000" alt="image" src="https://github.com/user-attachments/assets/f9677371-b9c9-4ce7-99db-b648a81eaea9" />


---

# 2️⃣ Solution Architecture – L1 to L5 Model

The solution implements a multi-layer integration model (L1–L5) to ensure full data integrity and compliance.

---

## 🏭 L1–L2: Line Level (Packaging Line Integration)

### Components
- Thermal Inkjet Printers (TIJ)
- Laser Coders
- 360° Vision Inspection Systems
- Rejection Gates
- Anti-Tampering Device (ATD)

### Capabilities
- Apply 2D Data Matrix (ISO/IEC 16022)
- Real-time code verification
- Automatic rejection of bad prints
- Serial data transmission to L3

---

## 🏢 L3: Site Level Serialization

### Example Systems
- Systech
- TraceLink
- Antares Vision

### Responsibilities
- Local serial number pool management
- Line orchestration
- Site-level reporting
- Rework and exception handling
- Temporary data buffering during connectivity failures

---

## 🏬 L4: Enterprise Level

### Systems
- ERP (SAP / Oracle)
- MES Platforms

### Responsibilities
- Master Data Governance (GTIN, Target Market, Product Codes)
- Batch creation
- Enterprise-level serial management
- OBP interface management
- Compliance audit logging

L4 acts as the primary gateway to the European Hub.

---

## 🌍 L5: Network Level – European Hub

---
<img width="1841" height="1056" alt="image" src="https://github.com/user-attachments/assets/f523e37b-4e17-403a-96ee-83cc093d4ce5" />

---

### Central Authority
European Medicines Verification Organisation (EMVO)

### Core Functions
- Commissioning data storage
- Routing to correct market
- Decommissioning validation
- Alert generation (potential falsification)

---

# 3️⃣ End-to-End Data Flow

```text
Packaging Line (L1/L2)
        ↓
Site Serialization Server (L3)
        ↓
Enterprise ERP / OBP Interface (L4)
        ↓
European Hub (L5)
        ↓
National System (NMVS)
        ↓
Pharmacy Decommissioning
```

---

# 4️⃣ Project Plan & Execution Roadmap

Execution is divided into four structured workstreams:
- Infrastructure
- Validation
- Integration
- Hypercare

---

## 📅 Phase 1: Assessment & System Design (Months 1–3)

### User Requirement Specifications (URS)
- Define hardware & software requirements
- Market-specific regulatory mapping

### Vendor Selection
- L3/L4 provider audit
- 21 CFR Part 11 compliance review
- EU Annex 11 assessment

### Network Architecture
- Secure VPN/API tunnels
- X.509 certificate exchange
- Firewall & encryption configuration

---

## 🛠️ Phase 2: Technical Build & Configuration (Months 4–8)

### L1/L2 Retrofitting
- Installation of high-speed TIJ printers
- Installation of 360° inspection cameras
- Line controller integration

### Master Data Setup
- GTIN creation
- Target market assignment
- Product code alignment

### API Development
Mapping GS1 EPCIS events:
- Commission
- Pack
- Ship
Configured to OBP interface (SOAP/REST).

---

## 🧪 Phase 3: Validation – IQ / OQ / PQ (Months 9–11)

| Testing Stage | Focus Area |
|---------------|------------|
| IQ (Installation Qualification) | Hardware installation verification |
| OQ (Operational Qualification) | Bad code detection, duplicate serial rejection |
| PQ (Performance Qualification) | End-to-end upload under full production load |

### Validation Framework
- GAMP 5 methodology
- Risk-based testing
- Traceability matrix (URS → Test Case)

---

## 🚀 Phase 4: Go-Live & Connectivity (Month 12+)

### OBP Onboarding
- Technical handshake with EMVO
- Certificate exchange
- Sandbox → Production migration

### National System Verification
- Confirm data residency in:
  - France
  - Germany
  - Other target markets

### Hypercare
- 24/7 monitoring
- First 10 batches oversight
- False alert reduction
- Rapid incident response

---

# 5️⃣ Technical Stack

## 📚 Standards
- GS1 EPCIS
- ISO/IEC 16022 (2D Data Matrix)
- XML / XSD Schema validation

## 🔗 Integration
- RESTful APIs
- SOAP Web Services
- XML / XSLT transformations
- Secure VPN tunnels

## 🗄️ Database
- Microsoft SQL Server
- Oracle DB
- High-availability clustering

## 🧾 Validation & Compliance
- GAMP 5 Framework
- 21 CFR Part 11
- EU Annex 11
- Audit Trail Enablement

---

# 6️⃣ Risk & Controls Matrix

| Risk | Mitigation |
|------|------------|
| Duplicate serial numbers | DB uniqueness constraints + randomization logic |
| Data upload failure | Auto-retry + alert escalation |
| Latency breach | Optimized API response & performance testing |
| Regulatory rejection | Pre-upload schema validation |

---

# 7️⃣ Repository Structure

```bash
/architecture
    L1-L5-system-design.md
/integration
    epcis-event-mapping.md
/validation
    IQ-OQ-PQ-strategy.md
/infrastructure
    network-security-design.md
/docs
    URS-template.md
    risk-assessment.md
```

---

# 📈 Business Impact

- Full EU FMD compliance
- Reduced counterfeit risk
- Sub-second pharmacy verification
- Standardized architecture across 30+ EEA markets
- Improved enterprise serialization governance

---

# 👨‍💼 Author

Pharma Digital Transformation | Serialization & Compliance Architecture
