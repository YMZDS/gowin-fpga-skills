---
name: gowin-program
description: 下载 Gowin FPGA 比特流到开发板 — 扫描设备、SRAM 编程。参数：.fs 文件路径。
runAs: subagent
allowed-tools: run_command, run_background, wait_for_job, job_output
---
## Gowin FPGA Program Skill

将 `.fs` 比特流下载到 Gowin FPGA 开发板。

### 环境

- 编程器: `%GOWIN_HOME%\Programmer\bin\programmer_cli.exe`
- 下载线: Gowin USB Cable (FT2CH)
- SRAM 编程模式: `--operation_index 2`

### 步骤

1. 确认 `.fs` 比特流文件路径
2. 扫描已连接的FPGA设备，确认设备型号
3. 确认 `%GOWIN_HOME%` 环境变量
4. 运行:
```
%GOWIN_HOME%\Programmer\bin\programmer_cli.exe --device <DEVICE> --operation_index 2 --fsFile <path_to_fs>
```
5. 等待下载完成（约 5-10 秒）
6. 检查输出: `User Code: 0x...` 和 `Status Code: 0x...` 表示成功

### 其他操作

- `--scan`: 扫描已连接的 FPGA 设备
- `--operation_index 0`: 读取设备 ID

### 设备支持

| 开发板 | 设备型号 | 参数 |
|--------|---------|------|
| Tang Nano 4K | GW1NSR-4C | `--device GW1NSR-4C` |
| Tang Nano 9K | GW1NR-9C | `--device GW1NR-9C` |

### 注意事项

- 确保开发板通过 USB 连接到电脑
- 如果找不到设备，检查 USB 驱动是否正确安装
- 下载前应先完成编译（gowin-build）
