# LLM Wiki Template

基于 Andrej Karpathy LLM WIKI 理念构建的个人知识库模板。

## 简介

采用 **Raw/Wiki/Schema** 三层架构设计，摒弃传统 RAG 临时检索模式，以大模型编译沉淀结构化 Markdown 维基，支持 AI 自主维护、知识互联与持续迭代。

## 软件架构

```
┌─────────────────────────────────────────────┐
│  Schema 层 - 模式层                         │
│  定义知识库组织结构和关联关系               │
├─────────────────────────────────────────────┤
│  Wiki 层 - 维基层                           │
│  结构化的 Markdown 维基页面                  │
├─────────────────────────────────────────────┤
│  Raw 层 - 原始数据层                        │
│  存储未经处理的原始文档和信息              │
└─────────────────────────────────────────────┘
```

## 目录结构

```
llmwiki-template/
├── AGENTS.md              # 智能体核心规则
├── CLAUDE.md              # Claude Code 入口文件
├── README.md              # 项目说明
├── raw/                   # Raw 层 - 原始数据（只读不修改）
│   ├── articles/          # 收集的文章、剪藏内容
│   ├── assets/            # 资源文件
│   ├── notes/             # 原始笔记
│   └── papers/            # 论文资料
├── templates/            # 知识页面模板
│   ├── article-template.md
│   ├── concept-template.md
│   ├── entity-template.md
│   ├── note-template.md
│   ├── paper-template.md
│   └── source-template.md
└── wiki/                  # Wiki 层 - 维基页面（AI 维护）
    ├── concepts/          # 概念页面
    ├── entities/          # 实体页面
    ├── sources/           # 来源页面
    ├── analysis/          # 分析页面
    ├── index.md           # 知识库首页
    └── log.md             # 活动日志
```

## 核心功能

### 智能体工作流

- **INGEST**: 处理原材料 → 生成知识库页面
- **QUERY**: 基于知识库回答问题
- **LINT**: 检查知识库完整性

### 知识类型支持

| 类型 | 说明 | 存放位置 |
|------|------|----------|
| concept | 概念定义 | wiki/concepts/ |
| entity | 实体对象 | wiki/entities/ |
| source-summary | 来源摘要 | wiki/sources/ |
| analysis | 对比分析 | wiki/analysis/ |
| note | 个人笔记 | raw/notes/ |
| article | 文章 | raw/articles/ |
| paper | 论文 | raw/papers/ |

## 页面规范

### YAML Frontmatter

```yaml
---
title: 页面标题
tags: [标签1, 标签2]
source: raw/xxx.md  # 仅用于源摘要页面
created: 2026-xx-xx
updated: 2026-xx-xx
status: draft/reviewed
---
```

### Markdown 格式

- 禁用分隔符：只用标题分层，不使用 `---`
- ATX 风格标题：`#`、`##`、`###`
- 无序列表：`-`
- 有序列表：`1.`
- 内部链接：`[[页面名称]]` 或 `[[页面名称|显示文本]]`
- 外部链接：`[文本](url)`

### 命名约定

| 类型 | 规范 | 示例 |
|------|------|------|
| 标签 | 小写、中划线 | `智慧校园`, `Qt开发` |
| 页面标题 | 中文、描述性 | `智慧校园方案设计` |
| 文件路径 | 与标题一致 | `wiki/concepts/双向链接.md` |

## 快速开始

### 1. 环境配置

1. 克隆本仓库到本地
2. 配置 Claude Code 或其他 LLM 环境
3. 打开 Vault，AI 将自动读取 AGENTS.md 规则

### 2. 使用流程

1. **添加原始数据**：将文档放入 `raw/` 目录下对应子目录
2. **运行 INGEST**：使用 `/ingest` 命令将原始文档转换为 Wiki 层页面
3. **定义关联**：在相关页面间添加双向链接
4. **知识查询**：直接提问，AI 将基于 wiki/ 内容回答

### 3. 核心约束

- **只读 raw/**：人类原始素材不可修改
- **只写 wiki/**：所有 AI 内容更新发生在 wiki/ 目录
- **禁止幻觉**：只基于本地笔记内容，不编造信息
- **双向链接**：A 链接到 B，B 也应链接回 A

## 模板说明

根据知识类型选择对应模板：

- **article-template.md**: 长篇文章
- **concept-template.md**: 概念定义
- **entity-template.md**: 实体对象
- **note-template.md**: 个人笔记
- **paper-template.md**: 论文笔记
- **source-template.md**: 来源引用

## 许可证

MIT License