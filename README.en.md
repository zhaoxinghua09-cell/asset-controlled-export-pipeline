# asset-controlled-export-pipeline · Controlled Asset Export Pipeline

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Agent Skill](https://img.shields.io/badge/Agent%20Skill-SKILL.md-blue.svg)](SKILL.md)
[![Category](https://img.shields.io/badge/category-brand--assets-8a2be2.svg)](#)
[![Version](https://img.shields.io/badge/version-1.0.0-informational.svg)](#)
[![llms.txt](https://img.shields.io/badge/AI--friendly-llms.txt-101E2C.svg)](llms.txt)
[![中文](https://img.shields.io/badge/%E4%B8%AD%E6%96%87-README.md-blue.svg)](README.md)

> Batch-export brand and social design assets from the Ardot canvas into a controlled local library: PNG + SVG on disk, copyright / provenance / license metadata injected (optionally via a local LLM), with a self-describing controlled index.

**Keywords**: 素材批量导出 · 受控素材库 · VI 资料分发 · 版权元数据 · 资产溯源 · PNG/SVG · 元数据注入 · asset export · provenance

This repository is an **Agent Skill distribution package**. The core file `SKILL.md` follows the Agent Skills spec (YAML frontmatter) and packages the method of "素材外发受控分发：双格式落盘 + 元数据注入 + 可追溯索引" into a skill an AI agent can load directly. Drop it into your agent's skills directory (e.g. `~/.workbuddy/skills/`).

- **Category**: 品牌资产 / Brand Assets
- **Version**: 1.0.0
- **Author**: 诺声(Logos)@SynomosAI
- **License**: MIT (see [LICENSE](LICENSE))

---

## Features

- 双格式落盘：PNG + SVG 同时导出，落在受控本地素材库
- 元数据注入：PNG 写 iTXt + XMP，SVG 写 <metadata> RDF（dc:description + mx:aiStatement）
- 可选本地大模型文案：接 localhost:8080 逐张生成中文声明，不可达时回退结构化模板
- 受控索引：在画布存档页生成自描述 _asset_index.json，回答「这张图谁做的、什么时候做的」
- 证据链留痕：导出链路按审计留痕，资产权属按注册方法论登记为可核验属性
- 可复跑：先从 _backup 还原干净原图再注入，避免元数据叠加

---

## Quick Start

Prerequisite: an AI coding assistant / skill runtime that can load Agent Skills. 含可执行 Python 脚本（scripts/）；依赖 pillow，可选本地大模型服务.

```bash
# 1. 克隆本仓库
git clone https://github.com/zhaoxinghua09-cell/asset-controlled-export-pipeline.git
cd asset-controlled-export-pipeline

# 2. 安装依赖（PIL 用于 PNG/XMP 注入）
pip install pillow

# 3. 从 CDN 直链批量下载（urls.json: {node_id: {"png":..,"svg":..}}）
python scripts/download_template.py --map urls.json

# 4. 注入版权 / 溯源元数据（--template = 不调用模型，用结构化模板文案）
python scripts/inject_model_text.py --template
```

Then invoke it in natural language, e.g.:

```text
「素材外发怎么防盗用」
「VI 资料怎么受控分发」
「这张图是谁做的、什么时候做的」
```

---

## Usage

1. Clone this repo, or copy the skill directory into your agent's skills folder.
2. Call the capability via the trigger keywords described in `SKILL.md`.
3. See `SKILL.md` for the full method, boundaries and provenance.

---

## Repository layout

```text
asset-controlled-export-pipeline/
├── README.md            # 本文件（双语）
├── README.en.md         # 英文版说明
├── SKILL.md             # 技能主文件（Agent Skills 规范 · YAML frontmatter）
├── manifest.json        # 技能元数据（名称 / 版本 / 许可 / 描述）
├── scripts/
│   ├── download_template.py   # 从 CDN 直链批量下载 PNG/SVG
│   └── inject_model_text.py   # 注入版权/溯源元数据（可选本地模型）
├── LICENSE              # MIT 许可全文
├── SECURITY.md          # 安全策略
├── CONTRIBUTING.md      # 贡献指南
├── AGENTS.md            # 给 AI Agent 的工作指引
├── llms.txt             # 给 AI 的最小索引（llms.txt 标准）
└── llms-full.txt        # 给 AI 的完整文本
```

---

## License

Released under the **MIT** license. See [LICENSE](LICENSE) for the full text. Attribution: cite this repository `https://github.com/zhaoxinghua09-cell/asset-controlled-export-pipeline` and the rights holder "赵兴华 / Steven Zhao·China". Contact: zhaoxinghua06@126.com ｜ ORCID 0009-0001-0512-1237.

---

## Security

If you find a security issue, report it privately per [SECURITY.md](SECURITY.md); do not disclose it in a public issue.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Keep the `SKILL.md` YAML frontmatter fields compatible when changing this skill.

## Disclaimer

This repository content is a **theoretical stance and tooling exploration**. It does not represent any certified, commercially delivered, or client-served claim. External standards, certifications and clause information are restatements of public sources; independently verify before formal citation. APIs, authorization codes and ambassadors are roadmap items, not yet live.
