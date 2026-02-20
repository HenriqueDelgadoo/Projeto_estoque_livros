# 📚 SenaiStock

Sistema Web completo para controle de estoque de livros didáticos do SENAI, desenvolvido com **PHP + Laravel**.

---

## 📌 Sobre o Projeto

O **SenaiStock** é um sistema web que permite controlar a entrada e saída de livros do almoxarifado, mantendo o saldo sempre atualizado e evitando falta de material nas turmas.

O sistema resolve o problema de controle manual do estoque, garantindo:

- ✔ Controle de saldo em tempo real
- ✔ Bloqueio de retirada com estoque insuficiente
- ✔ Registro de todas as movimentações
- ✔ Monitoramento de estoque baixo
- ✔ Autenticação de usuários

---

## 🚀 Tecnologias Utilizadas

- PHP 8+
- Laravel 10+
- MySQL
- Bootstrap (Interface)
- Laravel Breeze (Autenticação)

---

## 🏗️ Arquitetura

O sistema segue o padrão **MVC (Model - View - Controller)** do Laravel:

- **Model:** Regras de negócio e acesso ao banco
- **View:** Interface com Blade
- **Controller:** Controle das requisições
- **Middleware:** Controle de acesso

---

## 🔐 Funcionalidades

### 1️⃣ Autenticação
- Login e Logout
- Controle por perfil (Almoxarife / Coordenador)

---

### 2️⃣ Cadastro de Livros (CRUD)
- Cadastrar livro
- Editar livro
- Excluir livro
- Listar livros
- ISBN único
- Controle de quantidade em estoque

Campos:
- Título
- ISBN
- Matéria
- Quantidade

---

### 3️⃣ Entrada de Estoque
- Selecionar livro
- Informar quantidade recebida
- Soma automática ao estoque
- Registro no histórico como **ENTRADA**

Regra:
- Quantidade deve ser maior que zero

---

### 4️⃣ Saída de Estoque
- Selecionar livro
- Informar quantidade retirada
- Informar destino (ex: Turma A - Elétrica)
- Subtração automática do estoque
- Registro no histórico como **SAÍDA**

Regra de Negócio:
- ❌ Não permite retirada maior que o saldo disponível
- Exibe mensagem: "Estoque insuficiente"

---

### 5️⃣ Monitoramento de Estoque Baixo
- Lista livros com quantidade abaixo de 10 unidades
- Exibição com alerta visual

---

### 6️⃣ Histórico de Movimentações
Registra:
- Tipo (Entrada/Saída)
- Livro
- Usuário responsável
- Quantidade
- Destino (se saída)
- Data e hora

Permite filtros por:
- Tipo
- Data
- Livro

---

## 🗄️ Banco de Dados

### Tabela: users
- id
- name
- email
- password
- perfil
- timestamps

---

### Tabela: livros
- id
- titulo
- isbn (único)
- materia
- quantidade
- timestamps

---

### Tabela: movimentacoes
- id
- tipo (ENTRADA / SAIDA)
- livro_id
- user_id
- quantidade
- destino (nullable)
- timestamps

---

## 🛠️ Instalação do Projeto

### 1️⃣ Clonar o repositório

```bash
git clone https://github.com/seu-usuario/senai-stock.git
cd senai-stock
```

---

### 2️⃣ Instalar dependências

```bash
composer install
npm install
```

---

### 3️⃣ Configurar ambiente

Copie o arquivo:

```bash
cp .env.example .env
```

Configure o banco de dados no `.env`:

```env
DB_DATABASE=senai_stock
DB_USERNAME=root
DB_PASSWORD=
```

---

### 4️⃣ Gerar chave da aplicação

```bash
php artisan key:generate
```

---

### 5️⃣ Executar migrations

```bash
php artisan migrate
```

---

### 6️⃣ Rodar o servidor

```bash
php artisan serve
```

Acesse no navegador:

```
http://localhost:8000
```

---

## 📂 Estrutura do Projeto

```
app/
 ├── Models/
 │    ├── Livro.php
 │    └── Movimentacao.php
 │
 ├── Http/
 │    ├── Controllers/
 │    │      ├── LivroController.php
 │    │      ├── EstoqueController.php
 │    │      └── MovimentacaoController.php
 │
resources/
 ├── views/
 │    ├── dashboard.blade.php
 │    ├── livros/
 │    ├── estoque/
 │    └── movimentacoes/
```

---

## 🔒 Regras de Negócio

- Não permitir estoque negativo
- ISBN deve ser único
- Apenas usuários autenticados podem alterar estoque
- Toda movimentação deve ser registrada
- Quantidade deve ser maior que zero

---

## 📈 Melhorias Futuras

- Dashboard com gráficos
- Exportação em PDF
- Controle por múltiplas unidades
- Notificações automáticas de estoque baixo
- Sistema de relatórios avançado

---

## 👨‍💻 Autor

Henrique Delgado;
Gabriel Marques Terra;
Lucas Terminiello:

---
