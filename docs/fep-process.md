# FEP — FlagOS Enhancement Proposal 流程

## 什么是 FEP

FEP（FlagOS Enhancement Proposal）是 FlagOS 的 Feature 管理机制。每个需要跟踪的 Feature 对应一个 FEP Issue，用于描述做什么、为什么做、怎么验收，并关联所有实现 PR。

**工具链**：GitHub Issue + Milestone（`FlagOS-AI/community` 仓库）

- **Milestone** = 版本的 Feature 篮子（如 `FlagOS 2.1`），圈定本版本的 Feature 范围
- **FEP Issue** = Feature 的载体，每个 Feature 一个 Issue，关联所有 PR

## 什么时候需要写 FEP

| 场景 | 需要 FEP？ |
|------|-----------|
| 跨 2 个以上仓库的 Feature | **必须** |
| 新增芯片支持 | **必须** |
| 新增模块/仓库 | **必须** |
| 模块级别的重要功能/新特性 | **推荐** |
| 单仓库内的小 Feature / Bugfix | 不需要，在对应仓库 Issue 跟踪 |
| 文档改进 | 不需要 |

## FEP 模板

在 [community 仓库创建 Issue](https://github.com/FlagOS-AI/community/issues/new/choose)，选择 **FEP** 模板，按表单填写：

```
标题：[FEP][模块名] Feature 简述
Owner：@xxx
模块：FlagGems / FlagTree / FlagCX / ...
优先级：P0 / P1 / P2
目标版本：FlagOS 2.1

描述：做什么 + 为什么做
验收标准：checklist
关联 PR：checklist
测试计划：如何验证
跨模块依赖：（如有）
```

## Feature 优先级

| 级别 | 含义 | Freeze 时处理 |
|------|------|--------------|
| **P0 Must Have** | 版本核心卖点 | 必须保留，做不完则延期版本 |
| **P1 Should Have** | 重要但非核心 | 尽力完成，做不完降级到下版本 |
| **P2 Nice to Have** | 锦上添花 | Freeze 时优先砍掉 |

## FEP 生命周期

```
Open → In Progress → Done / Deferred
```

| 状态 | 含义 | 操作 |
|------|------|------|
| **Open** | 已提出，等待排期或 Review | 新建 FEP 后的初始状态 |
| **In Progress** | 开发进行中 | Owner 开始实现，关联 PR |
| **Done** | 验收标准全部满足 | 关闭 Issue |
| **Deferred** | 延期到后续版本 | 移至下一个 Milestone，标注原因 |

## 大 Feature 管理

### 跨模块 Feature

一个 FEP Issue 做**总控台**：
- Issue 描述中列出各模块的工作拆分和负责人
- 所有 PR 用 checklist 按模块跟踪进度
- 跨模块依赖在"跨模块依赖"字段中明确标注

### 跨版本 Feature

对于需要多个版本完成的大 Feature：
- 按 Phase 拆分，每个 Phase 一个 FEP Issue
- 标题标注 Phase：`[FEP][FlagCX] EP 通信优化 Phase 1`
- 各 Phase 的 FEP 分别关联到对应版本的 Milestone

## 协作分工

| 角色 | 职责 |
|------|------|
| **模块 Owner** | 写 FEP、更新状态、关联 PR、确保验收标准达成 |
| **测试团队** | 协助补充测试计划、编写测试用例、执行验证 |
| **Release Manager** | 追踪全局 Milestone 进度、催进度、Go/No-Go 决策 |

## Milestone 使用规范

- 每个 FlagOS 版本对应一个 Milestone（如 `FlagOS 2.1`）
- Milestone 设置 deadline（目标发布日期）
- 所有计划纳入该版本的 FEP 都关联到对应 Milestone
- Release Manager 通过 Milestone 视图追踪整体进度

## Label 规范

| Label | 用途 |
|-------|------|
| `FEP` | 标识 FEP Issue（模板自动添加） |
| `P0` / `P1` / `P2` | 优先级 |
| `module/FlagGems` | 模块标识 |
| `module/FlagTree` | 模块标识 |
| `module/FlagCX` | 模块标识 |
| `module/FlagScale` | 模块标识 |
| `module/FlagRelease` | 模块标识 |
| `module/KernelGen` | 模块标识 |
| `module/FlagPerf` | 模块标识 |
| `module/FlagAttention` | 模块标识 |
| `module/cross-cutting` | 跨模块 Feature |
