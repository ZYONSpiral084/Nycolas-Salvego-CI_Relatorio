# 🔬 Robocode CI Report — Nycolas-Salvego  / # 🔬 Relatório CI Robocode — Nycolas-Salvego


| 🇺🇸 English (left) | 🇧🇷 Português (right) |
|---|---|
| **Project**: Robocode CI pipeline, static analysis and automated battle reports. This repo bundles Robocode robots, a battle scenario, CI workflow (Checkstyle + SpotBugs), helper scripts and the libraries required to run local battles. | **Projeto**: Pipeline CI para Robocode, análise estática e geração automática de relatórios de batalha. Este repositório contém robôs Robocode, cenário de batalha, workflow CI (Checkstyle + SpotBugs), scripts utilitários e as bibliotecas necessárias para executar batalhas localmente. |

---

## 📌 Quick status / Estado rápido

| 🇺🇸 What it does | 🇧🇷 O que faz |
|---|---|
| - Runs code quality checks (Checkstyle) and static analysis (SpotBugs) in GitHub Actions.<br>- Executes automated Robocode battles and generates logs + an HTML report.<br>- Uploads `battle_logs/` as workflow artifacts for inspection. | - Executa verificações de qualidade (Checkstyle) e análise estática (SpotBugs) no GitHub Actions.<br>- Roda batalhas Robocode automatizadas e gera logs + relatório HTML.<br>- Faz upload de `battle_logs/` como artefato do workflow para inspeção. |

---

## 📁 Repo snapshot / Estrutura do repositório

| 🇺🇸 Files & folders of interest | 🇧🇷 Arquivos e pastas de interesse |
|---|---|
| - `.github/workflows/ci.yml` — CI workflow (push / pull_request on `main`).<br>- `scripts/testar_batalha.sh` — script that builds the battle file, runs Robocode, and generates an HTML report.<br>- `robocode/robots/github/` — Java source for robots: `Astroboys.java`, `Corners.java`.<br>- `libs/` — bundled Robocode jars and dependencies.<br>- `battles/` — preconfigured `.battle` files (example: `battle.battle`).<br>- `.history/` — previous workflow/script versions (for reference). | - `.github/workflows/ci.yml` — workflow CI (push / pull_request na `main`).<br>- `scripts/testar_batalha.sh` — script que monta o arquivo de batalha, executa o Robocode e gera relatório HTML.<br>- `robocode/robots/github/` — código-fonte Java dos robôs: `Astroboys.java`, `Corners.java`.<br>- `libs/` — jars do Robocode e dependências incluídas.<br>- `battles/` — arquivos `.battle` pré-configurados (ex.: `battle.battle`).<br>- `.history/` — versões anteriores de workflows/scripts (referência). |

---

## 🛠️ How to run locally (quick) / Como rodar localmente (rápido)

| 🇺🇸 Quick steps | 🇧🇷 Passos rápidos |
|---|---|
| 1. Ensure you have Java installed (JDK 11+ recommended).<br>2. Make the script executable: `chmod +x scripts/testar_batalha.sh`.<br>3. Run: `bash scripts/testar_batalha.sh` — this creates `battle_logs/` and a simple HTML report.<br>4. Inspect `battle_logs/` or download the artifact from the workflow run on GitHub. | 1. Certifique-se de ter Java instalado (JDK 11+ recomendado).<br>2. Dê permissão ao script: `chmod +x scripts/testar_batalha.sh`.<br>3. Execute: `bash scripts/testar_batalha.sh` — isso gera `battle_logs/` e um relatório HTML simples.<br>4. Consulte a pasta `battle_logs/` ou baixe o artefato do run no GitHub Actions. |

> Note: the project includes `libs/` with Robocode jars to help local execution; however, depending on your OS and setup you might prefer installing Robocode separately.  
> Observação: o projeto inclui `libs/` com os jars do Robocode para facilitar a execução local; dependendo do seu SO/ambiente, pode preferir instalar o Robocode separadamente.

---

## 🧩 CI / GitHub Actions (what it does)  
| 🇺🇸 English | 🇧🇷 Português |
|---|---|
| - Workflow: `.github/workflows/ci.yml` (runs on push / PR against `main`).<br>- Tasks (high level): checkout, Java setup, run Checkstyle, run SpotBugs, compile robots, run automated battle via script, collect logs and upload `battle_logs/` as artifact.<br>- Artifacts: `battle_logs/` (report.html + raw logs) — useful for grading or postmortem. | - Workflow: `.github/workflows/ci.yml` (dispara em push / PR para a branch `main`).<br>- Tarefas (visão geral): checkout, configurar Java, rodar Checkstyle, SpotBugs, compilar robôs, executar a batalha automatizada via script, coletar logs e enviar `battle_logs/` como artefato.<br>- Artefatos: `battle_logs/` (report.html + logs) — útil para avaliação ou análise posterior. |

---

## 🧾 What the battle script does / O que o script de batalha faz

| 🇺🇸 Script highlights | 🇧🇷 Destaques do script |
|---|---|
| - Creates a `.battle` configuration into `battle_logs/`.<br>- Invokes Robocode engine (using bundled jars or your local Robocode installation).<br>- Captures battle results into `battle_logs/` and generates a small HTML summary (`report.html`). | - Gera um arquivo `.battle` dentro de `battle_logs/`.<br>- Invoca a engine do Robocode (usando os jars incluídos ou instalação local).<br>- Captura os resultados em `battle_logs/` e cria um resumo em HTML (`report.html`). |

---

## ✅ How to inspect results / Como inspecionar resultados

| 🇺🇸 Inspect locally | 🇧🇷 Inspecionar localmente |
|---|---|
| - Open `battle_logs/report.html` in your browser.<br>- Review `battle_logs/sample_result.txt` and raw logs for per-round scores. | - Abra `battle_logs/report.html` no navegador.<br>- Confira `battle_logs/sample_result.txt` e os logs brutos para ver pontuações por rodada. |

---

## 🧰 Notes about Checkstyle & SpotBugs / Observações sobre Checkstyle & SpotBugs

| 🇺🇸 Notes | 🇧🇷 Observações |
|---|---|
| - The CI integrates Checkstyle (Google ruleset) and SpotBugs to catch style and potential bugs.<br>- Use these tools locally for quick feedback: `mvn checkstyle:check` / `mvn com.github.spotbugs:spotbugs-maven-plugin:check` (if you prefer Maven). | - O CI integra Checkstyle (padrão Google) e SpotBugs para achar problemas de estilo e bugs potenciais.<br>- Rode localmente para feedback rápido: `mvn checkstyle:check` / `mvn com.github.spotbugs:spotbugs-maven-plugin:check` (se usar Maven). |

---

## 🧾 Files of interest (short) / Arquivos importantes (resumo)

| 🇺🇸 English | 🇧🇷 Português |
|---|---|
| - `.github/workflows/ci.yml` — CI pipeline.<br>- `scripts/testar_batalha.sh` — battle + report generator.<br>- `robocode/robots/github/Astroboys.java` — robot source.<br>- `robocode/robots/github/Corners.java` — robot source.<br>- `libs/` — bundled jars. | - `.github/workflows/ci.yml` — pipeline CI.<br>- `scripts/testar_batalha.sh` — gerador de batalha e relatório.<br>- `robocode/robots/github/Astroboys.java` — código do robô.<br>- `robocode/robots/github/Corners.java` — código do robô.<br>- `libs/` — jars incluídos. |

---

## 👨‍🏫 Credits & context / Créditos & contexto

| 🇺🇸 English | 🇧🇷 Português |
|---|---|
| - Author / Maintainer: **Nycolas Antony Salvego** (ZYONSpiral084).<br>- Academic context: FATEC Ourinhos assignments and experiments. | - Autor / Mantenedor: **Nycolas Antony Salvego** (ZYONSpiral084).<br>- Contexto acadêmico: atividades e experimentos da FATEC Ourinhos. |

---

## 📜 License / Licença

| 🇺🇸 English | 🇧🇷 Português |
|---|---|
| Academic / educational use. Please cite the author when reusing. | Uso acadêmico / educacional. Por favor cite o autor ao reutilizar. |

---

