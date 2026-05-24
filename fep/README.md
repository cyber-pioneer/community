# FEP — FlagOS Enhancement Proposal

## 什么是 FEP

FEP 是 FlagOS 的 Feature 管理机制。每个跨模块或较大 Feature 对应一个 FEP：

- **FEP 设计文档**：markdown 文件，放在对应 `sig-*` 目录下，通过 PR 提交和 review，是设计意图的持久记录
- **FEP Issue**：GitHub Issue，用于追踪状态、关联 PR、日常讨论

**工具链**：GitHub Issue（追踪）+ Markdown 文件（设计文档）+ Milestone（版本管理）

## SIG 分组

| SIG | 覆盖模块 |
|-----|---------|
| `sig-operator` | FlagGems, FlagAttention, FlagFFT, FlagSparse, FlagDNN, FlagBLAS, FlagTensor, FlagAudio |
| `sig-compiler` | FlagTree |
| `sig-network` | FlagCX |
| `sig-framework` | PyTorch-Plugin-FL, vllm-plugin-FL, sglang-plugin-FL, TransformerEngine-FL, Megatron-LM-FL, verl-FL |
| `sig-training` | FlagScale |
| `sig-kernelgen` | KernelGen |
| `sig-embodied` | FlagOS-Robo |
| `sig-ai4s` | FlagQuantum |
| `sig-benchmark` | FlagPerf |
| `sig-skills` | Skills |
| `sig-tools` | FlagRelease |
| `sig-architecture` | 跨模块 Feature、流程变更 |

## 什么时候需要 FEP

| 场景 | 需要 FEP？ |
|------|-----------|
| 跨模块 Feature | **必须** |
| 新增芯片支持 | **必须** |
| 新增模块/仓库 | **必须** |
| 模块级重要新特性 | **推荐** |
| 单仓库小 Feature / Bugfix | 不需要 |
| 文档改进 | 不需要 |

## FEP 生命周期

```
Provisional ──→ Implementable ──→ Implemented
     │                                ↑
     ├──→ Deferred ──────────────────┘
     └──→ Rejected
```

| 状态 | 含义 | 操作 |
|------|------|------|
| **Provisional** | 草稿，SIG 内部讨论中 | 设计文档还在迭代，未正式批准 |
| **Implementable** | 设计已批准，可以开工 | SIG 负责人 approve PR 后进入此状态 |
| **Implemented** | 代码合入，验收通过 | 关闭 Issue |
| **Deferred** | 延期到后续版本 | 移至下一个 Milestone |
| **Rejected** | 不做了 | 关闭，保留设计文档作为历史记录 |

## 流程

### 1. 创建 FEP 设计文档

在对应 `sig-*` 目录下创建 markdown 文件，命名 `NNNN-title.md`：

- `NNNN` 为 GitHub Issue 号（先用 `draft` 占位，开好 Issue 后补上）
- `title` 为简短英文描述，用 `-` 连接

参考 [fep-template/README.md](fep-template/README.md) 模板填写。

### 2. 创建 FEP Issue

使用 [FEP Issue 模板](https://github.com/FlagOS-AI/community/issues/new?assignees=&labels=FEP&template=fep.yml) 开 tracking issue：

- 标题：`[FEP][sig-xxx] Feature 简述`
- 在描述中贴上设计文档的链接
- 关联到目标版本的 Milestone

### 3. 提 PR 迭代设计文档

- 将 FEP 文件通过 PR 提交到 `fep/sig-xxx/` 目录
- SIG 负责人和涉及方在 PR 中 review
- **"Merge early and iterate"**：先合入高层设计，细节后续 PR 补充
- 合入后状态标记为 `Implementable`

### 4. 实现

- 在 FEP Issue 中通过 checklist 跟踪关联 PR
- 设计有变化时更新 FEP 文档并提新 PR
- 验收标准全部满足后，Issue 关闭，状态变为 `Implemented`

## 角色

| 角色 | 职责 |
|------|------|
| **FEP Owner** | 写 FEP、更新状态、驱动实现、确保验收 |
| **SIG 负责人**（OWNERS） | Review 和 approve FEP 设计文档 |
| **Release Manager** | 追踪 Milestone 进度、Go/No-Go 决策 |

## Milestone 使用规范

- 每个 FlagOS 版本对应一个 Milestone（如 `FlagOS 2.1`）
- Milestone 设置 deadline
- 所有计划纳入该版本的 FEP 关联到对应 Milestone
- Release Manager 通过 Milestone 视图追踪整体进度

## Label 规范

| Label | 用途 |
|-------|------|
| `FEP` | 标识 FEP Issue（模板自动添加） |
| `sig-operator` | SIG 标识 |
| `sig-compiler` | SIG 标识 |
| `sig-network` | SIG 标识 |
| `sig-framework` | SIG 标识 |
| `sig-training` | SIG 标识 |
| `sig-kernelgen` | SIG 标识 |
| `sig-embodied` | SIG 标识 |
| `sig-ai4s` | SIG 标识 |
| `sig-benchmark` | SIG 标识 |
| `sig-skills` | SIG 标识 |
| `sig-tools` | SIG 标识 |
| `sig-architecture` | SIG 标识 |
