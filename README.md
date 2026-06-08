# Gowin FPGA Reasonix Skills 🛠️

Reasonix AI 助手 Skills，用于 Gowin FPGA 开发全流程。

支持 Tang Nano 系列开发板（4K/9K）的**编译 → 烧录 → 一键部署**。

---

## Skills 概述

| Skill | 功能 | 说明 |
|-------|------|------|
| `gowin-build` | 编译 FPGA 工程 | 综合 + 布局布线，生成 `.fs` 比特流 |
| `gowin-program` | 下载比特流 | 通过 USB 将 `.fs` 烧录到开发板 |
| `gowin-deploy` | 一键编译+烧录 | 先编译，成功后自动下载 |

---

## 使用方法

在 Reasonix AI 助手中调用：

```
run_skill gowin-build "path/to/project.gprj"
run_skill gowin-program "path/to/project.fs"
run_skill gowin-deploy "path/to/project.gprj"
```

---

## 环境要求

### Gowin EDA

| 组件 | 路径 |
|------|------|
| IDE | `%GOWIN_HOME%\IDE\bin\gw_sh.exe` |
| Programmer | `%GOWIN_HOME%\Programmer\bin\programmer_cli.exe` |

设置环境变量 `GOWIN_HOME` 指向 Gowin EDA 安装目录（如 `C:\Gowin\Gowin_V1.9.11.03_Education_x64`）。

### 支持的开发板

| 开发板 | 设备型号 | programmer_cli 参数 |
|--------|---------|---------------------|
| Tang Nano 4K | GW1NSR-4C | `--device GW1NSR-4C` |
| Tang Nano 9K | GW1NR-9C | `--device GW1NR-9C` |

---

## Skill 文件

- [`skills/gowin-build.md`](skills/gowin-build.md) — 编译 skill
- [`skills/gowin-program.md`](skills/gowin-program.md) — 烧录 skill
- [`skills/gowin-deploy.md`](skills/gowin-deploy.md) — 一键部署 skill

---

## 许可

MIT