# gaps.md — Gayatri Pokale
# Exercise 1 — INFO 7375
# Last updated: 2026-06-19
# Rule: a gap closes only when evidence ships → new resume.json entry → row deleted

## How to read this file
Each row maps a gap to a Madison build that would close it.
A gap without a Madison build is self-improvement, not a portfolio piece.
The top row is the Assignment 1 Part 2 project proposal.

---

## Gap Table

| Gap | Evidence the target demands it | What I have | Madison build that would close it | Plan |
|---|---|---|---|---|
| No public AI portfolio piece showing end-to-end pipeline | SWE job postings at AI-forward companies list deployed AI projects as differentiator — Northeastern co-op postings and LinkedIn SWE roles 2026 | Market Intelligence Agent V2 built in course but not fully documented as standalone portfolio piece | Extend Market Intelligence Agent V2 into a fully documented open-source repository with README, architecture diagram, live demo URL, and scale test results | Write comprehensive README, record 3-minute demo video, publish to GitHub with all documentation by July 2026 |
| No system design portfolio evidence | Senior SWE and SDE2 roles at target companies require demonstrated system design thinking — seen in 80% of job postings reviewed | Built microservices at Infosys and URL shortener project but no written design document exists | Build a Madison recipe that generates a system design document from a project description — produces architecture diagrams, trade-off analysis, and decision log | Create system design write-up for Market Intelligence Agent covering data flow, failure modes, and scaling decisions by August 2026 |
| No LeetCode or competitive programming signal | Technical interview processes at target companies include algorithmic coding rounds — standard for SWE roles at Amazon, Google, Microsoft | Strong backend production experience but no documented algorithmic practice | Build a Madison tool that tracks LeetCode practice — logs problems solved, patterns identified, and progress over time | Complete 50 medium LeetCode problems with documented solutions on GitHub by September 2026 |
| Limited cloud deployment experience beyond AWS basics | DevOps and cloud-native SWE roles require hands-on Kubernetes and full CI/CD pipeline experience — seen in Commonwealth co-op posting and target company JDs | AWS EC2/S3/RDS used at Infosys, Docker used in projects, but no Kubernetes or full CI/CD pipeline ownership | Extend Market Intelligence Agent V2 deployment to include a full CI/CD pipeline using GitHub Actions — auto-deploy to cloud on every commit | Add GitHub Actions workflow to Market Intelligence Agent repository with automated testing and deployment by July 2026 |
| No open source contributions outside coursework | SWE hiring managers at product companies value external open source contributions as proof of code quality under peer review | All projects are course assignments or employer work — no external open source contributions | Contribute to an existing Python or Java open source project — bug fix or small feature — and document the PR in resume.json | Identify one open source project to contribute to and submit first PR by August 2026 |

---

## Top Gap — Project Proposal (150-200 words)

**Project: Market Intelligence Agent V2 — Open Source Portfolio Edition**

The strongest gap between my current record and my SWE/SDE target role is 
the absence of a fully documented, publicly presentable AI portfolio piece. 
I have built the Market Intelligence Agent V2 as part of INFO 7375 — a 
complete end-to-end pipeline that collects RSS news from three sources, 
analyzes each article using Groq AI for sentiment, urgency, and sector 
classification, routes personalized HTML reports to correct business sector 
teams via Gmail, and exposes a Streamlit interface deployed at a public URL. 
The tool works and is deployed. What is missing is the documentation layer 
that turns a course project into a portfolio piece a hiring manager can 
evaluate in five minutes.

The Madison build that closes this gap is a documentation recipe — a 
structured template that generates a README, architecture diagram, scale 
test summary, and demo walkthrough from an existing project. Running this 
recipe on Market Intelligence Agent V2 produces a GitHub repository that 
demonstrates end-to-end AI pipeline thinking, Python deployment skills, 
API integration, error handling, and user-facing product design in a single 
artifact. This is the portfolio piece that makes the AI course work legible 
to a SWE hiring manager who has never heard of n8n or Groq.

---

## Deleted Row — with reason

**Deleted gap: "No machine learning model training experience"**

Reason for deletion: This gap is aspirational self-improvement, not 
evidence-backed. None of the SWE/SDE job postings reviewed for Assignment 1 
listed ML model training as a requirement for backend engineering roles. 
The target role is software engineer, not ML engineer. Adding this gap 
would blur the positioning and suggest a different career target than 
the one stated in brand.yml. Deleted to keep the gap table honest and 
role-specific.

---

## Rewritten Row — in my own words

**Original agent draft for cloud gap:**
"User lacks Kubernetes experience required for cloud-native roles"

**My rewrite:**
I have worked with Docker and AWS at Infosys and know how containerization 
works in production. What I have not done is own a full deployment pipeline 
end-to-end — from code commit to live environment — with automated testing 
and rollback. The gap is not theoretical knowledge of Kubernetes but the 
absence of a project where I made the deployment decisions myself and can 
show the CI/CD configuration. The Madison build that closes this is adding 
a real GitHub Actions workflow to Market Intelligence Agent V2 so the next 
version of resume.json can say "owned CI/CD pipeline" with a commit link 
as proof.
