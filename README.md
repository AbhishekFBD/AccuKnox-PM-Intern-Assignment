# IAM Permissions Explorer: Product Case Study

Author: Abhishek | Role: Product Manager Trainee
Focus: Cloud Security, Zero Trust, and UX Optimization

---

## Project Overview
The Challenge: In modern cloud environments (AWS/GCP), security teams face a "Production Paradox." They identify thousands of unused "Admin" permissions (Bloat) but are paralyzed by the fear that revoking them will break a live service.

The Solution: I designed the IAM Permissions Explorer, a security dashboard centered on a novel "Impact Simulation" engine. This allows engineers to "test" a policy revocation in a shadow mode (Dry Run) before enforcing it, solving the anxiety of downtime.

---

## Core Product Features
Drawing from my background in MERN Stack development and Algorithmic Optimization (LeetCode Rating: 1981), I prioritized features that balance security rigor with engineering velocity.

### 1. The Risk Heatmap (Prioritization)
Solves "Alert Fatigue" by using a weighted algorithm to surface only the High-Risk identities (e.g., Unused Admins).
![Risk Dashboard](./design/1-Risk-Heatmap.png)

### 2. The Impact Simulator (My Core Innovation)
Inspired by the "Dry Run" logic I proposed for Bitscale.ai. This feature replays 48 hours of log data against a candidate policy to predict "Breaking Changes" with 98% confidence.
![Simulation Workspace](./design/2-Impact-Simulation.png)

### 3. Automated Remediation Hub
Reduces UI complexity by 50% (similar to my optimization work at BookMyStay). It automates the "Justification" workflow via Slack, removing the manual burden from the Security Lead.
![Remediation Flow](./design/3-remediation-flow.png)

---

## Project Artifacts

- [Product Strategy (1-Pager)](./writeup/IAM_Explorer_Strategy.pdf): My RICE prioritization, User Persona (Kunal), and Success Metrics (KPIs).
- [Development Plan](./Development_Plan.md): (Bonus) A technical roadmap I wrote for the Engineering team, detailing the Graph Database schema and React.js architecture.
- [Wireframes](./design/): High-fidelity mockups demonstrating the user journey.

---

## Strategic Reasoning (Why this solution?)
I chose Impact Simulation as the P0 (Highest Priority) feature because it directly addresses the root cause of permission bloat: Fear.
- Metric: By increasing "Revocation Confidence," we aim to reduce Mean Time to Remediate (MTTR) by 70%.
- Feasibility: As detailed in my [Development Plan](./Development_Plan.md), this can be built using existing CloudTrail logs without requiring a massive infrastructure overhaul.

---

## About Me
I am a final-year B.Tech student and LeetCode Knight (Top 2% Global) with experience building full-stack applications. I blend deep technical problem-solving with product intuition to build tools that developers actually want to use.

- Tech Stack: React.js, Node.js, C++, SQL
- Product Skills: Root Cause Analysis, Wireframing, Roadmap Planning
