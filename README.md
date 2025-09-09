# 🔬 Robocode CI Report — Nycolas-Salvego
**2025-09-09**

**Languages:** [English](README.md) • [Português (pt-BR)](README.pt-BR.md) • [中文（简体）](README.zh-CN.md)

---

## 📌 Project Summary / Resumo do Projeto / 项目概述

| 🇺🇸 English | 🇧🇷 Português | 🇨🇳 中文（简体） |
|---|---|---|
| **Project**: Robocode CI pipeline, static analysis and automated battle reports. This repo bundles Robocode robots, a battle scenario, CI workflow (Checkstyle + SpotBugs), helper scripts and the libraries required to run local battles. | **Projeto**: Pipeline CI para Robocode, análise estática e geração automática de relatórios de batalha. Este repositório contém robôs Robocode, cenário de batalha, workflow CI (Checkstyle + SpotBugs), scripts utilitários e as bibliotecas necessárias para executar batalhas localmente. | **项目**：Robocode CI 管线、静态分析与自动化战斗报告。本仓库汇集了 Robocode 机器人、战斗场景、CI 工作流（Checkstyle + SpotBugs）、辅助脚本以及用于本地运行战斗的依赖库。 |

---

## 📌 Quick status / Estado rápido / 快速状态

| 🇺🇸 English | 🇧🇷 Português | 🇨🇳 中文（简体） |
|---|---|---|
| - Runs code quality checks (Checkstyle) and static analysis (SpotBugs) in GitHub Actions.<br>- Executes automated Robocode battles and generates logs + an HTML report.<br>- Uploads `battle_logs/` as workflow artifacts for inspection. | - Executa verificações de qualidade (Checkstyle) e análise estática (SpotBugs) no GitHub Actions.<br>- Roda batalhas Robocode automatizadas e gera logs + relatório HTML.<br>- Faz upload de `battle_logs/` como artefato do workflow para inspeção. | - 在 GitHub Actions 中运行代码质量检查（Checkstyle）和静态分析（SpotBugs）。<br>- 执行自动化 Robocode 战斗并生成日志与 HTML 报告。<br>- 将 `battle_logs/` 上传为工作流产物以便查看。 |

---

## 📁 Repo snapshot / Estrutura do repositório / 仓库结构

| 🇺🇸 English | 🇧🇷 Português | 🇨🇳 中文（简体） |
|---|---|---|
| - `.github/workflows/ci.yml` — CI workflow (push / pull_request on `main`).<br>- `scripts/testar_batalha.sh` — script that builds the battle file, runs Robocode, and generates an HTML report.<br>- `robocode/robots/github/` — Java source for robots: `Astroboys.java`, `Corners.java`.<br>- `libs/` — bundled Robocode jars and dependencies.<br>- `battles/` — preconfigured `.battle` files (example: `battle.battle`).<br>- `.history/` — previous workflow/script versions (for reference). | - `.github/workflows/ci.yml` — workflow CI (push / pull_request na `main`).<br>- `scripts/testar_batalha.sh` — script que monta o arquivo de batalha, executa o Robocode e gera relatório HTML.<br>- `robocode/robots/github/` — código-fonte Java dos robôs: `Astroboys.java`, `Corners.java`.<br>- `libs/` — jars do Robocode e dependências incluídas.<br>- `battles/` — arquivos `.battle` pré-configurados (ex.: `battle.battle`).<br>- `.history/` — versões anteriores de workflows/scripts (referência). | - `.github/workflows/ci.yml` — CI 工作流（在 `main` 分支上触发 push / pull_request）。<br>- `scripts/testar_batalha.sh` — 构建 .battle 文件、运行 Robocode 并生成 HTML 报告的脚本。<br>- `robocode/robots/github/` — 机器人 Java 源码：`Astroboys.java`, `Corners.java`。<br>- `libs/` — 打包的 Robocode jars 与依赖。<br>- `battles/` — 预配置的 `.battle` 文件（例如 `battle.battle`）。<br>- `.history/` — 以前的 workflow/脚本版本（供参考）。 |

---

## 🛠️ How to run locally (quick) / Como rodar localmente (rápido) / 本地快速运行

| 🇺🇸 English | 🇧🇷 Português | 🇨🇳 中文（简体） |
|---|---|---|
| 1. Ensure you have Java installed (JDK 11+ recommended).<br>2. Make the script executable: `chmod +x scripts/testar_batalha.sh`.<br>3. Run: `bash scripts/testar_batalha.sh` — this creates `battle_logs/` and a simple HTML report.<br>4. Inspect `battle_logs/` or download the artifact from the workflow run on GitHub. | 1. Certifique-se de ter Java instalado (JDK 11+ recomendado).<br>2. Dê permissão ao script: `chmod +x scripts/testar_batalha.sh`.<br>3. Execute: `bash scripts/testar_batalha.sh` — isso gera `battle_logs/` e um relatório HTML simples.<br>4. Consulte a pasta `battle_logs/` ou baixe o artefato do run no GitHub Actions. | 1. 确保已安装 Java（建议 JDK 11+）。<br>2. 赋予脚本执行权限：`chmod +x scripts/testar_batalha.sh`。<br>3. 运行：`bash scripts/testar_batalha.sh` — 该操作会生成 `battle_logs/` 和一个简单的 HTML 报告。<br>4. 查看 `battle_logs/` 或从 GitHub Actions 的运行中下载产物。 |

---

> Note / Observação / 注：The project includes `libs/` with Robocode jars to help local execution; depending on your OS and setup you might prefer installing Robocode separately.  
> Nota / Observação / 备注：O projeto inclui `libs/` com os jars do Robocode para facilitar a execução local; dependendo do seu SO/ambiente, pode preferir instalar o Robocode separadamente.  
> 说明：项目包含 `libs/`（Robocode jars），以便本地运行；但视系统环境，您也可以选择单独安装 Robocode。

---

## 🧩 CI / GitHub Actions (what it does) / CI / GitHub Actions（功能）

| 🇺🇸 English | 🇧🇷 Português | 🇨🇳 中文（简体） |
|---|---|---|
| - Workflow: `.github/workflows/ci.yml` (runs on push / PR against `main`).<br>- Tasks (high level): checkout, Java setup, run Checkstyle, run SpotBugs, compile robots, run automated battle via script, collect logs and upload `battle_logs/` as artifact.<br>- Artifacts: `battle_logs/` (report.html + raw logs) — useful for grading or postmortem. | - Workflow: `.github/workflows/ci.yml` (dispara em push / PR para a branch `main`).<br>- Tarefas (visão geral): checkout, configurar Java, rodar Checkstyle, SpotBugs, compilar robôs, executar a batalha automatizada via script, coletar logs e enviar `battle_logs/` como artefato.<br>- Artefatos: `battle_logs/` (report.html + logs) — útil para avaliação ou análise posterior. | - 工作流：`.github/workflows/ci.yml`（在对 `main` 的 push/PR 时运行）。<br>- 任务（高层）：checkout、配置 Java、运行 Checkstyle、运行 SpotBugs、编译机器人、通过脚本运行自动化战斗、收集日志并上传 `battle_logs/` 作为产物。<br>- 产物：`battle_logs/`（包含 report.html 与原始日志）— 适用于评分或事后分析。 |

---

## 🧾 What the battle script does / O que o script de batalha faz / 脚本功能

| 🇺🇸 English | 🇧🇷 Português | 🇨🇳 中文（简体） |
|---|---|---|
| - Creates a `.battle` configuration into `battle_logs/`.<br>- Invokes Robocode engine (using bundled jars or your local Robocode installation).<br>- Captures battle results into `battle_logs/` and generates a small HTML summary (`report.html`). | - Gera um arquivo `.battle` dentro de `battle_logs/`.<br>- Invoca a engine do Robocode (usando os jars incluídos ou instalação local).<br>- Captura os resultados em `battle_logs/` e cria um resumo em HTML (`report.html`). | - 在 `battle_logs/` 中生成 `.battle` 配置文件。<br>- 调用 Robocode 引擎（使用打包的 jars 或本地 Robocode 安装）。<br>- 将战斗结果保存到 `battle_logs/` 并生成一个 HTML 汇总（`report.html`）。 |

---

## ✅ How to inspect results / Como inspecionar resultados / 如何查看结果

| 🇺🇸 English | 🇧🇷 Português | 🇨🇳 中文（简体） |
|---|---|---|
| - Open `battle_logs/report.html` in your browser.<br>- Review `battle_logs/sample_result.txt` and raw logs for per-round scores. | - Abra `battle_logs/report.html` no navegador.<br>- Confira `battle_logs/sample_result.txt` e os logs brutos para ver pontuações por rodada. | - 在浏览器中打开 `battle_logs/report.html`。<br>- 查阅 `battle_logs/sample_result.txt` 与原始日志以查看逐轮得分。 |

---

## 🧰 Notes about Checkstyle & SpotBugs / Observações sobre Checkstyle & SpotBugs / 关于 Checkstyle 与 SpotBugs 的说明

| 🇺🇸 English | 🇧🇷 Português | 🇨🇳 中文（简体） |
|---|---|---|
| - The CI integrates Checkstyle (Google ruleset) and SpotBugs to catch style and potential bugs.<br>- Use these tools locally for quick feedback: `mvn checkstyle:check` / `mvn com.github.spotbugs:spotbugs-maven-plugin:check` (if you prefer Maven). | - O CI integra Checkstyle (padrão Google) e SpotBugs para achar problemas de estilo e bugs potenciais.<br>- Rode localmente para feedback rápido: `mvn checkstyle:check` / `mvn com.github.spotbugs:spotbugs-maven-plugin:check` (se usar Maven). | - CI 集成了 Checkstyle（Google 规则）与 SpotBugs 以发现风格问题与潜在缺陷。<br>- 在本地使用这些工具以获取快速反馈：`mvn checkstyle:check` / `mvn com.github.spotbugs:spotbugs-maven-plugin:check`（若使用 Maven）。 |

---

## 🧾 Files of interest (short) / Arquivos importantes (resumo) / 重要文件（摘要）

| 🇺🇸 English | 🇧🇷 Português | 🇨🇳 中文（简体） |
|---|---|---|
| - `.github/workflows/ci.yml` — CI pipeline.<br>- `scripts/testar_batalha.sh` — battle + report generator.<br>- `robocode/robots/github/Astroboys.java` — robot source.<br>- `robocode/robots/github/Corners.java` — robot source.<br>- `libs/` — bundled jars. | - `.github/workflows/ci.yml` — pipeline CI.<br>- `scripts/testar_batalha.sh` — gerador de batalha e relatório.<br>- `robocode/robots/github/Astroboys.java` — código do robô.<br>- `robocode/robots/github/Corners.java` — código do robô.<br>- `libs/` — jars incluídos. | - `.github/workflows/ci.yml` — CI 管线。<br>- `scripts/testar_batalha.sh` — 战斗与报告生成脚本。<br>- `robocode/robots/github/Astroboys.java` — 机器人源码。<br>- `robocode/robots/github/Corners.java` — 机器人源码。<br>- `libs/` — 打包的 jars。 |

---

## 👨‍🏫 Credits & context / Créditos & contexto / 致谢与背景

| 🇺🇸 English | 🇧🇷 Português | 🇨🇳 中文（简体） |
|---|---|---|
| - Author / Maintainer: **Nycolas Antony Salvego** (ZYONSpiral084).<br>- Academic context: FATEC Ourinhos assignments and experiments. | - Autor / Mantenedor: **Nycolas Antony Salvego** (ZYONSpiral084).<br>- Contexto acadêmico: atividades e experimentos da FATEC Ourinhos. | - 作者 / 维护者：**Nycolas Antony Salvego**（ZYONSpiral084）。<br>- 学术背景：FATEC Ourinhos 的作业与实验。 |

---

## 📜 License / Licença / 许可证

| 🇺🇸 English | 🇧🇷 Português | 🇨🇳 中文（简体） |
|---|---|---|
| Academic / educational use. Please cite the author when reusing. | Uso acadêmico / educacional. Por favor cite o autor ao reutilizar. | 学术 / 教育用途。重复使用时请注明作者。 |

---

## 🔁 Recommended workflow for updates / Fluxo recomendado para atualizações / 推荐更新工作流

```bash
git checkout -b ci-report/readme-update
# edit README.md, README.pt-BR.md, README.zh-CN.md as needed
git add README*.md
git commit -m "Update CI report READMEs (EN/PT/ZH)"
git push origin ci-report/readme-update
# open PR and request native review for README.zh-CN.md
```

---

## 📝 Notes about translations / Observações sobre traduções / 翻译说明

| 🇺🇸 English | 🇧🇷 Português | 🇨🇳 中文（简体） |
|---|---|---|
| Machine translation is acceptable for drafts — however, require a native review before marking zh-CN as official. Keep code blocks and commands in English across translations. | Tradução automática serve como rascunho — exija revisão nativa antes de marcar o zh-CN como oficial. Mantenha trechos de código e comandos em inglês. | 机器翻译可作为草稿，但在将 zh-CN 标为正式版本之前需要母语审校。所有翻译中的代码块与命令请保持英文。 |
