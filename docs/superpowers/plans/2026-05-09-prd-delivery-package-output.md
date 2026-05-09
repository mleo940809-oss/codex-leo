# PRD Delivery Package Output Alignment Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Make the PRD workflow explicitly require a complete delivery package and align the reusable Markdown template with the workflow's output expectations.

**Architecture:** Update the reusable PRD Markdown template to include a dedicated delivery-package section, then update the workflow spec's `6.6` section to name the required outputs and gate conditions. Keep changes localized to the template and the workflow spec to minimize drift.

**Tech Stack:** Markdown, workflow documentation, PRD process rules

---

### Task 1: Add delivery-package section to the reusable PRD template

**Files:**
- Modify: `docs/PRD工作流复用模板.md`

- [ ] **Step 1: Insert a dedicated delivery-package output section**

Add a new section near the end of the template with a table that lists the required delivery artifacts: PRD正文、交付包清单、冻结/归档记录、验收标准、附件清单、依赖说明、交付确认记录.

- [ ] **Step 2: Review the added section for naming consistency**

Confirm the new section uses the same terminology as the workflow spec and that the field names are specific enough for repeatable use.

### Task 2: Update workflow spec section 6.6

**Files:**
- Modify: `docs/产品需求管理流程规范.md`

- [ ] **Step 1: Rewrite `6.6` output requirements**

Explicitly list the expected output artifacts and state that the delivery package is incomplete if any required item is missing.

- [ ] **Step 2: Add a completion gate**

State the section cannot close unless the delivery package is complete, the frozen version matches, and the confirmation record is present.

### Task 3: Consistency check

**Files:**
- Review: `docs/PRD工作流复用模板.md`
- Review: `docs/产品需求管理流程规范.md`

- [ ] **Step 1: Compare the template section against `6.6`**

Verify that every required output in `6.6` has a corresponding place in the template.

- [ ] **Step 2: Fix any mismatch inline**

If the workflow spec names an artifact that is missing from the template, add it immediately rather than leaving a gap.

