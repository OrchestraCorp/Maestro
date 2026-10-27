<p align="center"><img src="assets/brand/maestro.png" width="144" height="144" alt="Maestro logo"></p>

# Maestro

[English](README.md) | 中文

Maestro 是 OrchestraCorp 面向人员与 AI（人工智能）agent（智能体）协作的工作台。产品方向涵盖企业工作协调、知识整理、决策与管理，由人员监督 agent 操作，由 Stage 执行业务权限控制。

Maestro 是独立维护的 [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) fork，基于 [Cordis](https://github.com/cordiverse/cordis) 构建，源码采用 [MIT 许可证](LICENSE)。

## 开发状态

Maestro 处于早期开发者预览阶段。企业集成与产品交付仍在开发中，API 和持久化数据可能发生变化。

| 领域 | 当前范围 |
|---|---|
| `main` | 上游运行时基础与 OrchestraCorp 产品文档。 |
| [`codex/maas-connections`](https://github.com/OrchestraCorp/Maestro/tree/codex/maas-connections) | Maestro 品牌界面，以及支持 Chat Completions、Responses 和 Anthropic Messages 的模型连接设置；产品构建与发布规划。 |
| Stage 集成 | Stage 登录、企业管理中心、业务连接器和 Stage 实例切换仍待集成。 |
| 产品验收 | 真实模型的效果、持续运行的稳定性、打包发布及完整企业业务闭环仍需验收。 |

MaaS 的效果与稳定性是产品重点。连接测试成功仅说明被测试的请求路径可用。已实现范围和待完成工作见开发分支的[模型连接行为](https://github.com/OrchestraCorp/Maestro/blob/codex/maas-connections/ORCHESTRA_MAAS.md)与[构建发布规则](https://github.com/OrchestraCorp/Maestro/blob/codex/maas-connections/ORCHESTRA_BUILD_RELEASE.md)。

## OrchestraCorp 项目

四个仓库承担不同职责，彼此之间的集成正在逐步推进。

| 项目 | 职责 |
|---|---|
| [Stage](https://github.com/OrchestraCorp/Stage) | 提供组织身份、权限、受控操作和审计的企业后端。 |
| [Maestro](https://github.com/OrchestraCorp/Maestro) | 工作协调、知识整理，以及规划中的企业管理体验。 |
| [Virtuoso](https://github.com/OrchestraCorp/Virtuoso) | 员工的个人工作台，通过会话和工具在人员监督下使用 agent 完成日常工作。 |
| [ScoreBook](https://github.com/OrchestraCorp/ScoreBook) | 组织知识、运行规则与可复用的流程模板。 |

Stage 负责业务访问授权。客户端连接、可见工具或模型凭据本身不授予企业权限。详见[产品职责](ORCHESTRA_PRODUCT.md)。

<a id="run"></a>

## 运行

运行 agent 或授予工具访问权限前，请阅读[安全说明](SAFETY.zh.md)。当前通过源码运行 Maestro；以下命令明确选择包含产品界面和模型连接设置的开发分支。

<a id="run-from-source"></a>

### 从源码运行

使用 `package.json` 声明的 Node.js `^22.19.0 || >=24.0.0` 和 pnpm `11.28.5`。

```sh
git clone --branch codex/maas-connections https://github.com/OrchestraCorp/Maestro.git
cd Maestro
pnpm install --frozen-lockfile
pnpm run build
pnpm dsh web
```

Web UI 会打印访问地址，通常为 `http://127.0.0.1:3080`。`pnpm run build` 准备构建产物；`pnpm dsh web` 使用这些产物启动，不重新构建。开发迭代可使用 `pnpm run dev:web`。宿主与启动选项见 [Web UI 指南](docs/user/guide/index.zh.md)和[开发指南](docs/development.zh.md)。

在开发分支中，通过模型连接设置填写提供方 URL、API Key 和模型，再明确选择默认模型。模型调用使用所配置的提供方，并可能产生费用。每位用户需要隔离的运行时；这些设置不提供共享多用户服务，Stage 也不保存这些模型凭据。

## 文档与贡献

- [产品职责与权限](ORCHESTRA_PRODUCT.md)
- [Fork 维护](ORCHESTRA_FORK.md)
- [架构](docs/architecture.zh.md)与[开发](docs/development.zh.md)
- [贡献指南](CONTRIBUTING.zh.md)与 [agent 指令](AGENTS.md)
- 通过 [Maestro Issues](https://github.com/OrchestraCorp/Maestro/issues)提交问题与建议

继承的运行时文档也会介绍上游能力。产品特有的范围与交付状态由 OrchestraCorp 产品文档定义。

## 上游与许可证

Maestro 基于 DeepSeek 的 [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness)和 Cordis 插件架构。OrchestraCorp 独立维护本产品，并保留上游版权声明。

源码采用 [MIT 许可证](LICENSE)，允许在遵守声明保留要求的前提下商用、修改和分发。第三方组件保留各自的许可证，详见 [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)和[内置依赖](vendor/README.md)。
