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
- **Risk status:** Open — Assessment Pending.
- **Status rationale:** The risk scenario and proposed treatment are documented, but the actual AWS configuration, database reachability, and effectiveness of existing safeguards have not been verified. No remediation has been implemented or validated in a live environment.
- **Rating methodology:** A project-specific 3 × 3 risk matrix combines likelihood and impact. High likelihood plus High impact produces a Critical rating.
- **Risk treatment:** Mitigate.
- **Recommended remediation:** Remove the overly permissive database security group rule allowing inbound traffic from `0.0.0.0/0`. Restrict database inbound traffic to the authorized application tier's security group and the database engine's required port. Keep customer-facing HTTPS access on TCP port 443 at the Application Load Balancer.
- **Validation requirements:** Collect configuration evidence showing that the database security group has no inbound rule allowing database access from `0.0.0.0/0` and permits the required database port only from the authorized application tier's security group. Collect network validation results demonstrating that unauthorized sources cannot reach the database, along with functional test results confirming that authorized application-to-database connectivity still works. Record the test date, test method, result, and evidence reference. These tests are planned and have not been performed in a live environment.
- **Implementation status:** Proposed; not implemented or verified in a live AWS environment.
- **Evidence status:** Hypothetical scenario; no live AWS configuration has been inspected.

---

## Risk R-002: Potential Exposure of Sensitive Information Through Application Logs

- **Preliminary impact:** High.
- **Impact rationale:** If sensitive information such as session tokens, credentials, or customer data is recorded in application logs and accessed by unauthorized parties, the consequences could include account compromise, customer information exposure, reputational damage, and contractual or regulatory consequences where applicable. The impact is rated High provisionally because the actual data logged, exposure pathways, and affected systems have not been assessed.
- **Preliminary likelihood:** Moderate.
- **Likelihood rationale:** Sensitive information could be captured in application logs if logging practices do not adequately filter or redact it. The likelihood is rated Moderate provisionally because the application code, logging configuration, redaction safeguards, and log-access permissions have not been examined.
- **Assessment limitation:** This is a hypothetical risk scenario. No evidence currently confirms that sensitive information is being recorded in logs or that unauthorized parties can access it.
- **Preliminary overall risk rating:** High.
- **Risk rating rationale:** Under the project's 3×3 risk matrix, Moderate likelihood combined with High impact produces a High overall risk rating. This rating is preliminary because the application code, logging configuration, and log-access controls have not been assessed.
- **Risk rating limitation:** This rating represents a hypothetical risk scenario, not a confirmed security finding. The rating should be reassessed when supporting evidence becomes available.
- **Risk treatment:** Mitigate.
- **Treatment rationale:** Northstar Workflow can reduce this risk without eliminating application logging by minimizing sensitive data in log records, applying appropriate redaction, and restricting log access according to least privilege.
- **Proposed remediation:** Review application logging practices and code for sensitive data exposure; prevent unnecessary recording of session tokens, credentials, and sensitive customer information; implement appropriate filtering or redaction; restrict log access through least-privilege permissions; and establish log-retention requirements.
- **Implementation status:** Proposed — not implemented or verified.
- **Validation requirements:** Review application logging code and configuration for sensitive-data handling; test with representative data to confirm sensitive values are not unnecessarily recorded; inspect sample logs for unintended exposure; verify log-access permissions follow least privilege; and document test results, evidence references, test date, and any remaining exceptions.
- **Validation status:** Not performed — remediation has not been implemented or verified.
- **Primary risk owner:** Engineering Manager (proposed role; accountable for the risk and treatment oversight).
- **Technical remediation owner:** Cloud Security Engineer (proposed role; responsible for the technical remediation).
- **GRC tracking and evidence support:** GRC Analyst, tracks documentation and supporting evidence.
- **Target remediation timeframe:** Within 7 days, subject to initial assessment and prioritization.
- **Timeframe rationale:** The preliminary High risk rating warrants timely remediation. The organization should first determine whether sensitive information is being recorded in application logs or exposed to unauthorized access. If active exposure is identified, immediate investigation and containment should take priority over the seven-day target.
- **Risk status:** Open — Assessment Pending.
- **Status rationale:** The risk scenario and proposed treatment are documented, but the application's logging practices, sensitive-data redaction, and log-access permissions have not been verified. No remediation has been implemented or validated. The risk remains open pending assessment and supporting evidence.
