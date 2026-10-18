# AGENTS.md — 给 AI Agent 的工作指引

本文件面向自动化 AI Agent（编码助手、技能加载器、知识库机器人）。人类读者请看 [README.md](README.md)。

## 这个仓库是什么

`asset-controlled-export-pipeline` 是一个 **Agent Skill 发布包**（分类：品牌资产 / Brand Assets），不是可独立运行的产品。核心资产是 `SKILL.md`（遵循 Agent Skills 规范，带 YAML frontmatter）。把本目录放入 Agent 的技能目录即可让它获得「素材外发受控分发：双格式落盘 + 元数据注入 + 可追溯索引」能力。

## 可用的工作命令

```bash
# 查看技能元数据（名称 / 版本 / 许可 / 描述）
cat manifest.json

# 查看技能全文（触发词、方法、边界）
cat SKILL.md

# 查看项目说明与快速开始
cat README.md
```

含可执行 Python 脚本（scripts/）；依赖 pillow，可选本地大模型服务。

## 约定（Do）

- 修改前先读 `SKILL.md` 的 YAML frontmatter，**保持字段兼容**（`name` / `slug` / `version` / `license` 等）。
- 新增能力写进 `SKILL.md` 正文，并同步更新 `manifest.json` 的描述与版本。
- 方法按「真实参照法」写：结论挂到可复现实测 / 官方文档，不凭感觉断言。

## 禁止（Don't）

- 不要改动 `SKILL.md` / `manifest.json` 的 `copyright` / `author` / `license` 字段，也不要改 `LICENSE` 的版权主体——**权属字段只由维护者变更**。
- 不要在仓库内提交任何密钥、令牌或真实客户数据。
- 不要声称本包「已认证 / 已商用交付 / 已服务特定客户」。

## 边界

素材外发受控分发：双格式落盘 + 元数据注入 + 可追溯索引；不覆盖其未提及的场景。本技能为通用方法论工具，非医疗器械 / 非医疗软件，无疗效或临床声明。
