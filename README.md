<p align="center"><img src="assets/brand/maestro.png" width="144" height="144" alt="Maestro logo"></p>

# Maestro

English | [中文](README.zh.md)

Maestro is OrchestraCorp's coordination workspace for people working with AI agents. Its product direction brings together enterprise work, knowledge, decisions and administration, with people supervising agent actions and Stage enforcing business permissions.

Maestro is an independently maintained fork of [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness), built on [Cordis](https://github.com/cordiverse/cordis). The source is available under the [MIT license](LICENSE).

## Development status

Maestro is an early developer preview. Enterprise integration and product delivery are under development; APIs and stored data may change.

| Area | Current scope |
|---|---|
| `main` | The upstream runtime foundation and OrchestraCorp product documentation. |
| [`codex/maas-connections`](https://github.com/OrchestraCorp/Maestro/tree/codex/maas-connections) | Maestro branding and model connection settings for Chat Completions, Responses and Anthropic Messages; product build and release planning. |
| Stage integration | Stage sign-in, enterprise administration, business connectors and switching between Stage instances remain planned integration work. |
| Product acceptance | Real-provider model quality, sustained reliability, packaged releases and the complete enterprise workflow still require acceptance testing. |

MaaS quality and reliability are product priorities. A successful connection test establishes only that the tested request path works. See the development branch's [model connection behavior](https://github.com/OrchestraCorp/Maestro/blob/codex/maas-connections/ORCHESTRA_MAAS.md) and [build and release rules](https://github.com/OrchestraCorp/Maestro/blob/codex/maas-connections/ORCHESTRA_BUILD_RELEASE.md) for the implemented scope and remaining work.

## OrchestraCorp projects

The four repositories have distinct responsibilities. Their integrations are being developed incrementally.

| Project | Responsibility |
|---|---|
| [Stage](https://github.com/OrchestraCorp/Stage) | Enterprise backend for organization identity, permissions, controlled operations and audit. |
| [Maestro](https://github.com/OrchestraCorp/Maestro) | Coordination workspace, knowledge organization and the planned enterprise administration experience. |
| [Virtuoso](https://github.com/OrchestraCorp/Virtuoso) | The employee workspace for conversations, tools and everyday work with agents under human supervision. |
| [ScoreBook](https://github.com/OrchestraCorp/ScoreBook) | Organizational knowledge, operating rules and reusable process templates. |

Stage remains the authority for business access. A client connection, visible tool or model credential does not grant enterprise permissions. See the [product responsibilities](ORCHESTRA_PRODUCT.md).

## Run

Review the [safety notice](SAFETY.md) before running agents or granting tool access. The source checkout is the current Maestro entry point; the commands below select the development branch containing the product interface and model connection settings.

### Run from source

Use Node.js `^22.19.0 || >=24.0.0` and pnpm `11.28.5` as declared in `package.json`.

```sh
git clone --branch codex/maas-connections https://github.com/OrchestraCorp/Maestro.git
cd Maestro
pnpm install --frozen-lockfile
pnpm run build
pnpm dsh web
```

The Web UI prints its address, normally `http://127.0.0.1:3080`. `pnpm run build` prepares the artifacts; `pnpm dsh web` launches them without rebuilding. For source iteration, use `pnpm run dev:web`. See the [Web UI guide](docs/user/guide/index.md) and [development guide](docs/development.md) for host and launch options.

In the development branch, configure your provider URL, API key and model through model connection settings, then explicitly choose a default model. Model calls use the configured provider and may incur charges. Each user needs an isolated runtime; a shared multi-user service is not provided by these settings, and Stage does not store these model credentials.

## Documentation and contribution

- [Product responsibilities and permissions](ORCHESTRA_PRODUCT.md)
- [Fork maintenance](ORCHESTRA_FORK.md)
- [Architecture](docs/architecture.md) and [development](docs/development.md)
- [Contribution guide](CONTRIBUTING.md) and [agent instructions](AGENTS.md)
- [Maestro issues](https://github.com/OrchestraCorp/Maestro/issues) for bug reports and proposals

The inherited runtime documentation also describes upstream capabilities. Product-specific scope and delivery status are defined by OrchestraCorp's product documents.

## Upstream and license

Maestro builds on DeepSeek's [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) and the Cordis plugin architecture. OrchestraCorp maintains this product independently and retains upstream copyright notices.

The source is licensed under [MIT](LICENSE), allowing commercial use, modification and redistribution subject to its notice requirements. Third-party components retain their own licenses; see [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) and [vendored dependencies](vendor/README.md).
