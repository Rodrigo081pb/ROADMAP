# **CI/CD**

## **1. O que é CI/CD?**
CI/CD significa **Continuous Integration (Integração Contínua) e Continuous Delivery/Deployment (Entrega/Implantação Contínua)**. Ele resolve problemas comuns no desenvolvimento de software, como:
- **Automação de builds e testes** → Sem precisar compilar/testar manualmente.
- **Menos bugs em produção** → Identificação precoce de falhas.
- **Entrega rápida de novas versões** → Evita longos ciclos de desenvolvimento.

🔥 **Explicação prática:**  
Pensa que tu tá desenvolvendo um site. No processo tradicional:
1. Tu escreve o código e sobe pro GitHub/GitLab.
2. Alguém precisa testar manualmente e aprovar.
3. Depois, faz deploy na mão pro servidor.

Com **CI/CD**, tudo é automatizado:
✅ O código é testado automaticamente.  
✅ Se tudo estiver certo, é gerado um **build**.  
✅ O build é enviado para o servidor sem tu precisar fazer nada.  

---

## **2. Benefícios do CI/CD**
- **Automação** → Testes, builds e deploys automáticos.
- **Menos bugs** → Detecta erros rapidamente com testes automatizados.
- **Entrega rápida** → Reduz tempo de espera para lançamentos.
- **Facilidade de rollback** → Se algo der errado, pode voltar para a versão anterior rapidamente.
- **Padronização** → Todos os desenvolvedores seguem o mesmo fluxo.

💡 **Empresas que usam CI/CD**: Google, Netflix, Amazon, Facebook… **CI/CD é padrão na indústria de software.**

---

## **3. Diferença entre CI, CD e DevOps**
| Conceito | O que faz? | Exemplo |
|----------|-----------|---------|
| **CI (Continuous Integration)** | Integração contínua do código em um repositório central. | Rodar testes automaticamente toda vez que um dev faz um commit. |
| **CD (Continuous Delivery)** | Automação do build e preparação para deploy. | Criar builds e deixar pronto para ser enviado ao servidor com um clique. |
| **CD (Continuous Deployment)** | Deploy automático após os testes passarem. | Se o código passar nos testes, já entra em produção automaticamente. |
| **DevOps** | Cultura que une devs e ops para automação. | Uso de CI/CD + monitoramento + infraestrutura automatizada. |

📌 **Resumo rápido:**  
- CI = Testes automáticos e integração de código.  
- CD (Delivery) = Preparação para deploy (manual).  
- CD (Deployment) = Deploy automático.  
- DevOps = Cultura que inclui CI/CD + infraestrutura + monitoramento.

---

## **4. Ferramentas Populares de CI/CD**
Tem várias ferramentas, mas as mais famosas são:
- **GitHub Actions** → CI/CD integrado ao GitHub.
- **GitLab CI/CD** → CI/CD integrado ao GitLab.
- **Jenkins** → CI/CD open-source, muito usado por empresas.
- **CircleCI** → CI/CD fácil de usar, integrado ao GitHub.
- **TravisCI** → CI/CD baseado em nuvem.

🔥 **Qual usar?**  
- Se usa **GitHub**, começa com **GitHub Actions**.  
- Se usa **GitLab**, vai de **GitLab CI/CD**.  
- Se quer algo mais customizável, usa **Jenkins**.

---

## **5. Ciclo de Vida do CI/CD**

1️⃣ **Desenvolvedor faz commit no Git** 📝  
2️⃣ **CI entra em ação** 🚀  
   - Roda testes automatizados  
   - Verifica qualidade do código  
   - Faz o build da aplicação  
3️⃣ **CD entra em ação** 🔄  
   - Se tudo passar, gera um artefato (arquivo final do app)  
   - Envia para um ambiente de homologação  
   - (Se for **Continuous Deployment**) → já faz deploy para produção  

🔥 **Resumo prático:**  
Tu escreveu código → CI verificou se tá certo → CD empacotou e botou no ar automaticamente.

---

## **6. Pré-requisitos para trabalhar com CI/CD**
Antes de meter a mão na massa, tu precisa saber:
- **Git e GitHub/GitLab** → Comandos básicos (commit, push, pull, branches).
- **Docker** → Para rodar aplicações em containers.
- **Cloud Computing** → AWS, Firebase ou outra plataforma de deploy.
- **YAML** → CI/CD usa muito arquivos `.yml` para configurar pipelines.



