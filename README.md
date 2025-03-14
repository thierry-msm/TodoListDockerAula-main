# TodoListDockerAula-main

## 📌 Sobre o Projeto

Este projeto consiste em uma **API de lista de tarefas (To-Do List)** desenvolvida com **Flask**, utilizando **SQLite** como banco de dados e servida por **Gunicorn**. Para garantir escalabilidade e balanceamento de carga, o projeto utiliza **Nginx** como proxy reverso e é totalmente **containerizado com Docker**. O **Docker Compose** é utilizado para orquestrar os serviços, permitindo fácil execução e manutenção.

## 🚀 Tecnologias Utilizadas

- **Flask** → Framework web para Python.
- **SQLite** → Banco de dados leve e fácil de usar.
- **Gunicorn** → Servidor WSGI para rodar aplicações Flask em produção.
- **Nginx** → Proxy reverso para balanceamento de carga e segurança.
- **Docker** → Para containerização do projeto.
- **Docker Compose** → Para orquestrar múltiplos containers.

---

## 📥 Pré-requisitos para rodar o projeto

Antes de começar, certifique-se de ter os seguintes requisitos instalados na sua máquina:

### **1️⃣ Instale o Docker e o Docker Compose**

- Caso não tenha em sua máquina, baixe e instale o [Docker Desktop](https://www.docker.com/products/docker-desktop/).
- Após instalar, verifique se tudo está funcionando executando:
  ```bash
  docker --version
  docker compose version
  ```

### **2️⃣ Instale o Python**

Se deseja rodar o projeto sem Docker, instale o **Python 3.9+** no seu sistema:

- [Baixar Python](https://www.python.org/downloads/)
- Verifique a instalação:
  ```bash
  python --version
  ```

---

## 🔥 Como executar o projeto

### **1️⃣ Clone o repositório**

Abra o terminal e execute:

```bash
git clone https://github.com/thierry-msm/TodoListDockerAula-main.git
cd TodoListDockerAula-main
```

### **2️⃣ Configurar e executar com Docker**

#### **📌 2.1 Construir a imagem Docker**

```bash
docker compose up -d --build
```

Isso cria e inicia os containers para **Flask, Nginx e Banco de Dados**.

#### **📌 2.2 Verificar se os containers estão rodando**

```bash
docker ps
```

Se tudo estiver correto, os containers `flask`, `nginx` e `sqlite` devem estar rodando.

### **3️⃣ Testar a API**

Após iniciar os serviços, a API estará disponível em:

```
http://127.0.0.1/
```

Para testar o balanceamento de carga, acesse várias vezes:

```bash
curl http://127.0.0.1/oi
```

Caso algo dê errado, verifique os logs:

```bash
docker logs -f flask
```

---

## ⚡ Como rodar sem Docker (opcional)

Caso queira rodar sem Docker, siga os passos abaixo:

### **1️⃣ Criar ambiente virtual e instalar dependências**

```bash
python -m venv .venv
source .venv/bin/activate  # Linux/macOS
.venv\Scripts\activate    # Windows
pip install -r requirements.txt
```

### **2️⃣ Criar o banco de dados**

```bash
python init_db.py
```

### **3️⃣ Rodar a aplicação Flask**

```bash
gunicorn -w 4 -b 0.0.0.0:5000 app:app
```

Agora acesse:

```
http://127.0.0.1:5000/
```

---

## 🛑 Como parar o projeto

Para **parar os containers** rodando no Docker:

```bash
docker compose down
```

Se quiser também **remover os volumes** (dados do banco serão apagados!):

```bash
docker compose down -v
```

Se estiver rodando **sem Docker**, pare o Flask com:

```bash
CTRL + C
```

---

## 🎯 Conclusão

Agora o projeto está rodando! 🚀

Se precisar de ajuda, abra uma **Issue** no repositório ou entre em contato. 😊

