# **GITHUB ACTIONS (CI/CD COM GITHUB)**  
---

## **1. O que é o GitHub Actions?**  
- É a ferramenta de CI/CD do **GitHub**.  
- Permite criar **pipelines automatizados** diretamente no repositório.  
- Usa **arquivos YAML** para definir fluxos de trabalho (workflows).  
- Funciona com **GitHub Runners** (máquinas que executam os jobs).  

💡 **Diferenciais do GitHub Actions:**  
✔️ **Totalmente integrado ao GitHub** (commits, PRs, issues).  
✔️ **Fácil de usar** (sem precisar configurar servidores).  
✔️ **Grátis para repositórios públicos**.  
✔️ **Suporte a múltiplas linguagens** (Python, Java, Node.js, etc.).  

---

## **2. Estrutura do GitHub Actions**  

No GitHub Actions, um pipeline é chamado de **Workflow**, e ele é composto por:  

| Conceito | O que faz? |
|----------|-----------|
| **Workflow** | O fluxo de CI/CD definido num arquivo `.yml`. |
| **Jobs** | Conjunto de etapas dentro do workflow. |
| **Steps** | Comandos executados dentro de um job. |
| **Actions** | Plugins reutilizáveis que facilitam a automação. |
| **Runners** | Servidores onde os jobs são executados. |

🔥 **Fluxo do GitHub Actions:**  
1️⃣ Dev faz um **commit/push** no repositório.  
2️⃣ O **workflow** é disparado automaticamente.  
3️⃣ O **job** roda os **steps** necessários (testes, build, deploy).  
4️⃣ Se tudo der certo, faz o **deploy automático**.  

---
