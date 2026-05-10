---
name: prd-workflow-governance
description: Use when reviewing, creating, or formalizing PRD/workflow governance artifacts: demand intake, analysis, review gates, template selection, freeze/change control, prototype binding, delivery-package output, or document-version rules.
---

# PRD Workflow Governance

## Overview

Use this skill for structured product-document work where correctness depends on process discipline, not just wording. It applies to PRDs, demand-flow rules, review standards, freeze criteria, prototype binding, delivery packages, and versioned governance docs.

## When To Use

Use it when the task involves any of these:

- PRD drafting, rewriting, reviewing, or standardization
- demand intake, prioritization, analysis, or freeze rules
- formal review, approval, sign-off, or change control
- prototype binding, prototype acceptance, or archive records
- delivery-package completeness, traceability, or version management

Do not use it for pure code implementation, visual design, or simple copyediting.

## Core Workflow

1. Determine the stage first.
   - Exploration and scope narrowing use the lightweight template.
   - Formal review, freeze, delivery, and archive use the standard template.
   - Do not mix the two in one living document.
2. Check completeness before approval.
   - Every functional point must be traceable to a scenario, rule, exception, and acceptance criterion.
   - Missing owner, unclear scope, or untestable rules block progress.
3. Enforce review gates.
   - Review must produce a decision, not only discussion.
   - Freeze requires resolved disputes, final scope, and explicit confirmation.
4. Validate delivery artifacts.
   - Delivery package must match the frozen version.
   - Prototype binding, interaction acceptance, and archive record must be present when the task reaches formal delivery.
5. Preserve traceability.
   - Keep version, owner, approval, and archive references explicit.
   - If the document changes after freeze, treat it as a formal change request.

## Reference Files

- [Stage and template selection](references/stage-and-template-selection.md)
- [Review and freeze gates](references/review-and-freeze-gates.md)
- [Delivery and traceability](references/delivery-and-traceability.md)

## Practical Defaults

- Prefer concise, testable requirements over long narrative.
- Prefer explicit tables for roles, rules, fields, exceptions, and acceptance criteria.
- Prefer one document per stage, with stable versioning and clear handoff records.

