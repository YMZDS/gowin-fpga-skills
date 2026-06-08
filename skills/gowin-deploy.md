---
name: gowin-deploy
description: Gowin FPGA 一键编译+烧录。先编译再下载，自动衔接。
runAs: subagent
allowed-tools: run_command, run_background, wait_for_job, job_output, run_skill
---
## Gowin FPGA Build + Program (一键编译烧录)

自动完成 Gowin FPGA 工程的编译和烧录。

### 步骤

1. 调用 `gowin-build` skill 编译工程
2. 编译成功后，调用 `gowin-program` skill 下载比特流

### 示例

```
run_skill gowin-build "path/to/project.gprj"
# 等待编译完成...
run_skill gowin-program "path/to/project.fs"
```

### 快速命令 (单文件工程)

```
%GOWIN_HOME%\IDE\bin\gw_sh.exe build.tcl && %GOWIN_HOME%\Programmer\bin\programmer_cli.exe --device <DEVICE> --operation_index 2 --fsFile <path>.fs
```

### 注意事项

- 编译失败不会执行烧录步骤
- 确保 USB 下载线已连接