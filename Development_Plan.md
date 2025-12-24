# Development Action Plan: IAM Permissions Explorer

Objective: Technical roadmap to build the Impact Simulation engine and Risk Heatmap MVP.
Proposed Tech Stack: MERN (MongoDB, Express, React, Node.js) + Python (Log Analysis).

---

## Phase 1: Data Modeling (The Graph Problem)
Since IAM relationships are hierarchical (User -> Group -> Role -> Policy -> Resource), we need a schema that supports recursive queries.

Action Items:
1. Database Schema Design:
   - Create a User collection and a Role collection in MongoDB.
   - Optimization: Use a Graph-based approach (or recursive $graphLookup in MongoDB) to map nested dependencies efficiently.
2. Ingestion Service (Node.js):
   - Build a cron job that hits the AWS IAM API (e.g., get-account-authorization-details) every 24 hours.
   - Store the Last Used timestamp for every permission to identify Ghost Accounts.

---

## Phase 2: The Impact Simulation Engine (Core Feature)
This is the logic powering the Dry Run mode to solve Production Anxiety.

Action Items:
1. Log Ingestion Pipeline:
   - Set up a listener for CloudTrail Logs (AWS) or Audit Logs (GCP).
   - Filter specifically for Access Denied and Authorized events relevant to the target role.
2. The Simulation Algorithm:
   - Input: A Candidate Policy (the new, cleaner JSON).
   - Process: Replay the last 48h of logs against this Candidate Policy.
   - Logic: If a log entry would have triggered a 403 Denied under the new policy, flag it as a Breaking Change.
   - Output: Return a Confidence Score (e.g., 98% Success Rate).

---

## Phase 3: Frontend Architecture (React.js)
Focus on performance for large datasets (5,000+ identities).

Action Items:
1. Risk Heatmap Component:
   - Use TanStack Table for virtualization (to handle thousands of rows without UI lag).
   - Implement client-side sorting by Risk Score and Last Active Date.
2. Diff Viewer:
   - Integrate react-diff-viewer to show the side-by-side comparison of Current vs Recommended JSON policies.
3. State Management:
   - Use React Query to cache the simulation status so the user doesn't lose progress if they switch tabs.

---

## Phase 4: Automation & Integrations

Action Items:
1. Slack Webhook Integration:
   - Create a generic API endpoint /api/v1/notify-owner.
   - When clicked, it sends an interactive Slack block kit message to the resource owner asking for justification.
2. Auto-Remediation Cron:
   - A nightly job that checks for permissions marked approved_for_deletion and calls the AWS SDK to detach them automatically.

---

## Success Criteria for Dev Team
- Latency: The Risk Heatmap must load in <200ms.
- Accuracy: The Simulation Engine must process 1GB of logs in <60 seconds.
- Safety: The Revoke button must require a confirmation modal with the Simulation Score visible.
