# Risk Register — Northstar Workflow, Inc.

This risk register documents preliminary cybersecurity risk scenarios for Northstar Workflow, Inc., a fictional SaaS company using a conceptual AWS architecture. The scenarios, ratings, existing controls, and proposed remediation activities have not been validated against a live AWS environment.

The risk ratings use a project-specific 3 × 3 risk matrix. These ratings are preliminary judgments for this portfolio project, not confirmed security findings or ratings prescribed by NIST.

---

## Risk R-001: Potential Database Exposure

- **Asset:** Customer and business data stored in the database.
- **Risk category:** Network security and data confidentiality.
- **Scenario:** The hypothetical database security group is misconfigured to allow inbound connections from `0.0.0.0/0`, permitting connection attempts from any IPv4 address.
- **Threat:** An unauthorized external party attempts to connect to the database.
- **Vulnerability or control weakness:** An overly permissive inbound database security group rule.
- **Potential business impact:** Unauthorized access to the database could result in the disclosure, modification, or deletion of customer and business data, potentially causing business disruption, contractual consequences, and reputational damage. Actual consequences would depend on the data involved, the extent of unauthorized access, and the organization's applicable obligations. No unauthorized access has been confirmed.
- **Potential existing controls (not verified):** Security groups, network ACLs, and database authentication and authorization may help restrict unauthorized access. Their implementation and effectiveness have not been assessed.
- **Control verification status:** Unverified. No live AWS configuration, database settings, or supporting evidence has been examined. The existence and effectiveness of these controls must not be assumed.
- **Preliminary likelihood:** High.
- **Likelihood rationale:** The overly permissive inbound database security group creates an opportunity for connection attempts from any IPv4 address. Successful unauthorized access remains possible if the database is reachable and other safeguards fail. The rating is a preliminary scenario-based judgment, not a measured probability.
- **Preliminary impact:** High.
- **Impact rationale:** Unauthorized access to customer and business data could have significant confidentiality, integrity, operational, contractual, and reputational consequences. High impact is a preliminary assessment based on the potential consequences; the actual data exposure and business effects have not been verified.
- **Assessment limitations:** Database reachability, authentication strength, and the effectiveness of other network and access controls have not been verified. The scenario does not establish that the database is publicly reachable or that unauthorized access has occurred.
- **Preliminary overall risk rating:** Critical.
- **Risk rating rationale:** Under the project's risk matrix, High likelihood combined with High impact produces a Critical overall risk rating. This is a project-specific assessment methodology, not a claim that NIST prescribes this particular matrix.
- **Risk rating limitation:** The rating is preliminary and based on a hypothetical configuration. It must be reassessed when configuration evidence, reachability test results, and other relevant safeguards have been evaluated.
- **Risk treatment:** Mitigate.
- **Treatment rationale:** Restricting database network access to authorized sources can reduce the opportunity for unauthorized connection attempts while preserving required application functionality.
- **Proposed remediation:** Remove the inbound database security group rule allowing traffic from `0.0.0.0/0`. Restrict database inbound traffic to the authorized application tier's security group and the database engine's required port. Keep customer-facing HTTPS access on TCP port 443 at the Application Load Balancer. Confirm that the database does not have unintended public exposure and that the proposed restrictions preserve required application-to-database connectivity.
- **Validation requirements:** Collect configuration evidence showing that the database security group has no inbound rule allowing database access from `0.0.0.0/0` and permits the required database port only from the authorized application tier's security group. Obtain network validation results demonstrating that unauthorized sources cannot reach the database, along with functional test results confirming that authorized application-to-database connectivity still works. Record the test date, test method, result, evidence reference, and any unresolved exceptions. These tests are planned and have not been performed in a live environment.
- **Validation status:** Not performed — remediation has not been implemented or verified in a live AWS environment.
- **Primary risk owner:** Engineering Manager (proposed role; accountable for risk treatment and remediation oversight).
- **Technical remediation owner:** Cloud Security Engineer (proposed role; responsible for implementing and validating the security-group changes).
- **GRC tracking and evidence support:** GRC Analyst (proposed role; responsible for maintaining risk documentation and tracking remediation evidence).
- **Remediation priority:** Immediate triage due to the preliminary Critical rating. If an actual exposure is confirmed, investigation and appropriate containment should take priority.
- **Target remediation timeframe:** Within 24–72 hours after confirmation of an actual exposure.
- **Timeframe rationale:** The potential consequences of unauthorized database access warrant prompt investigation and remediation. The proposed timeframe is an illustrative project target, not a universal regulatory deadline. Any confirmed active exposure should be triaged immediately.
- **Implementation status:** Proposed — not implemented or verified in a live AWS environment.
- **Evidence status:** Hypothetical scenario; no live AWS configuration has been inspected.
- **Risk status:** Open — Assessment Pending.
- **Status rationale:** The risk scenario and proposed treatment are documented, but the actual AWS configuration, database reachability, and effectiveness of existing safeguards have not been verified. No remediation has been implemented or validated in a live environment.

---

## Risk R-002: Potential Exposure of Sensitive Information Through Application Logs

- **Asset:** Customer information, authentication-related data, session tokens, credentials, and application logs.
- **Risk category:** Data confidentiality, application security, and logging.
- **Scenario:** The hypothetical application records sensitive information in application logs, potentially making that information accessible to people or systems that do not require it.
- **Threat:** An unauthorized party or user with excessive permissions accesses sensitive information recorded in application logs.
- **Vulnerability or control weakness:** Inadequate sensitive-data filtering or redaction, excessive logging, or overly permissive access to application logs.
- **Potential business impact:** Unauthorized disclosure of sensitive information through application logs could result in customer data exposure, account compromise, reputational damage, and contractual or regulatory consequences where applicable. Actual consequences would depend on the information exposed, the extent of access, and the organization's applicable obligations. No exposure has been confirmed.
- **Potential existing controls (not verified):** Application logging configuration, sensitive-data filtering or redaction, IAM permissions governing log access, and log-retention settings may provide safeguards. Their implementation and effectiveness have not been assessed.
- **Control verification status:** Unverified. The application code, logging configuration, redaction safeguards, log-access permissions, and retention settings have not been examined. The existence and effectiveness of these controls must not be assumed.
- **Preliminary likelihood:** Moderate.
- **Likelihood rationale:** Sensitive information could be captured in application logs if logging practices do not adequately filter or redact it. The likelihood is rated Moderate provisionally because the application code, logging configuration, redaction safeguards, and log-access permissions have not been examined. This is a scenario-based judgment, not a measured probability.
- **Preliminary impact:** High.
- **Impact rationale:** If sensitive information such as session tokens, credentials, or customer data is recorded in application logs and accessed by unauthorized parties, the consequences could include account compromise, customer information exposure, reputational damage, and contractual or regulatory consequences where applicable. The impact is rated High provisionally because the actual data logged, exposure pathways, and affected systems have not been assessed.
- **Assessment limitations:** This is a hypothetical risk scenario. No evidence currently confirms that sensitive information is being recorded in logs or that unauthorized parties can access it. The application's logging practices, access controls, and applicable data-handling obligations have not been assessed.
- **Preliminary overall risk rating:** High.
- **Risk rating rationale:** Under the project's 3 × 3 risk matrix, Moderate likelihood combined with High impact produces a High overall risk rating. This rating is preliminary because the application code, logging configuration, and log-access controls have not been assessed.
- **Risk rating limitation:** This rating represents a hypothetical risk scenario, not a confirmed security finding. It should be reassessed when supporting evidence becomes available.
- **Risk treatment:** Mitigate.
- **Treatment rationale:** Northstar Workflow can reduce this risk without eliminating application logging by minimizing sensitive data in log records, applying appropriate redaction, and restricting log access according to least privilege.
- **Proposed remediation:** Review application logging practices and code for sensitive-data exposure. Prevent unnecessary recording of session tokens, credentials, and sensitive customer information. Implement appropriate filtering or redaction, restrict log access through least-privilege permissions, and establish appropriate log-retention requirements.
- **Validation requirements:** Review application logging code and configuration for sensitive-data handling. Test with representative data to confirm sensitive values are not unnecessarily recorded. Inspect sample logs for unintended exposure, verify that log-access permissions follow least privilege, and document test results, evidence references, test date, and any remaining exceptions. These tests are planned and have not been performed.
- **Validation status:** Not performed — remediation has not been implemented or verified.
- **Primary risk owner:** Engineering Manager (proposed role; accountable for risk treatment and remediation oversight).
- **Technical remediation owner:** Cloud Security Engineer (proposed role; responsible for technical remediation and validation).
- **GRC tracking and evidence support:** GRC Analyst (proposed role; responsible for tracking documentation and supporting evidence).
- **Remediation priority:** Timely assessment and remediation due to the preliminary High rating. Any confirmed active exposure of credentials, session tokens, or other sensitive information should be investigated and contained promptly.
- **Target remediation timeframe:** Within 7 days, subject to initial assessment and prioritization.
- **Timeframe rationale:** The preliminary High risk rating warrants timely remediation. The organization should first determine whether sensitive information is being recorded in application logs or exposed to unauthorized access. If active exposure is identified, immediate investigation and containment should take priority over the seven-day target. This timeframe is an illustrative project target, not a universal regulatory deadline.
- **Implementation status:** Proposed — not implemented or verified.
- **Evidence status:** Hypothetical scenario; application logging practices and log-access controls have not been inspected.
- **Risk status:** Open — Assessment Pending.
- **Status rationale:** The risk scenario and proposed treatment are documented, but the application's logging practices, sensitive-data redaction, and log-access permissions have not been verified. No remediation has been implemented or validated. The risk remains open pending assessment and supporting evidence.
