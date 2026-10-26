# Risk Register — Northstar Workflow, Inc.

## Risk R-001: Potential Database Exposure

- **Asset:** Customer and business data stored in the database.
- **Risk category:** Network security and data confidentiality.
- **Primary risk owner:** Engineering Manager (proposed role; accountable for risk treatment and remediation oversight).
- **Technical remediation owner:** Cloud Security Engineer (proposed role; responsible for implementing and validating the security-group changes).
- **GRC support:** GRC Analyst (proposed role; responsible for maintaining risk documentation and tracking remediation evidence).
- **Remediation priority:** Immediate triage due to the preliminary Critical rating.
- **Target remediation timeframe:** Within 24–72 hours after confirmation of an actual exposure.
- **Deadline rationale:** Potential unauthorized access to customer and business data could result in significant confidentiality, contractual, operational, and reputational consequences.
- **Deadline status:** Proposed project target; no actual exposure or remediation date has been verified.
- **Scenario:** The database security group is misconfigured to allow inbound connections from `0.0.0.0/0`, permitting connection attempts from any IPv4 address.
- **Threat:** An unauthorized external party attempts to connect to the database.
- **Vulnerability or control weakness:** The overly permissive inbound security group rule.
- **Potential impact:** Unauthorized access, disclosure, modification, or deletion of customer data, potentially resulting in business disruption, contractual consequences, and reputational damage.
- **Potential existing controls:** Security groups, network ACLs, and database authentication and authorization may help restrict unauthorized access.
- **Control verification status:** Unverified. No live AWS configuration, database settings, or supporting evidence has been examined. The existence and effectiveness of these controls must not be assumed.
- **Likelihood:** High (preliminary).
- **Likelihood rationale:** The overly permissive inbound database security group creates an opportunity for connection attempts from any IPv4 address. Successful unauthorized access remains possible if the database is reachable and other safeguards fail.
- **Assessment limitations:** Database reachability, authentication strength, and the effectiveness of other network and access controls have not been verified. The rating is a scenario-based judgment, not a measured probability.
- **Impact rating:** Not yet assessed.
- **Overall risk rating:** Critical (preliminary).
- **Rating methodology:** A project-specific 3 × 3 risk matrix combines likelihood and impact. High likelihood plus High impact produces a Critical rating.
- **Risk treatment:** Mitigate.
- **Recommended remediation:** Remove the overly permissive database security group rule allowing inbound traffic from `0.0.0.0/0`. Restrict database inbound traffic to the authorized application tier's security group and the database engine's required port. Keep customer-facing HTTPS access on TCP port 443 at the Application Load Balancer.
- **Validation requirements:** Collect configuration evidence showing that the database security group has no inbound rule allowing database access from `0.0.0.0/0` and permits the required database port only from the authorized application tier's security group. Collect network validation results demonstrating that unauthorized sources cannot reach the database, along with functional test results confirming that authorized application-to-database connectivity still works. Record the test date, test method, result, and evidence reference. These tests are planned and have not been performed in a live environment.
- **Implementation status:** Proposed; not implemented or verified in a live AWS environment.
- **Evidence status:** Hypothetical scenario; no live AWS configuration has been inspected.
