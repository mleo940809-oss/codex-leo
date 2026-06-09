# PRD Workflow V3 Fixes Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 修正 `IT产品经理工作流-v3` 中的总纲入口冲突、节点编号残留、重复文件和偏差门禁口径不一致问题。

**Architecture:** 本次只修改已解压的 v3 工作流文档，不修改原 ZIP。以 `总纲.md` 作为唯一正式总纲入口，将 `工作流总纲.md` 改为历史说明文件，避免两个并行入口；其余节点文件按 v3 节点链路统一为 `1 -> 2 -> 3 -> 3.5 -> 4 -> 4.5 -> 5 -> 5.5 -> 6 -> 7 -> 7.5 -> 8`。

**Tech Stack:** Markdown 文档、PowerShell 文本检索、人工一致性校验。

---

### Task 1: 固定唯一总纲入口

**Files:**
- Modify: `E:\Codex\New_rules\.review\IT产品经理工作流-v3\总纲.md`
- Modify: `E:\Codex\New_rules\.review\IT产品经理工作流-v3\工作流总纲.md`

- [x] **Step 1: 将 `工作流总纲.md` 降级为历史说明**

把 `工作流总纲.md` 正文替换为历史稿说明，明确当前正式入口是 `总纲.md`，禁止作为执行入口。

- [x] **Step 2: 修正 `总纲.md` 的节点链路和目录结构**

确保 `总纲.md` 包含节点4、4.5，并在目录结构中补齐：

```text
节点4-可视化设计/
节点4.5-可视化设计评审/
节点5-PRD书写/
节点5.5-PRD初审/
节点6-高保真原型图/
节点7-原型验收/
节点7.5-原型图确认与PRD回填/
节点8-全面评审/
```

- [x] **Step 3: 校验双入口风险**

Run:

```powershell
Select-String -LiteralPath 'E:\Codex\New_rules\.review\IT产品经理工作流-v3\工作流总纲.md' -Pattern '当前正式入口|不得作为执行入口'
```

Expected: 两个关键词均出现。

---

### Task 2: 修正总纲编号、回流和版本映射

**Files:**
- Modify: `E:\Codex\New_rules\.review\IT产品经理工作流-v3\总纲.md`

- [x] **Step 1: 修正回流机制编号**

将原型验收统一为节点7，PRD回填统一为节点7.5，全面评审统一为节点8。

- [x] **Step 2: 修正问题回流判定表格式**

补齐图表问题行尾表格分隔符，避免 Markdown 表格断裂。

- [x] **Step 3: 修正版本与产出物映射**

版本映射应包含：

```text
4    可视化设计交付物
4.5  可视化设计评审报告
5    PRD文档
5.5  PRD初审报告
6    HTML原型/静态资源/页面索引
7    原型验收报告
7.5  终版PRD/差异说明/PRD变更记录
8    全面评审报告
```

- [x] **Step 4: 校验旧编号残留**

Run:

```powershell
Select-String -LiteralPath 'E:\Codex\New_rules\.review\IT产品经理工作流-v3\总纲.md' -Pattern '6\.5 PRD回填|7 全面评审|4\.5初审|节点5图表'
```

Expected: 无命中。

---

### Task 3: 处理节点5.5重复文件

**Files:**
- Modify: `E:\Codex\New_rules\.review\IT产品经理工作流-v3\节点5.5-PRD初审\5.5-节点5.5-PRD初审.md`
- Keep: `E:\Codex\New_rules\.review\IT产品经理工作流-v3\节点5.5-PRD初审\规范与模板.md`

- [x] **Step 1: 将重复文件改成指向说明**

保留文件但替换正文，说明正式文件为 `规范与模板.md`，该文件不得作为并行执行入口。

- [x] **Step 2: 校验重复入口风险**

Run:

```powershell
Select-String -LiteralPath 'E:\Codex\New_rules\.review\IT产品经理工作流-v3\节点5.5-PRD初审\5.5-节点5.5-PRD初审.md' -Pattern '正式执行入口|规范与模板.md|不得作为并行执行入口'
```

Expected: 三个关键词均出现。

---

### Task 4: 统一节点7和节点7.5偏差门禁口径

**Files:**
- Modify: `E:\Codex\New_rules\.review\IT产品经理工作流-v3\节点7-原型验收\规范与模板.md`
- Modify: `E:\Codex\New_rules\.review\IT产品经理工作流-v3\节点7.5-原型图确认与PRD回填\规范与模板.md`

- [x] **Step 1: 修正节点7旧编号**

将“进入6.5”改为“进入7.5”，将设计偏差回流节点从 `节点5/5` 改为 `节点5/节点6`。

- [x] **Step 2: 统一偏差处理口径**

节点7.5 中所有“设计偏差清零”改为“设计偏差已关闭或已确认接受”；明确致命/严重必须清零，一般/建议可通过业务确认接受或纳入后续计划。

- [x] **Step 3: 校验偏差口径**

Run:

```powershell
Select-String -LiteralPath 'E:\Codex\New_rules\.review\IT产品经理工作流-v3\节点7-原型验收\规范与模板.md','E:\Codex\New_rules\.review\IT产品经理工作流-v3\节点7.5-原型图确认与PRD回填\规范与模板.md' -Pattern '进入6\.5|节点5/5|设计偏差清零'
```

Expected: 无命中。

---

### Task 5: 修正节点8最终评审门禁

**Files:**
- Modify: `E:\Codex\New_rules\.review\IT产品经理工作流-v3\节点8-全面评审\规范与模板.md`

- [x] **Step 1: 修正 PRD 回流复审节点**

将 PRD 问题回流后的“重新过4.5初审”改为“重新过5.5 PRD初审”。

- [x] **Step 2: 纳入节点4和4.5交付物**

在最终交付物一致性门禁中加入：

```text
可视化设计交付物
图表源文件
节点4.5可视化设计评审报告
```

- [x] **Step 3: 校验节点8旧口径**

Run:

```powershell
Select-String -LiteralPath 'E:\Codex\New_rules\.review\IT产品经理工作流-v3\节点8-全面评审\规范与模板.md' -Pattern '4\.5初审|可视化设计交付物|节点4\.5可视化设计评审报告'
```

Expected: 不出现 `4.5初审`；出现后两个新增交付物关键词。

---

### Task 6: 全局一致性验证

**Files:**
- Verify all Markdown files under `E:\Codex\New_rules\.review\IT产品经理工作流-v3`

- [x] **Step 1: 全局搜索旧编号和冲突入口**

Run:

```powershell
Get-ChildItem -LiteralPath 'E:\Codex\New_rules\.review\IT产品经理工作流-v3' -Recurse -Filter '*.md' | Select-String -Pattern '进入6\.5|6\.5 PRD回填|4\.5初审|节点5/5|节点5图表|设计偏差清零'
```

Expected: 无影响正式执行口径的命中。

- [x] **Step 2: 全局搜索 v3 关键节点**

Run:

```powershell
Get-ChildItem -LiteralPath 'E:\Codex\New_rules\.review\IT产品经理工作流-v3' -Recurse -Filter '*.md' | Select-String -Pattern '节点4\.5|节点5\.5|节点7\.5|节点8'
```

Expected: 关键节点均有合理命中。

- [x] **Step 3: 输出修改结果**

最终回复中说明已修改文件、未修改原 ZIP、残余风险和建议下一步。
