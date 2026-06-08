---
name: gowin-build
description: 编译 Gowin FPGA 工程 — 运行综合+布局布线，生成 .fs 比特流文件。参数：工程 .gprj 文件路径。
runAs: subagent
allowed-tools: run_command, run_background, wait_for_job, job_output, read_file, write_file
---
## Gowin FPGA Build Skill

综合 + 布局布线 Gowin FPGA 工程，生成比特流。

### 环境

- Gowin EDA: `%GOWIN_HOME%\IDE\bin\gw_sh.exe`
- 编译脚本 `build.tcl` 模板:
```
open_project <project_path>
run syn
run pnr
```

### 步骤

1. 确认工程 `.gprj` 文件路径
2. 确认环境变量 `%GOWIN_HOME%` 已设置
3. 创建或确认 `build.tcl` 存在
4. 运行: `%GOWIN_HOME%\IDE\bin\gw_sh.exe build.tcl`
5. 等待完成（综合~2分钟，P&R~3分钟）
6. 编译成功后比特流位于: `<project_dir>\impl\pnr\<project_name>.fs`

### 注意事项

- gw_sh.exe 必须在工程目录或其父目录运行，或 build.tcl 使用绝对路径
- 编译时间取决于设计规模，通常 3-8 分钟
- 检查输出中的 ERROR 和 WARN 信息

### 设备支持

| 开发板 | 设备型号 |
|--------|---------|
| Tang Nano 4K | GW1NSR-4C |
| Tang Nano 9K | GW1NR-9C |