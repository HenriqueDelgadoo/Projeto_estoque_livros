# 📚 SenaiStock

Sistema Web completo para controle de estoque de livros didáticos do SENAI, desenvolvido com **PHP + Laravel**.

---

## 📌 Sobre o Projeto

O **SenaiStock** é um sistema web que permite controlar a entrada e saída de livros do almoxarifado, mantendo o saldo sempre atualizado e evitando falta de material nas turmas.

O sistema resolve o problema de controle manual do estoque, garantindo:

* ✔ **Controle de saldo em tempo real**
* ✔ **Bloqueio de retirada** com estoque insuficiente
* ✔ **Registro de todas as movimentações** (Auditabilidade)
* ✔ **Monitoramento de estoque baixo**
* ✔ **Autenticação segura** de usuários

---

## 🔗 Links Úteis e Documentação

* 📑 **Documentação Detalhada (Milanote):** [Acesse aqui](https://app.milanote.com/1VTuyb1wNggDbB?p=iRUzxTpROXh)
* 🎨 **Protótipo (Figma):** [Link para o Projeto no Figma](https://www.figma.com/design/qRQOzPSOp29ZR1pDYgBzO1/Senai-Estoque?node-id=0-1&m=dev&t=KzvO60ciM8k8olok-1)
* 📄 **Arquivo de Documentação:** Consulte o arquivo `Documentação SenaiStock` na raiz deste repositório.

---

## 🚀 Tecnologias Utilizadas

* **Linguagem:** PHP 8+
* **Framework:** Laravel 10+
* **Banco de Dados:** MySQL
* **Frontend:** Bootstrap (Interface)
* **Autenticação:** Laravel Breeze

---

## 🏗️ Arquitetura

O sistema segue o padrão **MVC (Model - View - Controller)** do Laravel:

* **Model:** Regras de negócio e acesso ao banco de dados.
* **View:** Interface do usuário construída com Blade Engines.
* **Controller:** Gerenciamento do fluxo de requisições.
* **Middleware:** Camada de segurança e controle de acesso.

---

## 🔐 Funcionalidades

### 1. Autenticação
* Login e Logout seguros.
* Controle por perfil de acesso (**Almoxarife / Coordenador**).

### 2. Cadastro de Livros (CRUD)
* Operações completas: Cadastrar, Editar, Excluir e Listar.
* Validação de **ISBN único**.
* Campos: Título, ISBN, Matéria e Quantidade.

### 3. Movimentações (Entrada e Saída)
* **Entrada:** Soma automática ao estoque com registro histórico.
* **Saída:** Subtração automática com bloqueio de **estoque negativo**.
* **Regra:** Se a retirada for maior que o saldo, o sistema exibe: *"Estoque insuficiente"*.

### 4. Relatórios e Alertas
* **Monitoramento:** Lista automática de livros com menos de 10 unidades.
* **Histórico:** Filtros por tipo (Entrada/Saída), data e livro específico.

---

## 🗄️ Estrutura do Banco de Dados

### Tabela: `users`
| Campo | Tipo |
| :--- | :--- |
| id | PK |
| name | string |
| email | string (unique) |
| perfil | enum (Almoxarife/Coordenador) |

### Tabela: `livros`
| Campo | Tipo |
| :--- | :--- |
| id | PK |
| titulo | string |
| isbn | string (unique) |
| materia | string |
| quantidade | integer |

---

## 🛠️ Instalação do Projeto

Siga os passos abaixo para rodar o projeto localmente:

```bash
# 1. Clonar o repositório
git clone [https://github.com/seu-usuario/senai-stock.git](https://github.com/seu-usuario/senai-stock.git)
cd senai-stock

# 2. Instalar dependências
composer install
npm install

# 3. Configurar ambiente
cp .env.example .env

# Configure o banco de dados no .env:
# DB_DATABASE=senai_stock
# DB_USERNAME=root
# DB_PASSWORD=

# 4. Gerar chave e migrar banco
php artisan key:generate
php artisan migrate

# 5. Rodar o servidor
php artisan serve

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

## 👨‍💻 Autores

Henrique Delgado;
Gabriel Marques Terra;
Lucas Terminiello:

---
