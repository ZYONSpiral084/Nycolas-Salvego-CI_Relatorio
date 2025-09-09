# 🔬 Robocode CI 报告 — Nycolas-Salvego
**2025-09-09**

**语言：** [English](README.md) • [Português (pt-BR)](README.pt-BR.md) • [中文（简体）](README.zh-CN.md)

---

## 📌 项目概述

**项目**：Robocode CI 管线、静态分析与自动化战斗报告。本仓库包含 Robocode 机器人、战斗场景、CI 工作流（Checkstyle + SpotBugs）、辅助脚本以及本地运行战斗所需的库。

---

## 📌 快速状态

- 在 GitHub Actions 中运行 Checkstyle 与 SpotBugs。  
- 执行自动化战斗，生成日志与 HTML 报告。  
- 将 `battle_logs/` 作为产物上传以供检查。

---

## 📁 仓库结构

- `.github/workflows/ci.yml` — CI 工作流（在 `main` 上触发）。  
- `scripts/testar_batalha.sh` — 生成 .battle、运行 Robocode 并生成 HTML 报告的脚本。  
- `robocode/robots/github/` — 机器人源码：`Astroboys.java`, `Corners.java`。  
- `libs/` — 打包的 Robocode jars 与依赖。  
- `battles/` — 预配置的 `.battle` 文件。  
- `.history/` — 历史脚本/工作流版本。

---

## 🛠️ 本地快速运行

1. 安装 Java（建议 JDK 11+）。  
2. 赋予脚本执行权限：`chmod +x scripts/testar_batalha.sh`。  
3. 运行：`bash scripts/testar_batalha.sh` — 生成 `battle_logs/` 与 `report.html`。  
4. 查看本地日志或从 GitHub Actions 下载产物。

---

## 🧩 CI / GitHub Actions（功能）

- 工作流：`.github/workflows/ci.yml`（对 `main` 的 push/PR 触发）。  
- 任务：checkout、配置 Java、运行 Checkstyle、运行 SpotBugs、编译机器人、通过脚本运行自动化战斗、收集日志并上传 `battle_logs/`。  
- 产物：`battle_logs/`（包含 report.html 与原始日志）。

---

## 🧾 脚本功能概述

- 在 `battle_logs/` 中生成 `.battle` 配置。  
- 调用 Robocode 引擎（使用打包 jars 或本地安装）。  
- 捕获结果并生成 `report.html`。

---

## ✅ 查看结果

- 在浏览器打开 `battle_logs/report.html`。  
- 查阅 `battle_logs/sample_result.txt` 与原始日志以查看逐轮详情。

---

## 🧰 Checkstyle 与 SpotBugs

CI 集成了 Checkstyle（Google 规则）与 SpotBugs。可在本地运行以获得快速反馈：`mvn checkstyle:check` / `mvn com.github.spotbugs:spotbugs-maven-plugin:check`（若使用 Maven）。

---

## 👨‍🏫 致谢与背景

- 作者：**Nycolas Antony Salvego**（ZYONSpiral084）。  
- 背景：FATEC Ourinhos 的学术作业与实验。

---

## 📜 许可证

学术 / 教育用途。重复使用请注明作者。
