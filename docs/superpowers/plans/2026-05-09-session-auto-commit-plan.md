# 会话自动提交产物到 Git 实施计划

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 建立一套“阶段门通过后自动提交”的会话级 Git 提交机制，让每个会话在形成正式产物时自动生成快照、提交 Git 并保留可回滚历史，同时避免把讨论稿、半成品和无关改动误提交。

**Architecture:** 采用“会话 checkpoint + 正式产物包 + Git 提交”三段式流程。会话中的讨论只在达到正式产物门槛时进入提交候选状态；候选状态必须先满足快照、版本号和文件完整性校验，再执行 `git add`、`git commit`，正式发布时补打标签。该方案不以“对话结束”为提交触发点，而以“阶段性产物完成”为触发点。

**Tech Stack:** Git、PowerShell、Markdown、现有文档规范体系、`docs/versions/` 快照目录。

**Governance:** 会话自动提交不能替代会话记忆沉淀。跨会话、长任务或压缩风险场景，必须先按会话记忆规则写入可回读记录并更新索引，再进入 Git 提交候选。

**Policy Position:** 本计划是辅助性的仓库执行规范，不高于会话记忆强制执行规则。凡涉及跨会话延续、决策型问题或压缩风险，必须先完成会话记忆沉淀，再允许进入自动提交候选。

### 会话记忆前置

如果本次会话属于跨会话延续、长任务、决策型问题或存在明显压缩风险，必须先用 `notion-knowledge-capture` 写入会话记录并更新总索引，然后才能进入 Git 自动提交候选。Git 提交只负责产物留档，不承担会话记忆职责。

---

## 方案对比

### 方案 A：会话结束即提交

优点：
- 自动化程度高
- 规则简单

缺点：
- 很容易把半成品、讨论稿和试错内容一起提交
- 历史会很碎，回滚成本高
- 不适合你当前的文档治理体系

结论：
- 不推荐

### 方案 B：每次写文件就提交

优点：
- 改动粒度极细

缺点：
- 提交过碎
- 审阅困难
- 很容易产生噪音提交

结论：
- 不推荐

### 方案 C：阶段门通过后自动提交

优点：
- 与现有文档流程、版本快照和正式发布规则一致
- 可控、可审阅、可回滚
- 能区分草稿和正式产物

缺点：
- 需要先定义正式产物门槛
- 需要一点固定的提交前检查规则

结论：
- 推荐采用。本计划的最终方案。

### 治理约束

本计划只在现有工作分支内执行自动提交，不负责替代分支创建。若当前会话还没有工作分支，应先创建或切换到合适的工作分支，再进入自动提交流程。

---

### Task 1: 定义会话提交边界

**Files:**
- Create: `docs/会话自动提交规范.md`
- Modify: `docs/文档仓库提交规范.md`
- Modify: `docs/工作产出物管理规则.md`
- Modify: `AGENTS.md`
- Modify: `docs/会话记忆强制执行规则.md`

- [ ] **Step 1: Define what counts as a commit-worthy session outcome**

明确只有以下类型的结果才进入自动提交候选：

- 正式文档正文已更新
- 对应 `docs/versions/` 快照已生成
- 版本号已递增或正式修订已确认
- 文件内容达到可追溯、可审阅、可回滚状态

- [ ] **Step 2: Define what must not trigger auto-commit**

明确以下内容不得自动提交：

- 口头讨论记录
- 临时分析稿
- 未完成的草稿
- 仅用于试验的文件修改
- 无法解释来源的杂项文件

- [ ] **Step 3: Define the session checkpoint rule**

把提交触发点定义为“阶段门完成”，不是“会话结束”或“每次保存”。

- [ ] **Step 4: Define the session memory gate**

跨会话、长任务、决策型问题或明显压缩风险场景下，必须先用会话记忆规则沉淀会话记录并更新索引，Git 提交不能替代会话记录。

- [ ] **Step 5: Add the top-level entry point**

在 `AGENTS.md` 和会话记忆规则中补入会话自动提交的入口说明，明确它属于辅助执行规范，且优先级低于会话记忆沉淀规则。

---

### Task 2: Define the commit package

**Files:**
- Create: `docs/会话自动提交规范.md`
- Modify: `docs/文档仓库提交规范.md`

- [ ] **Step 1: Specify the minimum commit package**

每次自动提交前，必须同时满足：

- 主文档已更新
- 对应快照已生成
- 版本号已确认
- 变更理由已记录
- 没有未解释的临时文件

- [ ] **Step 2: Specify file inclusion rules**

自动提交只纳入本次正式产物相关文件，优先包含：

- 主文档
- `docs/versions/` 中对应快照
- 与本次产物直接相关的辅助规范变更

排除：

- 临时测试文件
- 无关截图
- 个人草稿
- 未说明来源的杂项文件

- [ ] **Step 3: Specify commit message template**

提交信息采用短句式，格式应能直接反映产物主题，例如：

- `docs: publish prd workflow v1.8`
- `docs: snapshot git submission rule v1.1`
- `docs: update work product governance`

---

### Task 3: Define the execution sequence

**Files:**
- Create: `docs/会话自动提交规范.md`
- Modify: `docs/文档仓库提交规范.md`

- [ ] **Step 1: Write the exact automation order**

自动提交顺序固定为：

0. 如果属于跨会话延续、长任务或压缩风险场景，先写会话记录并更新总索引
1. 确认当前处于合适的工作分支；如未在分支上，先创建或切换到工作分支
2. 判断是否达到正式产物门槛
3. 生成或校验快照
4. 校验正文与快照一致性
5. 暂存本次正式文件
6. 执行 Git 提交
7. 正式发布时打标签

- [ ] **Step 2: Add a pre-commit validation list**

提交前必须检查：

- 是否同一主题
- 是否误改无关文件
- 是否已生成快照
- 是否已递增版本号
- 是否可解释每个文件的变更原因

- [ ] **Step 3: Add a post-commit confirmation rule**

提交完成后必须记录：

- 提交哈希
- 关联版本号
- 快照文件名
- 发布状态

---

### Task 4: Define failure handling and override rules

**Files:**
- Create: `docs/会话自动提交规范.md`
- Modify: `docs/文档仓库提交规范.md`

- [ ] **Step 1: Define failed-check behavior**

如果快照未生成、版本未确认或存在无关文件，则不执行自动提交，保留当前工作区并提示人工处理。

- [ ] **Step 2: Define manual override**

只有当用户明确要求“保留草稿”或“暂不提交”时，才允许暂缓提交。

- [ ] **Step 3: Define recovery behavior**

若提交前检查失败，必须先修复原因，再重新走一次完整的提交顺序，不得跳过校验继续提交。

---

### Task 5: Integrate with existing governance docs

**Files:**
- Modify: `AGENTS.md`
- Modify: `docs/文档仓库提交规范.md`
- Modify: `docs/产品需求管理流程规范.md`
- Modify: `docs/工作产出物管理规则.md`
- Modify: `docs/会话记忆强制执行规则.md`

- [ ] **Step 1: Add a reference to the new session submission rule**

在现有规范中补一条“会话自动提交”入口说明，让团队知道正式产物完成后会走自动提交规则。

- [ ] **Step 1b: Add the session memory precedence note**

明确会话记忆沉淀优先于 Git 提交；当需要跨会话延续或压缩前保留时，先完成会话记录，再进入自动提交候选。

- [ ] **Step 1c: Add the AGENTS entry**

在 `AGENTS.md` 中加入一条简短入口说明，指向会话自动提交规范和会话记忆强制执行规则，避免新规则只存在于单独文档里。

- [ ] **Step 2: Align release and snapshot language**

确保主流程里的版本号、快照、归档、提交和标签表述一致，不再出现相互冲突的叫法。

- [ ] **Step 3: Validate the full chain**

验证一条完整链路是否成立：

会话完成 -> 正式产物确认 -> 快照生成 -> Git 提交 -> 正式发布/标签 -> 历史留存

- [ ] **Step 4: Add the branch gate to the sequence**

确保自动提交链路包含“工作分支存在”这一前置条件，不在 `main` 上直接做自动提交。

---

## 验收标准

这份方案完成后，应该满足以下结果：

- 每个正式产物都有明确的自动提交触发点
- 只有阶段性产物会进入 Git 提交
- 提交前必须先留快照
- 草稿和讨论稿不会污染正式历史
- 回滚时能定位到快照和提交两层历史

## 风险提示

- 如果不先定义正式产物边界，自动提交会变成“自动乱提交”
- 如果不绑定快照，Git 历史和文档版本会脱节
- 如果不设置失败回退，自动化会在最需要稳的时候失控
