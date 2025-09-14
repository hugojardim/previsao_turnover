# Sistema de Previsão de Turnover para Academias

![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)
![SciKit-Learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626.svg?style=flat&logo=Jupyter&logoColor=white)

## 📖 Sobre o Projeto

Este projeto consiste em um sistema de Machine Learning de ponta a ponta, projetado para ajudar academias de ginástica a monitorar a frequência de seus alunos e prever proativamente o risco de evasão (churn). Através de uma API robusta e processamento assíncrono, o sistema coleta dados de check-in, analisa o comportamento dos alunos e fornece insights valiosos para a retenção de clientes.

---

## ✨ Funcionalidades

- **👨‍💻 API RESTful:** Interface para gerenciamento de alunos e consulta de dados.
- **💾 Banco de Dados:** Persistência de dados dos alunos, check-ins e planos.
- **🚀 Processamento Assíncrono:** Uso de filas para tarefas como processamento de check-ins em massa e geração de relatórios.
- **🤖 Modelo de IA:** Um modelo de Machine Learning que calcula a probabilidade de um aluno cancelar sua matrícula.

---

## 🛠️ Tecnologias Utilizadas

- **Backend:** Python (Flask ou FastAPI)
- **Banco de Dados:** PostgreSQL
- **Fila de Mensagens:** RabbitMQ
- **Machine Learning:** Scikit-learn, Pandas
- **Documentação da API:** Swagger (ou similar)

---

## 🚀 Como Começar

Siga os passos abaixo para configurar e executar o projeto em seu ambiente local.

### Pré-requisitos

- Python 3.8+
- PostgreSQL
- RabbitMQ
- Git

### Instalação

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/hugojardim/previsao_turnover.git
   cd previsao_turnover
   ```

2. **Crie e ative um ambiente virtual:**
   ```bash
   python -m venv venv
   source venv/bin/activate  # No Windows, use `venv\Scripts\activate`
   ```

3. **Instale as dependências:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure o Banco de Dados:**
   - Crie um banco de dados no PostgreSQL.
   - Renomeie o arquivo `.env.example` para `.env` e preencha com as suas credenciais do banco de dados.
   - Execute o script de inicialização para criar as tabelas:
     ```bash
     python init_db.py
     ```

### Execução

1. **Inicie o servidor da API:**
   ```bash
   uvicorn main:app --reload  # Exemplo para FastAPI
   ```

2. **Inicie os workers do RabbitMQ (em outro terminal):**
   ```bash
   celery -A tasks worker --loglevel=info # Exemplo de comando
   ```

Acesse a documentação interativa da API em `http://127.0.0.1:8000/docs`.

---

## 🤖 Modelo de Previsão de Churn

O modelo de Machine Learning foi treinado para prever a probabilidade de um aluno evadir, com base nas seguintes features:

- Frequência semanal de visitas
- Tempo decorrido desde o último check-in
- Duração média das visitas na academia
- Tipo de plano contratado

O notebook Jupyter com o processo de treinamento e análise do modelo pode ser encontrado em: `notebooks/treinamento_modelo.ipynb`.

---

## Endpoints da API

### Alunos
- `POST /aluno/registro`: Registra um novo aluno.
- `POST /aluno/checkin`: Registra um check-in (entrada) de um aluno na academia.
- `GET /aluno/{id}/frequencia`: Retorna o histórico de frequência de um aluno específico.
- `GET /aluno/{id}/risco-churn`: Retorna a probabilidade de churn calculada pelo modelo de IA.

---

## 📝 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.
