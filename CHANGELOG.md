# PhotoCraft 更新日志

本文记录 DynamaxVV fork 自上游基点之后的已提交变更。上游历史发布记录见 [Releases](https://github.com/storytold/photocraft/releases)，本 fork 的范围与验证说明见 [FORK_CHANGES.md](FORK_CHANGES.md)。日期不表示发布了新的应用版本。

## 未发布

### 2026-10-16

- 将主 README 改为中文项目入口，说明 fork 来源、运行方式、自动化入口与当前功能边界。
- 将替换前的 README 保留为 [README.en.md](README.en.md)，在新版中提供入口。
- 新增本更新日志和 [fork 更改说明](FORK_CHANGES.md)。
- 新增[文档导航](docs/README.md)与[文档维护](docs/documentation-maintenance.md)，区分参考文档、生成报告和历史评估。
- 修复共享私有仓库路径被当作公开链接的问题，以及 MCP 手册构建后的失效链接。
- 按已提交的语料测试阈值修正详细路线图中的过时数字，保留原始评估日期；未重新测量专业工作流完成度。

本机维护另清理了 5 个增量缓存目录和 250 项临时文件，保留依赖缓存、验收记录与发布包。此项操作不改变应用功能，也不会在克隆仓库时执行。

原本地工作区中的功能改动尚未合入此 fork，未作为本节的已提交功能列出。
