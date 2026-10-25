# Risk Register — Northstar Workflow, Inc.

## Risk R-001: Potential Database Exposure

- **Asset:** Customer and business data stored in the database.
- **Risk category:** Network security and data confidentiality.
- **Scenario:** The database security group is misconfigured to allow inbound connections from `0.0.0.0/0`, permitting connection attempts from any IPv4 address.
- **Threat:** An unauthorized external party attempts to connect to the database.
- **Vulnerability or control weakness:** The overly permissive inbound security group rule.
- **Potential impact:** Unauthorized access, disclosure, modification, or deletion of customer data, potentially resulting in business disruption, contractual consequences, and reputational damage.
- **Existing controls:** Not yet verified. The scenario does not establish whether additional network, authentication, or database protections are effective.
- **Likelihood:** Not yet assessed.
- **Impact rating:** Not yet assessed.
- **Overall risk rating:** Not yet assessed.
- **Recommended treatment:** Restrict database inbound access to explicitly authorized application components and required ports. Review related network routes and access controls.
- **Evidence status:** Hypothetical scenario; no live AWS configuration has been inspected.
