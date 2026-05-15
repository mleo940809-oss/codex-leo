# 会话记录：Weixin摇一摇 PRD 角色用例图与流程图生成总结

**日期**：2026-05-12  
**范围**：Weixin摇一摇 PRD 2.1.0 - 2.1.6 图表生成、保存、归档与章节引用更新

## 本次目标

围绕 Weixin摇一摇 PRD 的多个章节，按“先出效果图，再生成可编辑源文件，再更新章节引用”的方式，持续补齐角色用例图与流程图。

## 已完成事项

### 1. 角色用例图与流程图的图表生成

已为以下章节生成并落盘了独立命名的 PNG 与 `.drawio` 源文件：

- `2.1.1.2.1 角色用例图`
  - [Weixin摇一摇_活动列表页角色用例图_v1.0_20260511.png](E:/Codex/New_rules/docs/versions/Weixin摇一摇/Weixin摇一摇_活动列表页角色用例图_v1.0_20260511.png)
  - [Weixin摇一摇_活动列表页角色用例图_v1.0_20260511.drawio](E:/Codex/New_rules/docs/versions/Weixin摇一摇/Weixin摇一摇_活动列表页角色用例图_v1.0_20260511.drawio)

- `2.1.2.2.1 角色用例图`
  - [Weixin摇一摇_活动新增页角色用例图_v1.0_20260511.png](E:/Codex/New_rules/docs/versions/Weixin摇一摇/Weixin摇一摇_活动新增页角色用例图_v1.0_20260511.png)
  - [Weixin摇一摇_活动新增页角色用例图_v1.0_20260511.drawio](E:/Codex/New_rules/docs/versions/Weixin摇一摇/Weixin摇一摇_活动新增页角色用例图_v1.0_20260511.drawio)

- `2.1.3.2.1 角色用例图`
  - [Weixin摇一摇_活动编辑页角色用例图_v1.0_20260511.png](E:/Codex/New_rules/docs/versions/Weixin摇一摇/Weixin摇一摇_活动编辑页角色用例图_v1.0_20260511.png)
  - [Weixin摇一摇_活动编辑页角色用例图_v1.0_20260511.drawio](E:/Codex/New_rules/docs/versions/Weixin摇一摇/Weixin摇一摇_活动编辑页角色用例图_v1.0_20260511.drawio)

- `2.1.4.2.1 角色用例图`
  - [Weixin摇一摇_活动修改页角色用例图_v1.0_20260511.png](E:/Codex/New_rules/docs/versions/Weixin摇一摇/Weixin摇一摇_活动修改页角色用例图_v1.0_20260511.png)
  - [Weixin摇一摇_活动修改页角色用例图_v1.0_20260511.drawio](E:/Codex/New_rules/docs/versions/Weixin摇一摇/Weixin摇一摇_活动修改页角色用例图_v1.0_20260511.drawio)

- `2.1.5.2.1 角色用例图`
  - [Weixin摇一摇_活动详情页角色用例图_v1.0_20260511.png](E:/Codex/New_rules/docs/versions/Weixin摇一摇/Weixin摇一摇_活动详情页角色用例图_v1.0_20260511.png)
  - [Weixin摇一摇_活动详情页角色用例图_v1.0_20260511.drawio](E:/Codex/New_rules/docs/versions/Weixin摇一摇/Weixin摇一摇_活动详情页角色用例图_v1.0_20260511.drawio)

- `2.1.6.2.1 角色用例图`
  - [Weixin摇一摇_批次管理页角色用例图_v1.0_20260511.png](E:/Codex/New_rules/docs/versions/Weixin摇一摇/Weixin摇一摇_批次管理页角色用例图_v1.0_20260511.png)
  - [Weixin摇一摇_批次管理页角色用例图_v1.0_20260511.drawio](E:/Codex/New_rules/docs/versions/Weixin摇一摇/Weixin摇一摇_批次管理页角色用例图_v1.0_20260511.drawio)

### 2. PRD 章节引用已更新

已把上述章节中的图表引用切换为新文件名，避免继续引用旧的统一角色图文件：

- [Weixin摇一摇_PRD_v2.9_20260511.md](E:/Codex/New_rules/docs/versions/Weixin摇一摇/Weixin摇一摇_PRD_v2.9_20260511.md)

### 3. 命名规则确认

本次统一采用页面级独立命名，避免与总角色图冲突：

- 总角色图保留原名：`Weixin摇一摇_角色用例图_v1.7_20260511.png`
- 页面级图新增前缀：
  - `活动列表页`
  - `活动新增页`
  - `活动编辑页`
  - `活动修改页`
  - `活动详情页`
  - `批次管理页`

## 重要结论

1. 对这类 PRD 图，`PNG` 负责最终视觉效果，`drawio` 负责可编辑源文件。
2. 直接手写 `.drawio` XML 时，打开后的排版会与效果图有偏差，这是正常现象，不是文件损坏。
3. 后续如果继续产这类图，最好继续保持“先效果图，后落盘源文件，再更新 PRD 引用”的顺序。
4. 页面级图文件必须使用独立命名，不能再复用总角色图文件名。

## 当前未完成项

- `2.1.6.2.2 产品流程图` 的效果图已经生成，但尚未落盘为正式 PNG / `.drawio` 文件，也尚未更新 PRD 引用。

## 后续建议

1. 继续补齐 `2.1.6.2.2 产品流程图` 的正式文件与引用。
2. 后续同类图表沿用本次命名规范和章节更新方式。
3. 如需完全一致的可编辑源文件，需接受 draw.io 渲染重排，或者改用更适合的矢量交付方式。
