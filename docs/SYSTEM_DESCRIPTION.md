# System Description — Northstar Workflow, Inc.

## 1. Purpose

This document describes the hypothetical AWS-based system used by Northstar Workflow, Inc. for its security risk assessment. It establishes the system boundary and identifies the primary components that will be considered during the assessment.

## 2. System Overview

Northstar Workflow, Inc. is a fictional software-as-a-service (SaaS) company that provides a workflow management platform for small businesses. Customers use the platform to organize projects, manage tasks, and share internal business documents.

For this assessment, the platform is assumed to use an AWS-based architecture. The environment is conceptual and has not been deployed or independently verified.

## 3. Proposed Architecture

The proposed system consists of the following components:

- **Amazon VPC:** Provides the network boundary for the application's AWS resources.
- **Public and private subnets:** Separate internet-facing entry components from application and database resources.
- **Application Load Balancer:** Provides an entry point for customer HTTPS traffic and routes requests to the application tier.
- **Application tier:** Runs the SaaS application within private subnets.
- **Database tier:** Stores customer account information, project and task records, and other application data within private subnets.
- **AWS Identity and Access Management (IAM):** Manages permissions for authorized users and workloads.
- **Encryption controls:** Protect data in transit and at rest.
- **AWS CloudTrail:** Records supported AWS account and API activity for audit and investigation purposes.
- **Amazon CloudWatch:** Supports configured logging, metrics, and monitoring.
- **Backup and recovery capabilities:** Support restoration of protected data following an eligible loss or disruption.

The specific AWS compute, database, encryption, and backup services have not yet been selected. Their configuration and effectiveness are not assumed to be compliant or secure.

### 3.1 Risk-Relevant Components

Two components are particularly relevant to the preliminary risk scenarios documented in this assessment:

- **Database network access:** The database tier is intended to reside in private subnets. Its actual exposure depends on the implemented network configuration, including security group rules, routing, and permitted connection sources. Private-subnet placement alone does not establish that database access is appropriately restricted. This consideration supports risk scenario R-001.

- **Application logging:** Application and security logs may support monitoring and incident investigation. The information recorded, the handling of sensitive values, and the permissions governing log access will need to be evaluated. These considerations support risk scenario R-002.

## 4. Information Processed

The system is assumed to process or store:

- Customer names and email addresses.
- Authentication-related information.
- Project and task records.
- Uploaded business documents.
- Subscription and account records.
- Application and security logs.

Payment card numbers and regulated health information are outside the assumptions of this scenario.

## 5. System Boundary

The assessment will focus on the proposed AWS environment and its security-relevant components, including network architecture, application and database access, identity and permissions, encryption, logging and monitoring, and backup and recovery.

The assessment will also consider relevant administrative and operational practices where they affect the security of this system.

The assessment will not claim to evaluate a live production environment, validate actual AWS configurations, or certify the company against a security framework.

## 6. Assessment Status and Limitations

This is a hypothetical portfolio assessment. The architecture and system characteristics are scenario assumptions, not verified implementation details. Any future findings or control gaps must be labeled appropriately as hypothetical, assumed, or verified based on the evidence actually available.

The assessment will use relevant NIST Cybersecurity Framework 2.0 outcomes and selected NIST SP 800-53 controls to organize the security review.
