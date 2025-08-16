# Projeto de Automação de Testes de API com Postman e CI/CD

![Status do Workflow](https://github.com/DimitriRBarros/API-Tests-Booker/actions/workflows/api-tests.yml/badge.svg)

## 📝 Descrição

Este projeto demonstra a criação e automação de uma suíte de testes de integração para uma API RESTful. Utilizando **Postman** para a elaboração dos cenários, **Newman** para a execução via linha de comando e **GitHub Actions** para a integração contínua (CI/CD), o projeto valida um fluxo completo de operações CRUD, autenticação e tratamento de erros.

A API utilizada para os testes foi a [Restful-booker](https://restful-booker.herokuapp.com/), um serviço público excelente para praticar testes de API.

---

## ✨ Funcionalidades Testadas

A suíte de testes está estruturada para cobrir os seguintes aspectos da API:

* **Autenticação:** Geração de token de acesso.
* **CRUD Completo de Reservas (Bookings):**
    * `CREATE`: Criação de uma nova reserva.
    * `READ`: Leitura dos dados de uma reserva específica.
    * `UPDATE`: Atualização completa de uma reserva existente.
    * `DELETE`: Exclusão de uma reserva.
* **Validação de Contrato (Schema Validation):** Garante que a estrutura das respostas da API (JSON Schema) não seja alterada inesperadamente.
* **Tratamento de Erros:** Valida se a API retorna os códigos de status corretos para cenários de falha (ex: `404 Not Found` ao buscar um recurso inexistente).

---

## 🚀 Tecnologias Utilizadas

* **Postman:** Ferramenta para design, documentação e execução de testes de API.
* **Newman:** Executor de coleções do Postman via linha de comando, essencial para automação e integração contínua.
* **Node.js:** Ambiente de execução para o Newman.
* **Git & GitHub:** Para versionamento de código e hospedagem do repositório.
* **GitHub Actions:** Plataforma de CI/CD para automação do pipeline de testes.
* **newman-reporter-htmlextra:** Biblioteca para geração de relatórios de teste em HTML, ricos em detalhes.

---

## ⚙️ Como Rodar o Projeto Localmente

Siga os passos abaixo para executar a suíte de testes no seu ambiente local.

### Pré-requisitos

* [Node.js](https://nodejs.org/en/) (versão 18 ou superior)
* [Git](https://git-scm.com/downloads)

### Passos

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/DimitriRBarros/API-Tests-Booker.git](https://github.com/DimitriRBarros/API-Tests-Booker.git)
    cd API-Tests-Booker
    ```

2.  **Instale as dependências (Newman e o Reporter):**
    ```bash
    npm install -g newman newman-reporter-htmlextra
    ```

3.  **Execute os testes:**
    ```bash
    newman run collection.json -e environment.json -r "cli,htmlextra" --reporter-htmlextra-export "reports/api_test_report.html"
    ```

4.  **Visualize o relatório:**
    Após a execução, um relatório detalhado será gerado em `reports/api_test_report.html`. Abra este arquivo em seu navegador para ver os resultados.

---

## 🤖 Automação e Integração Contínua (CI/CD)

Este projeto está configurado com um pipeline de integração contínua utilizando **GitHub Actions**. O workflow está definido no arquivo `.github/workflows/api-tests.yml`.

O pipeline é acionado automaticamente nos seguintes eventos:
* `push` na branch `main`.
* Abertura de `pull request` para a branch `main`.

A cada execução, o pipeline realiza os mesmos passos que a execução local e, ao final, disponibiliza o relatório HTML como um **artefato** que pode ser baixado para análise. O status da última execução pode ser verificado pelo badge no topo deste README.