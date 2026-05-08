


# LLM Wiki Template

基于 Andrej Karpathy LLM WIKI 理念构建的个人知识库模板

## 简介

本项目采用 **Raw/Wiki/Schema** 三层架构设计，摒弃传统 RAG 临时检索模式，以大模型编译沉淀结构化 Markdown 维基，支持 AI 自主维护、知识互联与持续迭代，可快速搭建专属 LLM 知识库。

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

### 目录结构

```
llmwiki-template/
├── AGENTS.md              # 智能体指南
├── README.md               # 项目说明
├── raw/                   # Raw 层 - 原始数据
│   ├── articles/          # 原始文章
│   ├── assets/            # 资源文件
│   ├── notes/             # 原始笔记
│   └── papers/            # 论文资料
├── templates/             # 知识页面模板
│   ├── article-template.md
│   ├── concept-template.md
│   ├── entity-template.md
│   ├── note-template.md
│   ├── paper-template.md
│   └── source-template.md
└── wiki/                  # Wiki 层 - 维基页面
    ├── concepts/          # 概念页面
    ├── entities/         # 实体页面
    ├── sources/          # 来源页面
    ├── index.md          # 知识库首页
    └── log.md            # 活动日志
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
| source | 来源引用 | wiki/sources/ |
| note | 个人笔记 | raw/notes/ |
| article | 文章 | raw/articles/ |
| paper | 论文 | raw/papers/ |

## 快速开始

### 1. 环境配置

1. 克隆本仓库到本地
2. 配置 LLM 环境（如 OpenAI API、Ollama 等）
3. 初始化知识库结构

### 2. 使用流程

1. **添加原始数据**: 将文档放入 `raw/` 目录下对应子目录
2. **运行 INGEST**: 使用 LLM 编译工具将原始文档转换为 Wiki 层页面
3. **定义关联**: 在 Schema 层定义知识之间的关联关系
4. **知识查询**: 通过 QUERY 命令进行知识检索

### 3. 页面编写规范

每个 Wiki 页面需包含 YAML Frontmatter：

```yaml
---
status: draft/reviewed
tags: []
related: []
---
```

## 模板说明

根据知识类型选择对应模板：

- **article-template.md**: 长篇文章
- **concept-template.md**: 概念定义
- **entity-template.md**: 实体对象
- **note-template.md**: 个人笔记
- **paper-template.md**: 论文笔记
- **source-template.md**: 来源引用

## 参与贡献

1. Fork 本仓库
2. 新建特性分支：`feat_xxx`
3. 提交变更
4. 发起 Pull Request

## 许可证

MIT License