# Assessment Scope — Northstar Workflow, Inc.

## 1. Organization Overview

Northstar Workflow, Inc. is a fictional small software-as-a-service (SaaS) company with approximately 25 employees. It provides a subscription-based workflow management platform that helps small businesses organize projects, manage tasks, and share internal business documents.

## 2. Business Operations

The company operates its application in a hypothetical Amazon Web Services (AWS) cloud environment. Its service depends on application availability, secure customer authentication, reliable data storage, and the ability to recover customer information following an incident.

## 3. Information Assets

The platform is assumed to process or store:

- Customer names and business email addresses.
- Customer account and authentication-related data.
- Project and task records.
- Uploaded business documents.
- Subscription and account records.
- Application and security logs.

The scenario does not assume that the company stores payment card numbers or regulated health information.

## 4. Business Priorities

Northstar Workflow's primary security priorities are:

- Protecting customer information from unauthorized access.
- Preserving the accuracy and integrity of customer data.
- Maintaining service availability.
- Recovering data and services following an incident.
- Meeting applicable contractual security commitments.

## 5. Assessment Context

This fictional organization will serve as the business context for a cybersecurity risk assessment using the NIST Cybersecurity Framework (CSF) 2.0 and relevant controls from NIST Special Publication 800-53.

The AWS environment is hypothetical and is not represented as a deployed or independently verified system.

## 6. Assessment Boundaries

### In Scope

The hypothetical assessment includes the following components and security considerations:

- AWS network architecture, including the VPC, subnets, routing, and security groups.
- Application-tier and database-tier network access.
- Application handling of customer information and uploaded business documents.
- Application and security logging, including the potential exposure of sensitive information through logs.
- Security controls and risk scenarios relevant to protecting customer information, maintaining service availability, and supporting incident investigation.

### Out of Scope

The following activities are excluded from this documentation-based assessment:

- Testing or scanning a live AWS environment.
- Reviewing actual AWS configurations, application source code, or production logs.
- Performing penetration testing or vulnerability scanning.
- Independently validating control implementation or operating effectiveness.
- Assessing payment card data environments or regulated health information systems.

These boundaries may be refined if additional system details or assessment evidence become available.
