# Risk Register — Northstar Workflow, Inc.

## Risk R-001: Potential Database Exposure

- **Asset:** Customer and business data stored in the database.
- **Risk category:** Network security and data confidentiality.
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
- **Rating limitation:** The rating is preliminary and based on hypothetical scenario assumptions. It must be revisited if additional evidence changes the likelihood or impact assessment.
- **Recommended treatment:** Restrict database inbound access to explicitly authorized application components and required ports. Review related network routes and access controls.
- **Evidence status:** Hypothetical scenario; no live AWS configuration has been inspected.
