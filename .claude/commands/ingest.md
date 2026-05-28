# INGEST - 处理原材料

处理 `raw/` 中的原始素材，生成对应的 `wiki/` 结构化页面。

## 输入

`/ingest <文件路径或关键词>`

示例：`/ingest raw/articles/我的文章.md`

## 工作流程

1. **读取原始文件**：完整读取指定文件
2. **创建源摘要**：在 `wiki/sources/` 创建/更新源摘要页面
3. **提取概念**：提炼关键概念，在 `wiki/concepts/` 创建/更新概念页面
4. **识别实体**：识别人物/工具/项目，在 `wiki/entities/` 创建/更新实体页面
5. **添加链接**：在相关页面之间添加双向链接
6. **更新索引**：更新 `wiki/index.md` 添加新条目
7. **记录日志**：在 `wiki/log.md` 记录操作

## 规则

- **只读 raw/**：不修改原始文件
- **保留 frontmatter**：更新页面时保留 YAML frontmatter
- **禁止幻觉**：只写原材料中存在的内容
- **双向链接**：A 链接到 B，B 也应链接回 A

## 输出格式

```
## INGEST 完成

- 源摘要：wiki/sources/xxx.md
- 新增概念：wiki/concepts/xxx.md (N个)
- 新增实体：wiki/entities/xxx.md (N个)
- 添加链接：N对双向链接
- 日志：wiki/log.md
```