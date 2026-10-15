# PhotoCraft 文档导航

按任务选择入口。文档中的版本、日期和验收范围决定其适用性；菜单已接入命令不代表行为已与 Photoshop 完全一致。

## 使用与开发

| 任务 | 入口 |
|---|---|
| 了解项目、安装与下载 | [项目说明](../README.md) |
| 查看本 fork 修改 | [更新日志](../CHANGELOG.md)、[更改说明](../FORK_CHANGES.md) |
| 按章节阅读手册 | [文档手册目录](../book/src/SUMMARY.md) |
| 编译、运行与测试 | [开发指南](development.md) |
| 修改代码与新增命令 | [贡献指南](contributing.md)、[代理与贡献者规则](../AGENTS.md) |
| 理解分层与文档模型 | [架构](architecture.md)、[实现决策](decisions.md) |
| 调整界面 | [UI 设计](ui-design.md)、[本地化](localization.md) |
| 用代理驱动应用 | [控制协议](control-protocol.md)、[MCP](mcp.md) |
| 开发插件 | [插件接口](plugins.md) |
| 打包与发布 | [发布指南](releasing.md) |
| 检查文档与管理构建缓存 | [文档维护](documentation-maintenance.md) |
| 报告安全问题 | [安全政策](../SECURITY.md) |

## 进度与证据

- [一页路线图](../ROADMAP.md)：总体目标与估计；先看测量日期和版本。
- [详细路线图](roadmap.md)：里程碑、当前重点及待完成工作。
- [Photoshop 对齐评估](target-app-parity.md)：评估方法、分项证据与估计。
- [差距清单](gaps.md)：按优先级排列的问题。
- [文件兼容性](file-format-parity.md)、[工具与画笔](brush-parity.md)、[界面](ui-parity.md)、[硬件](hardware-parity.md)：各领域的行为边界。
- [计分卡](scorecard.md)：由 `cargo xtask scorecard` 生成。测试下限、历史性能基线和人工清单各有不同含义；它们不等于本次运行结果。
- [菜单命令覆盖](parity-checklist.md)：由 `cargo xtask parity` 生成，仅衡量菜单接线。

生成文件应修改其源数据再重新生成。架构文档中的原始设计方案、路线图中的历史检查点和带日期的性能报告用于保留决策与测量背景；判断当前行为时还需核对源码和相应测试。

共享 `craftrules` 是私有的相邻仓库，独立克隆 PhotoCraft 不会自动获得它。公开发布步骤见[发布指南](releasing.md)，需要额外共享规则时请联系维护者。
