# **MÓDULO 2 - GITHUB ACTIONS (CI/CD COM GITHUB)**  

Agora vamos meter a mão na massa com **GitHub Actions**, que é a ferramenta de CI/CD integrada ao GitHub. Bora aprender do zero ao avançado! 🚀  

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

## **3. Criando um Workflow Básico**  

Vamos criar nosso primeiro pipeline no GitHub Actions!  

### **Passo 1 - Criar a pasta de workflows**  
No teu repositório do GitHub, cria a seguinte estrutura:  

```
📂 meu-projeto/
 ├── 📂 .github/
 │    ├── 📂 workflows/
 │         ├── 📝 ci-cd.yml
```

### **Passo 2 - Criar um workflow YAML**  
Abre o arquivo `.github/workflows/ci-cd.yml` e adiciona isso:

```yaml
name: Meu Primeiro Workflow

on: 
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout do código
        uses: actions/checkout@v3

      - name: Configurar Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 16

      - name: Instalar dependências
        run: npm install

      - name: Rodar testes
        run: npm test
```

📌 **Explicação do código:**  
- **on: push** → O pipeline roda toda vez que alguém fizer `push` na `main`.  
- **jobs: build** → Define um job chamado "build".  
- **runs-on: ubuntu-latest** → Roda o job em um servidor Ubuntu.  
- **steps** → Lista de etapas a serem executadas.  
- **actions/checkout@v3** → Baixa o código do repositório.  
- **actions/setup-node@v3** → Instala o Node.js.  
- **npm install / npm test** → Instala dependências e roda testes.  

---

## **4. Rodando o Workflow**
Agora é só **fazer um commit e um push** pro GitHub, e o workflow vai rodar automaticamente!  

### **Como ver o status do workflow?**  
1️⃣ Vai no repositório no GitHub.  
2️⃣ Clica na aba **Actions**.  
3️⃣ Escolhe o workflow **"Meu Primeiro Workflow"**.  
4️⃣ Vê os logs da execução!  

Se tudo der certo, tu vai ver algo assim: ✅ **Workflow concluído com sucesso!**  

---

## **5. Automação de Testes e Builds**
Agora vamos rodar testes automaticamente e construir o projeto antes do deploy.  

### **Exemplo: CI/CD para uma API Python**
```yaml
name: CI/CD Python API

on: [push]

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout do código
        uses: actions/checkout@v3

      - name: Configurar Python
        uses: actions/setup-python@v3
        with:
          python-version: 3.9

      - name: Instalar dependências
        run: pip install -r requirements.txt

      - name: Rodar testes
        run: pytest
```
🔥 **Explicação:**  
- Usa `setup-python@v3` para instalar Python.  
- Instala dependências do `requirements.txt`.  
- Roda **testes automatizados com pytest**.  

📌 Se os testes falharem, o deploy **não acontece** (evita colocar código bugado em produção!).

---

## **6. Deploy Automático com GitHub Actions**
Agora vamos **deployar um projeto automaticamente** depois que os testes passarem.

### **Exemplo: Deploy para Firebase Hosting**
```yaml
name: Deploy Firebase

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout do código
        uses: actions/checkout@v3

      - name: Instalar Firebase CLI
        run: npm install -g firebase-tools

      - name: Autenticar no Firebase
        run: firebase login:ci --token ${{ secrets.FIREBASE_TOKEN }}

      - name: Deploy para o Firebase
        run: firebase deploy --only hosting
```

📌 **Destaques:**  
- Instala o **Firebase CLI**.  
- Usa **variáveis de ambiente** (`secrets.FIREBASE_TOKEN`) para segurança.  
- Faz deploy **automaticamente** para o Firebase Hosting.  

---

## **7. Melhorando o Pipeline (Cache, Matriz, Notificações)**
### **7.1 - Cache para acelerar builds**
Se teu projeto for grande, tu pode salvar dependências em cache para rodar mais rápido:

```yaml
      - name: Cache do Node.js
        uses: actions/cache@v3
        with:
          path: ~/.npm
          key: ${{ runner.os }}-node-${{ hashFiles('**/package-lock.json') }}
          restore-keys: |
            ${{ runner.os }}-node-
```

📌 O cache evita que o `npm install` precise rodar toda vez. Isso **acelera o pipeline**!

---

### **7.2 - Testando em Múltiplos Ambientes (Matrix Builds)**
Se precisar testar um projeto em várias versões do **Node.js**, usa **Matrix Builds**:

```yaml
  test:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        node-version: [14, 16, 18]

    steps:
      - name: Configurar Node.js
        uses: actions/setup-node@v3
        with:
          node-version: ${{ matrix.node-version }}
```

📌 Esse pipeline roda os testes **3 vezes**, uma pra cada versão do Node.js.

---

### **7.3 - Notificações no Slack**
Tu pode receber um alerta no **Slack** quando o deploy for concluído:

```yaml
      - name: Notificação no Slack
        uses: rtCamp/action-slack-notify@v2
        env:
          SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK }}
          SLACK_CHANNEL: "#devops"
          SLACK_MESSAGE: "Deploy concluído com sucesso! 🚀"
```

---


✔️ O que é o GitHub Actions e como funciona.  
✔️ Criamos um **workflow básico**.  
✔️ Rodamos **testes automatizados**.  
✔️ Fizemos **deploy automático**.  
✔️ Melhoramos o pipeline com **cache, matrix e notificações**.  

---

**Terminei pronto para falar sobre GitLab CI/CD!** 🚀  

Diz aí, boy, bora pro **GitLab CI/CD** ou tem alguma dúvida antes de seguir?