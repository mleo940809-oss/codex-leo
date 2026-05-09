# 产品需求管理流程规范结构收敛实施计划

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 将 `产品需求管理流程规范` 收敛为“主流程正文 + 外部规范引用”的稳定结构，消除章节边界混杂、减少重复维护点，并保留版本管理和产物治理的独立规范。

**Architecture:** 主文档只保留流程节点、责任、审批、时限、交付与复盘的核心规则；版本管理、产物治理、PRD 模板和节点技能路由统一移出到独立规范或附录引用。通过统一优先级声明和引用关系，避免不同文档各说各话。

**Tech Stack:** Markdown、现有 `docs/` 规范体系、Git、PowerShell。

---

### Task 1: 收敛主文档边界

**Files:**
- Modify: `docs/产品需求管理流程规范.md`

- [ ] **Step 1: Remove inline implementation-layer detail from the main workflow**

Keep the main workflow focused on process rules and convert support content into short references.

- [ ] **Step 2: Replace detailed version-management content with a reference**

Reference the separate `文档仓库提交规范.md` instead of keeping full version-maintenance rules inside the workflow doc.

- [ ] **Step 3: Keep appendices as references only**

Retain appendix-style links for skills, PRD templates, and work-product governance without expanding them in the main document.

---

### Task 2: Add explicit precedence rules

**Files:**
- Modify: `docs/产品需求管理流程规范.md`

- [ ] **Step 1: Add a single conflict-resolution order**

State which document wins when the workflow doc, work-product rules, Git rules, and PRD template disagree.

- [ ] **Step 2: Keep the precedence order short and enforceable**

Use one ordered list and avoid ambiguous “coexistence” language.

---

### Task 3: Normalize numbering and references

**Files:**
- Modify: `docs/产品需求管理流程规范.md`

- [ ] **Step 1: Recheck all top-level headings**

Ensure numbering is sequential and no duplicate top-level chapter numbers remain.

- [ ] **Step 2: Recheck appendix labels**

Make sure appendices are clearly labeled as references and do not look like duplicated core chapters.

---

### Task 4: Verify and snapshot

**Files:**
- Modify: `docs/versions/产品需求管理流程规范_v1.7_20260509.md` if the main doc content changes materially

- [ ] **Step 1: Compare the main doc against the snapshot rule**

Confirm whether the edit requires a new snapshot based on the version-management rule.

- [ ] **Step 2: Validate the final outline**

Check that headings, references, and document boundaries are internally consistent.

- [ ] **Step 3: Save the final version**

If the change is substantive, create a new `docs/versions/` snapshot with the updated version number and date.

