# 🔬 Relatório CI Robocode — Nycolas-Salvego
**2025-09-09**

**Idiomas:** [English](README.md) • [Português (pt-BR)](README.pt-BR.md) • [中文（简体）](README.zh-CN.md)

---

## 📌 Resumo do Projeto

**Projeto**: Pipeline CI para Robocode, análise estática e geração automática de relatórios de batalha. Este repositório contém robôs Robocode, cenário de batalha, workflow CI (Checkstyle + SpotBugs), scripts utilitários e as bibliotecas necessárias para executar batalhas localmente.

---

## 📌 Estado rápido

- Executa Checkstyle e SpotBugs no GitHub Actions.  
- Roda batalhas automatizadas e gera logs + relatório HTML.  
- Envia `battle_logs/` como artefato do workflow.

---

## 📁 Estrutura do repositório

- `.github/workflows/ci.yml` — workflow CI (push / pull_request na `main`).  
- `scripts/testar_batalha.sh` — script que monta o arquivo `.battle`, executa o Robocode e gera relatório HTML.  
- `robocode/robots/github/` — código-fonte Java dos robôs (`Astroboys.java`, `Corners.java`).  
- `libs/` — jars do Robocode e dependências incluídas.  
- `battles/` — arquivos `.battle` pré-configurados.  
- `.history/` — versões anteriores dos scripts/workflows.

---

## 🛠️ Como rodar localmente (rápido)

1. Instale Java (JDK 11+ recomendado).  
2. Torne o script executável: `chmod +x scripts/testar_batalha.sh`.  
3. Execute: `bash scripts/testar_batalha.sh` — isso gera `battle_logs/` e um `report.html`.  
4. Visualize os logs localmente ou baixe o artefato no GitHub Actions.

---

## 🧩 CI / GitHub Actions (o que faz)

- Workflow: `.github/workflows/ci.yml` (executa em push/PR para `main`).  
- Tarefas: checkout, configurar Java, rodar Checkstyle, SpotBugs, compilar robôs, executar batalha via script, coletar logs e enviar `battle_logs/` como artefato.  
- Artefatos: `battle_logs/` (report.html + logs).

---

## 🧾 O que o script de batalha faz

- Gera `.battle` em `battle_logs/`.  
- Invoca Robocode (jars incluídos ou instalação local).  
- Registra resultados e gera `report.html`.

---

## ✅ Como inspecionar resultados

- Abra `battle_logs/report.html`.  
- Veja `battle_logs/sample_result.txt` e logs brutos para detalhes por rodada.

---

## 🧰 Checkstyle & SpotBugs

O CI integra Checkstyle (regras Google) e SpotBugs. Use localmente para feedback: `mvn checkstyle:check` / `mvn com.github.spotbugs:spotbugs-maven-plugin:check` (se usar Maven).

---

## 👨‍🏫 Créditos & contexto

- Autor: **Nycolas Antony Salvego** (ZYONSpiral084).  
- Contexto: atividades acadêmicas na FATEC Ourinhos.

---

## 📜 Licença

Uso acadêmico / educacional. Cite o autor ao reutilizar.

