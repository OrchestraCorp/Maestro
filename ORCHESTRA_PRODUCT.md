# Maestro

Maestro 是 OrchestraCorp 中连接 ScoreBook 与 Stage 的首脑 Agent。

Maestro 在本目录独立维护完整源码、依赖、版本和发布流程，自行选择与同步 DeepSeek Harness 上游版本。Virtuoso 使用另一份独立仓库；两者之间没有强制共享的 Runtime 仓库、工作目录或依赖。

## 主要职责

- 理解 Stage 中的工作上下文和组织事件。
- 从授权范围内的工作记录、决策和 Repo 中整理产物。
- 维护文档、知识、协议和归档提案。
- 协调 Stage 与 ScoreBook 的版本、证据和发布准备。
- 将不确定、冲突和需要人判断的事项生成决策卡。

## 权限边界

- Maestro 不自动拥有全仓读取、治理合并或规则生效权。
- Maestro 的读取和写入范围按任务、领域、数据分类和有效期限制。
- Maestro 可以在授权工作区编辑文件、创建分支和提交 MR；合并与生效另行控制。
- Maestro 的判断、来源、产物和失败必须回写 Stage 事件。

Maestro 是语义整理与协调层，不是无限权限的同步机器人。

## 仓库与实现状态

当前已从核验过的上游提交建立独立本地 fork，拥有自己的 `.git`、`main`、上游引用和基线标签。原有职责与权限设计保存在本文件；根目录 `README.md` 与 `README.zh.md` 保留上游说明。

当前基于上游运行时，已提供 [DSH 原生模型连接](ORCHESTRA_MAAS.md)；已加入产品 Profile/目标设计清单、校验器和只读构建计划。实际产品 Profile、Stage 登录、业务界面和企业连接器尚未实现，完整企业业务闭环尚未验证；模型接入代码不代表真实模型验证或产品发布已通过。产品 `origin` 指向 GitHub 私有仓库 `OrchestraCorp/Maestro`。

[仓库维护说明](ORCHESTRA_FORK.md)记录来源、历史状态和独立同步规则。

[Profile、构建与发布规则](ORCHESTRA_BUILD_RELEASE.md)是本产品代码设计与后续交付的维护依据。
