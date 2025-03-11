# **GITLAB CI/CD** 🚀  

---

## **1️⃣ O que é o GitLab CI/CD?**
O **GitLab CI/CD** é a ferramenta de **Integração e Entrega Contínua** integrada ao GitLab. Ele permite:  

✅ Automatizar **builds, testes e deploys** diretamente no GitLab.  
✅ Criar **pipelines personalizados** com etapas separadas (build, test, deploy).  
✅ Integrar com **Docker, Kubernetes, AWS, Firebase, servidores próprios**.  
✅ Rodar pipelines em **máquinas locais, servidores ou runners na nuvem**.  

**📌 Diferença entre GitHub Actions e GitLab CI/CD**  
| GitHub Actions | GitLab CI/CD |
|---------------|-------------|
| Pipelines definidos em `.github/workflows/` | Pipelines definidos em `.gitlab-ci.yml` |
| Usa **Actions** da comunidade | Usa **Executores (Runners)** |
| Executa workflows em runners do GitHub | Pode usar runners locais ou na nuvem |
| CI/CD só funciona em repositórios GitHub | CI/CD funciona no próprio GitLab |

---

## **2️⃣ Criando um pipeline no GitLab CI/CD**  
Diferente do GitHub Actions, o **GitLab usa um único arquivo** chamado **`.gitlab-ci.yml`** para definir todo o pipeline.  

### **📌 Passo 1: Criar o arquivo `.gitlab-ci.yml`**
No repositório do GitLab, cria o arquivo na raiz:

```
📂 meu-projeto/
 ├── 📄 .gitlab-ci.yml
 ├── 📂 src/
 ├── 📂 tests/
 ├── 📄 requirements.txt
 ├── 📄 README.md
```

Agora abre o arquivo `.gitlab-ci.yml` e adiciona um pipeline básico:

```yaml
stages:
  - test
  - build

test_job:
  stage: test
  image: python:3.9
  before_script:
    - pip install --upgrade pip
    - pip install -r requirements.txt
  script:
    - pytest

build_job:
  stage: build
  script:
    - echo "Construindo aplicação..."
    - python setup.py sdist
```

📌 **Explicação:**  
- Define **duas etapas (`stages`)**: `test` e `build`.  
- `test_job`:  
  ✅ Usa **Python 3.9** para rodar testes com `pytest`.  
- `build_job`:  
  ✅ Constrói um pacote Python (`setup.py sdist`).  

Agora faz um **commit e push** para o GitLab:

```bash
git add .gitlab-ci.yml
git commit -m "Adicionando pipeline do GitLab CI/CD"
git push origin main
```

---

## **3️⃣ Rodando o pipeline no GitLab**
Agora que o `.gitlab-ci.yml` foi adicionado:  

1️⃣ Vai no repositório **GitLab → CI/CD → Pipelines**.  
2️⃣ Tu vai ver um **pipeline rodando automaticamente**.  
3️⃣ Clica nele para ver os logs das etapas `test` e `build`.  

Se tudo estiver certo, os **jobs** vão passar ✅.

---

## **4️⃣ Personalizando o Pipeline**
Agora que já rodamos o primeiro pipeline, bora melhorar ele com:

### **🔹 Executando testes em diferentes versões do Python**
Se tu quer testar em **Python 3.7, 3.8, 3.9, 3.10**, usa `matrix jobs`:

```yaml
test_job:
  stage: test
  image: python:$PYTHON_VERSION
  variables:
    PYTHON_VERSION: "3.9"
  script:
    - pip install -r requirements.txt
    - pytest
  parallel:
    matrix:
      - PYTHON_VERSION: ["3.7", "3.8", "3.9", "3.10"]
```

Isso **roda os testes em várias versões do Python ao mesmo tempo**! 🚀  

---

### **🔹 Usando cache para acelerar builds**
Pra evitar instalar dependências toda vez, usa cache:

```yaml
cache:
  paths:
    - .venv/
    - ~/.cache/pip/
```

Agora, sempre que o pipeline rodar, ele vai reaproveitar dependências antigas.

---

### **🔹 Criando um Runner Local**
Se tu quer rodar os pipelines em um **servidor próprio**, instala um **GitLab Runner**:

1. No **GitLab → Settings → CI/CD → Runners**, pega o **token do runner**.  
2. No servidor, instala o runner:

```bash
curl -L https://packages.gitlab.com/install/repositories/runner/gitlab-runner/script.deb.sh | sudo bash
sudo apt install gitlab-runner
```

3. Registra o runner:

```bash
sudo gitlab-runner register
```

4. Agora ele vai aparecer na aba **Runners** do GitLab.  

---

### **🔹 Fazendo Deploy no Heroku**
Se tu quer fazer deploy no **Heroku**, adiciona isso ao `.gitlab-ci.yml`:

```yaml
deploy:
  stage: deploy
  script:
    - echo "Deploy no Heroku..."
    - heroku login -i
    - git push heroku main
  only:
    - main
```

Agora, sempre que um **commit for feito na `main`**, ele faz deploy automaticamente! 🚀  

---

## **🔥 Resumo**
✔️ Criamos um **pipeline básico no GitLab CI/CD**.  
✔️ Adicionamos **testes automatizados** com `pytest`.  
✔️ Melhoramos com **cache e testes em múltiplas versões do Python**.  
✔️ Criamos um **GitLab Runner local** para rodar pipelines no próprio servidor.  
✔️ Configuramos **deploy automático para o Heroku**.  

---
