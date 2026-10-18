# asset-controlled-export-pipeline · 受控资产导出管线

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Agent Skill](https://img.shields.io/badge/Agent%20Skill-SKILL.md-blue.svg)](SKILL.md)
[![Category](https://img.shields.io/badge/category-brand--assets-8a2be2.svg)](#)
[![Version](https://img.shields.io/badge/version-1.0.0-informational.svg)](#)
[![Multilingual](https://img.shields.io/badge/i18n-8%20languages-brightgreen.svg)](#)
[![llms.txt](https://img.shields.io/badge/AI--friendly-llms.txt-101E2C.svg)](llms.txt)
[![English](https://img.shields.io/badge/English-README.en.md-blue.svg)](README.en.md)

> 把 Ardot 画布上的品牌 / 社媒设计资产批量导出为受控本地素材库——PNG + SVG 双格式落盘，自动注入版权 / 溯源 / 许可元数据（可选接本地大模型逐张生成中文声明），并生成自描述受控索引。
> Batch-export brand and social design assets from the Ardot canvas into a controlled local library: PNG + SVG on disk, copyright / provenance / license metadata injected (optionally via a local LLM), with a self-describing controlled index.

SynomosAI 四支柱体系：**身份（Identity）· 溯源（Traceability）· 治理（Governance）· 共生（Symbiosis）**——当 AI 进入商业，可信是唯一的硬通货。

**关键词 / Keywords**：素材批量导出 · 受控素材库 · VI 资料分发 · 版权元数据 · 资产溯源 · PNG/SVG · 元数据注入 · asset export · provenance

本仓库是一个 **Agent Skill 发布包**：核心文件 `SKILL.md` 遵循 Agent Skills 规范（YAML frontmatter），把「素材外发受控分发：双格式落盘 + 元数据注入 + 可追溯索引」的方法固化为可被 AI Agent 直接加载的技能。可直接放入主流 AI Agent（如 WorkBuddy）的技能目录使用。

- **分类 / Category**：品牌资产 / Brand Assets
- **版本 / Version**：1.0.0
- **署名 / Author**：诺声(Logos)@SynomosAI
- **许可 / License**：MIT（详见仓库 [LICENSE](LICENSE)）

---

## ✨ 特性 / Features

- 双格式落盘：PNG + SVG 同时导出，落在受控本地素材库
- 元数据注入：PNG 写 iTXt + XMP，SVG 写 <metadata> RDF（dc:description + mx:aiStatement）
- 可选本地大模型文案：接 localhost:8080 逐张生成中文声明，不可达时回退结构化模板
- 受控索引：在画布存档页生成自描述 _asset_index.json，回答「这张图谁做的、什么时候做的」
- 证据链留痕：导出链路按审计留痕，资产权属按注册方法论登记为可核验属性
- 可复跑：先从 _backup 还原干净原图再注入，避免元数据叠加

---

## 🚀 快速开始 / Quick Start

前置：一个能加载 Agent Skill 的 AI 编码助手 / 技能运行时；含可执行 Python 脚本（scripts/）；依赖 pillow，可选本地大模型服务。

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

跑通后，直接用自然语言发起调用，例如：

```text
「素材外发怎么防盗用」
「VI 资料怎么受控分发」
「这张图是谁做的、什么时候做的」
```

---

## 📖 使用方式 / Usage

1. 克隆本仓库，或将技能目录放入 Agent 技能目录（如 `~/.workbuddy/skills/`）；
2. 按 `SKILL.md` 的描述与触发词调用对应能力；
3. 详细方法、边界与治理溯源见 `SKILL.md` 正文。

> 若要逐张生成中文声明文案，去掉 --template（默认尝试调用 localhost:8080，失败自动回退模板）。

---

## 📁 仓库结构 / Repository layout

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

## 许可说明 · License Notice

- **权利状态**：本仓库以 **MIT 许可** 许可发布，可依该许可证条款自由使用、修改与再分发。
- **引用建议**：引用时请标注仓库名与原文链接 `https://github.com/zhaoxinghua09-cell/asset-controlled-export-pipeline`
  与权利人「赵兴华 / Steven Zhao·China」。
- **品牌状态限定**：MedXpert、SynomosAI、LGD 等为相关项目标识，
  **均未申请实体注册、未申请商标注册**；出现仅作来源标识，
  不构成对法人实体或商标权的任何主张。
- **完整条款**：见仓库根目录 [LICENSE](LICENSE)。
- **联系**：zhaoxinghua06@126.com ｜ ORCID 0009-0001-0512-1237

---

## 🔒 安全 / Security

如发现安全问题，请按 [`SECURITY.md`](SECURITY.md) 的方式私下报告，不要在公开 issue 中披露。

## 🤝 贡献 / Contributing

欢迎按 [`CONTRIBUTING.md`](CONTRIBUTING.md) 提交改进。本仓库为技能发布包，改动请保持 `SKILL.md` 的 YAML frontmatter 字段兼容（`name` / `slug` / `version` / `license` 等）。

## 免责声明

本仓库内容为**理论站位与工具化探索**，不代表任何已获认证、已商业化交付或已服务特定客户的声明；文中涉及的外部标准、认证与条款信息为公开资料转述，正式引用前请**独立核实**。API、授权码与形象大使等为路线图（roadmap）事项，尚未上线。
