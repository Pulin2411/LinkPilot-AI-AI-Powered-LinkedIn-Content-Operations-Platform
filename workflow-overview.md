# Workflow Overview

## Project Overview

LinkPilot AI is an AI-powered LinkedIn Content Operations Platform built using n8n, OpenAI, Google Sheets, Gmail, Google Drive, and LinkedIn.

The platform automates the complete content lifecycle:

1. Topic Research
2. Content Creation
3. Quality Review
4. Rewrite Optimization
5. Human Approval
6. LinkedIn Publishing
7. Performance Tracking

The goal is to help business owners, consultants, founders, and thought leaders maintain a consistent LinkedIn presence while reducing manual effort.

---

# High-Level Architecture

```text
Topic
  ↓
Research Agent
  ↓
Content Writer Agent
  ↓
Quality Reviewer
  ↓
Rewrite Loop
  ↓
Human Approval
  ↓
LinkedIn Publisher
  ↓
Google Sheet Tracking
```

Optional:

```text
Approved Content
  ↓
Image Prompt Generator
  ↓
AI Image Generation
  ↓
Google Drive
  ↓
Google Sheet Update
```

---

# Workflow 1 – Content Research

## Purpose

Find the most relevant business-focused article related to a user-defined topic.

## Agent

Content Research Agent

## Responsibilities

* Search recent content
* Prioritize trusted sources
* Focus on business value
* Avoid documentation pages
* Return a single article URL

## Output

Article URL

Example:

```text
https://example.com/article
```

---

# Workflow 2 – LinkedIn Content Generation

## Purpose

Convert research insights into an original LinkedIn post.

## Agent

LinkPilot Content Writer

## Responsibilities

* Maintain founder voice
* Focus on business outcomes
* Create engaging hooks
* Simplify technical concepts
* Generate actionable insights

## Output

Publication-ready LinkedIn post

---

# Workflow 3 – Quality Review

## Purpose

Evaluate content quality before approval.

## Agent

Content Quality Reviewer

## Evaluation Criteria

* Hook
* Readability
* Engagement
* Authority
* Humanity

## Output

JSON Review Object

Example:

```json
{
  "hook": 9,
  "readability": 8,
  "engagement": 9,
  "authority": 8,
  "humanity": 9,
  "overall": 8.6,
  "feedback": "Needs stronger CTA"
}
```

---

# Workflow 4 – Rewrite Loop

## Purpose

Improve content that does not meet quality requirements.

## Agent

LinkedIn Rewrite Agent

## Responsibilities

* Improve hook
* Improve readability
* Improve engagement
* Preserve founder voice
* Preserve business message

## Process

```text
Review
   ↓
Fail
   ↓
Rewrite
   ↓
Review Again
```

Maximum attempts can be configured.

---

# Workflow 5 – Human Approval

## Purpose

Ensure final human oversight before publishing.

## Process

Draft approval email is sent.

Reviewer can:

* Approve
* Reject

Approved content moves to publishing.

Rejected content returns for revision.

---

# Workflow 6 – LinkedIn Publishing

## Purpose

Publish approved content automatically.

## Conditions

Content must satisfy:

```text
Status = READY_TO_POST
Approval_status = Approved
Posting_Status != Posted
```

## Actions

* Publish to LinkedIn
* Store post URL
* Store content ID
* Update posting status

---

# Workflow 7 – Image Generation (Optional)

## Purpose

Generate LinkedIn-ready infographic images.

## Agent

Image Prompt Generator

## Features

* Executive design style
* Business-focused visuals
* Human + AI collaboration themes
* Personal branding

## Output

Infographic image uploaded to Google Drive

---

# Google Sheet as System Database

Google Sheets acts as the central content repository.

Tracks:

* Topics
* Research URLs
* Drafts
* Review scores
* Approval status
* Publishing status
* LinkedIn URLs
* Image URLs

---

# Benefits

## Consistency

Maintains a regular content publishing schedule.

## Quality Control

Every post passes through automated review.

## Scalability

Reduces manual effort while increasing content output.

## Personal Branding

Helps establish authority through consistent thought leadership.

## Automation

Minimizes repetitive content management tasks.

---

# Future Roadmap

Planned enhancements:

* AI Topic Generator
* LinkedIn Carousel Generation
* Multi-Platform Publishing
* Analytics Dashboard
* Performance Feedback Loop
* Content Calendar
* IntelliOps Branding Mode
* Agentic Content Operations

---

# Author

Pulin Shah

AI Consultant | Automation Specialist | IT Leader

20+ Years of IT Experience

Focused on AI Automation, Operational Efficiency, and Business Growth.
