# **Aula Completa de Requests e APIs REST**  
Bem-vindo a este README, boy! Aqui você encontra uma aula detalhada e melhorada sobre como trabalhar com **APIs REST** e a biblioteca **Requests** do Python. Tudo de forma prática, direta e sem complicações.

---

## **Índice**
1. [O que são APIs REST?](#o-que-sao-apis-rest)  
2. [Princípios do REST](#principios-do-rest)  
3. [Métodos HTTP mais usados](#metodos-http-mais-usados)  
4. [Instalando a biblioteca Requests](#instalando-a-biblioteca-requests)  
5. [Requisições GET, POST, PUT e DELETE](#requisicoes-get-post-put-e-delete)  
6. [Manipulando Respostas da API](#manipulando-respostas-da-api)  
7. [Tratando Erros e Exceções](#tratando-erros-e-excecoes)  
8. [Autenticação em APIs](#autenticacao-em-apis)  
9. [Boas Práticas](#boas-praticas)  
10. [Links Úteis e Referências](#links-uteis-e-referencias)  

---

## **O que são APIs REST?**
**API (Application Programming Interface)** é o conjunto de regras que permite que diferentes aplicações conversem entre si.  
- **REST (Representational State Transfer)** é um estilo arquitetural onde os recursos são acessados de forma simples e previsível por meio de **endpoints HTTP**.

Um exemplo de endpoint REST para acessar o usuário de ID = 1:

GET https://api.exemplo.com/users/1

Você faz uma **requisição HTTP** e o servidor retorna uma **resposta** (geralmente em JSON).

---

## **Princípios do REST**
1. **Stateless**  
   Cada requisição é independente; o servidor não guarda o estado da sessão no lado dele.

2. **Cacheable**  
   As respostas podem ser armazenadas em cache para melhor performance e escalabilidade.

3. **Client-Server**  
   O cliente (como navegador ou aplicação) e o servidor são separados, comunicando-se através de requisições HTTP.

4. **Uniform Interface**  
   Uso padronizado de métodos HTTP (GET, POST, PUT, DELETE) e URIs bem definidos.

---

## **Métodos HTTP mais usados**
- **GET**: Busca recursos ou dados.
- **POST**: Envia dados para o servidor (criar novos recursos).
- **PUT**: Atualiza recursos existentes (total ou parcialmente, dependendo da API).
- **DELETE**: Remove recursos.

Esses métodos seguem a ideia de **CRUD** (Create, Read, Update, Delete).

---

## **Instalando a biblioteca Requests**
Antes de começar, verifique se você tem o **Python** instalado (versão 3.x). Então, basta rodar:

```bash
pip install requests

- veja o arquivo requests_ipynb na pasta requests

## **Boas Práticas**

1. **Use sempre HTTPS**  
   - Proteja dados sensíveis de interceptações (_man-in-the-middle attacks_).

2. **Valide as respostas**  
   - Sempre verifique o `status_code` e trate erros com `try-except`.

3. **Documente sua API**  
   - Se você cria APIs, use ferramentas como **Swagger** ou **OpenAPI** para documentá-las.

4. **Evite chamar a API em loop sem controle**  
   - Limite a quantidade de requisições para não gerar sobrecarga (e possivelmente ser bloqueado).

5. **Separação de responsabilidades**  
   - Mantenha as chamadas de API isoladas em funções ou módulos específicos, facilitando testes e manutenção.

6. **Armazene chaves com segurança**  
   - Use variáveis de ambiente ou gerenciadores de segredos (Vault, AWS Secrets Manager, etc.) para proteger tokens de autenticação.

---

## **Links Úteis e Referências**

- **Documentação oficial do Requests**  
  [Requests Docs](https://requests.readthedocs.io/en/master/)
- **Documentação do Python**  
  [Python.org](https://www.python.org/doc/)
- **Códigos de status HTTP**  
  [MDN HTTP Status Codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)
- **OpenAPI / Swagger**  
  [OpenAPI](https://www.openapis.org/)
- **Ferramentas de teste de API**  
  [Postman](https://www.postman.com/) | [Insomnia](https://insomnia.rest/)
