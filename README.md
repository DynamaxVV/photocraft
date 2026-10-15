# PhotoCraft

原生 Rust 图像编辑器，目标是逐步对齐 Photoshop 的编辑行为、快捷键与文件兼容性，并让编辑能力可由脚本和 AI 代理调用。

[旧版 README（英文）](README.en.md) · [更新日志](CHANGELOG.md) · [本 fork 更改说明](FORK_CHANGES.md) · [文档导航](docs/README.md)

![PhotoCraft 编辑界面](docs/images/photocraft-demo.jpg)

## 关于这个仓库

这是 [DynamaxVV/photocraft](https://github.com/DynamaxVV/photocraft)，基于 [storytold/photocraft](https://github.com/storytold/photocraft) 的个人 fork。PhotoCraft 的原始开发与版权归属保留，当前 fork 的修改记录见 [FORK_CHANGES.md](FORK_CHANGES.md)。

本分支已提交的更改主要是中文入口、文档整理和有效性修正。本地尚未提交的功能开发不属于当前 GitHub 分支；功能状态以本分支源码与测试为准。

## 可以做什么

- 使用图层、蒙版、选区、调整图层、混合模式与图层样式完成编辑。
- 使用笔刷、修复、文字、形状和路径等工具处理图像。
- 读写 PSD/PSB 与原生 `.pcraft` 文档，并导入、导出多种平面图像格式。
- 通过 CLI 批处理、MCP 服务和桌面 JSON 控制通道执行命令。
- 在 macOS、Windows、Linux 等桌面环境运行；同一套 Rust 引擎与界面也可编译为 WebAssembly。

桌面使用 **egui/eframe + wgpu**，采用原生窗口。像素位深和色彩模型是运行时数据，色彩转换通过 ICC 色彩管理模块处理。

项目仍处于 **alpha** 阶段。菜单入口、文件往返测试和 Photoshop 中的实际编辑效果是不同的验收维度；复杂 PSD、文字排版、专业工作流和性能仍有缺口。具体见[路线图](docs/roadmap.md)、[对齐评估](docs/target-app-parity.md)与[计分卡](docs/scorecard.md)。

## 从源码运行

需要 Rust stable 1.95 或更高版本。Linux 的系统依赖见[开发指南](docs/development.md#prerequisites)。以下命令从仓库根目录执行：

```sh
git clone https://github.com/DynamaxVV/photocraft.git
cd photocraft
cargo run --release -p photocraft -- image.psd
```

不传入图片路径可直接启动应用：

```sh
cargo run --release -p photocraft
```

字体可以使用系统字体；共享字体库 `craft-fonts` 是可选构建输入，配置方法见[开发指南](docs/development.md#fonts-craft-fonts)。本机 E 盘缓存约定与清理方法见[文档维护](docs/documentation-maintenance.md#本机构建缓存)。

如需预编译安装包，可查看[上游 Releases](https://github.com/storytold/photocraft/releases)。本 fork 当前未发布独立安装包，上游安装包不包含本 fork 的修改。

## 自动化与代理

界面、CLI、MCP 与桌面控制通道共用引擎命令。先查询参数，再执行操作：

```sh
cargo run -p photocraft-cli -- --help
cargo run -p photocraft-cli -- commands
cargo run -p photocraft-cli -- mcp --automation-read-root ./work --automation-write-root ./work
```

MCP 文件读写范围由启动参数指定。桌面桥接、鉴权与截图方法见[控制协议](docs/control-protocol.md)，工具与安装说明见 [MCP 文档](docs/mcp.md)。

## 开发与验证

开始修改前先读 [AGENTS.md](AGENTS.md) 和[贡献指南](docs/contributing.md)。常用检查：

```sh
cargo test --workspace
cargo xtask layers
cargo xtask wasm
```

完整验证要求取决于修改范围。图像与文件格式代码还需真实文件语料、像素或多位深测试；界面改动需截图检查。语料获取、构建环境和各类验证入口见[开发指南](docs/development.md)。

## 文档与变更

| 入口 | 内容 |
|---|---|
| [更新日志](CHANGELOG.md) | 本 fork 按时间记录的已提交变更 |
| [本 fork 更改说明](FORK_CHANGES.md) | 上游基点、修改范围、验证结果与尚未发布的本地工作 |
| [文档导航](docs/README.md) | 按使用、开发、自动化和发布任务寻找文档 |
| [文档手册](book/src/SUMMARY.md) | 按章节阅读架构、格式和安全说明 |
| [旧版 README（英文）](README.en.md) | 保留原说明、截图展示及上游生态介绍；历史数字以对应日期为准 |

## 许可证与致谢

代码采用 [MIT](LICENSE-MIT) 或 [Apache-2.0](LICENSE-APACHE) 双许可证，原始版权与声明见 [NOTICE](NOTICE)。第三方素材与原始素材的来源、许可证见 [ATTRIBUTION.md](ATTRIBUTION.md)。截图所用艺术作品来源见 [SOURCES.md](docs/images/SOURCES.md)。

ArtCraft 品牌标识有[独立许可](docs/brand/LICENSE-brand.txt)。PhotoCraft 是独立开源项目，与 Adobe 无隶属或背书关系；文中的 Photoshop 名称用于描述兼容目标。
