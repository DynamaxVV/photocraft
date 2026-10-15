# PhotoCraft 文档维护

## 检查有效性

先读[文档导航](README.md)，确定修改的是当前参考文档、历史评估还是生成报告。核对构建参数、命令 ID、版本和文件路径时使用同一提交的源码；保留历史报告的日期、测试环境和验收范围。更新回归测试下限不代表重新完成真实文件或 Photoshop 验收。

检查仓库内 Markdown 链接、图片路径和章节锚点。相邻的私有仓库不属于 PhotoCraft 的公开文档树，应以代码路径说明其位置，并提供可公开阅读的替代入口。外部网页的可访问性需要另行联网检查；本地链接通过不证明外部链接有效。

使用与 `.github/workflows/docs.yml` 相同的 mdBook 版本，从仓库根目录构建：

```sh
mdbook --version                 # CI 使用 0.4.52
mdbook build book --dest-dir /absolute/cache/path/photocraft/book-output
git diff --check
```

`--dest-dir` 应指向项目专用缓存中的目录。mdBook 构建验证章节组织和渲染，不会执行文档中的命令，也不会自动证明所有链接、功能或截图仍正确。涉及应用行为时仍按 [AGENTS.md](../AGENTS.md) 运行对应验证。

[计分卡](scorecard.md)和[菜单覆盖](parity-checklist.md)由 xtask 生成，应改源数据再生成。文档整理不应为了更新日期而重写性能数据、提高测试下限或改变完成状态。

## 本机构建缓存

此 macOS 工作环境的 PhotoCraft 缓存位于 `/Volumes/E/cache/photocraft/`。构建前，在配有本地环境脚本的工作区执行 `. scripts/local-build-env.sh`；该脚本是本机配置，独立克隆的仓库未必包含它。脚本缺失时先恢复本机缓存配置，不能静默改用内置盘。其他机器按自身环境设置 `CARGO_TARGET_DIR` 和临时目录。

清理前确认没有 Cargo、rustc、Trunk、打包或验收进程正在使用对应目录。按明确路径清理过期的 `incremental`、一次性临时文件和已结束任务的构建目录；保留依赖下载缓存、仍需使用的编译对象、验收证据和最终发布包。不要用无差别 `cargo clean` 代替范围检查。

`/Volumes/E/cache` 是多个应用共享的 APFS 缓存卷。只处理 `photocraft/` 子目录；不要在其他应用使用该卷时卸载或压缩稀疏容器。删除文件释放卷内空间与压缩稀疏容器回收 E 盘空间是两个操作。

## 提交范围

先查看 `git status` 和远端分支。存在其他任务的未提交改动时，单独暂存本次文件；本地显著落后远端时，可在缓存目录建立基于远端的新 worktree。推送到自己的 fork，并核对远端提交 ID，避免把其他任务或过期源码一起发布。
