# Security Control Matrix — Northstar Workflow, Inc.

## 1. Purpose

This document identifies security controls relevant to the preliminary cybersecurity risks documented in the Northstar Workflow, Inc. security risk assessment.

The matrix maps identified risks to relevant controls from NIST Special Publication 800-53 and documents the rationale for selecting each control, its intended application, and the evidence needed to assess implementation.

Northstar Workflow, Inc. is a fictional organization, and the AWS environment is hypothetical. Control implementation and effectiveness have not been verified in a live environment.

## 2. Reference Framework

- **Primary control catalog:** NIST Special Publication 800-53, Security and Privacy Controls for Information Systems and Organizations.
- **Catalog version:** Revision 5.2.0.
- **Risk framework:** NIST Cybersecurity Framework (CSF) 2.0.
- **Assessment context:** Preliminary, risk-based control selection for a hypothetical AWS-hosted SaaS environment.

## 3. Control Selection Method

Controls are selected based on their relevance to documented risk scenarios, affected system components, and the security outcomes needed to address those risks.

For each selected control, this matrix records:
- The related risk identifier.
- The NIST control identifier and name.
- The reason the control is relevant.
- Its intended application to the hypothetical system.
- The evidence needed to assess implementation.
- The current assessment status.

Control selection does not establish that a control has been implemented or is effective. Those conclusions require appropriate assessment evidence.

### Control Assessment Approach

If supporting evidence becomes available, each selected control should be evaluated based on its documented design, implementation, and operating effectiveness, as applicable to the control. Documentation alone may not establish that a control operates effectively. Assessment conclusions must be supported by appropriate evidence, and any limitations or unverified elements must be documented.

## 4. Selected Security Controls

### SC-7 — Boundary Protection

- **Related Risk:** R-001 — Potential Database Exposure.
- **Selection Rationale:** SC-7 addresses monitoring and controlling communications at external managed interfaces and key internal managed interfaces. It is relevant to the potential for unauthorized network access to the database.
- **Intended Application:** In the hypothetical AWS architecture, network boundaries and traffic rules should restrict database connections to authorized sources, such as the application tier, while controlling external access to the environment.
- **Assessment Evidence Required:** Database security-group rules, relevant subnet route tables, network architecture documentation, and connectivity test results.
- **Assessment Status:** Not assessed. The AWS environment is hypothetical, and no live configuration or connectivity evidence has been reviewed.

### AU-2 — Event Logging

- **Related Risk:** R-002 — Potential Exposure of Sensitive Information Through Application Logs.
- **Selection Rationale:** AU-2 addresses identifying events that the system can log, determining which events should be logged, and documenting the rationale for those decisions. It is relevant to establishing appropriate logging requirements for the hypothetical application.
- **Intended Application:** Northstar should define which application and security events need to be logged to support monitoring and investigation while avoiding unnecessary collection of sensitive information. The specific requirement to exclude session tokens, credentials, and unnecessary sensitive customer information from application logs is a proposed risk-treatment requirement; AU-2 is not being represented as an explicit prohibition against recording those values.
- **Assessment Evidence Required:** Documented logging requirements, application logging configuration, relevant logging code or configuration, representative log samples, and test results demonstrating whether sensitive values are excluded.
- **Assessment Status:** Not assessed. The AWS environment and application are hypothetical, and no implementation or logging evidence has been reviewed.
