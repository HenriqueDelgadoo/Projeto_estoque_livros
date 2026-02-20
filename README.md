# Projeto_estoque_livros
📚 SenaiStock – Sistema Completo de Controle de Estoque de Livros Didáticos

Sistema Web completo desenvolvido para o SENAI, com Back-End + Front-End + Banco de Dados, permitindo controle total de livros didáticos no almoxarifado.

🏫 Contexto do Projeto

O almoxarifado do SENAI recebe grandes remessas de livros, mas não possui controle preciso das saídas. Isso causa:

Estoque zerado inesperadamente

Atrasos na distribuição para turmas

Falta de planejamento de reposição

O SenaiStock resolve esse problema com um sistema completo de gestão de estoque, com autenticação, controle de movimentações e relatórios.

🖥️ Visão Geral do Sistema
4

O sistema é composto por:

🔐 Tela de Login

📚 Cadastro de Livros

➕ Registro de Entrada (Abastecimento)

➖ Registro de Saída (Baixa Manual)

📊 Monitoramento de Estoque Baixo

📄 Histórico de Movimentações

👤 Controle de Usuários

🏗️ Arquitetura do Sistema
🔹 1. Front-End

Interface Web Responsiva

Tecnologias sugeridas:

React ou HTML + CSS + JavaScript

Bootstrap ou Tailwind

🔹 2. Back-End

API REST responsável pelas regras de negócio

Tecnologias sugeridas:

Node.js + Express
ou

Java + Spring Boot

🔹 3. Banco de Dados

PostgreSQL ou MySQL

🔐 Funcionalidades do Sistema
1️⃣ Autenticação e Controle de Acesso
Perfis de Usuário:
Perfil	Permissões
Almoxarife	Gerencia entradas e saídas
Coordenador	Visualiza relatórios e estoque
Funcionalidades:

Login com email e senha

Senhas criptografadas

Controle por perfil

Sessão com Token JWT

2️⃣ Cadastro de Livros
Campos:

ID

Título

ISBN (Único)

Matéria

Quantidade em Estoque

Funcionalidades:

Cadastrar novo livro

Editar livro

Excluir livro

Listar todos os livros

3️⃣ Entrada de Estoque (Abastecimento)

Quando chegam caixas da editora:

Seleciona o livro

Informa a quantidade recebida

Sistema soma ao saldo atual

✔ Regra:

Quantidade deve ser maior que 0.

4️⃣ Saída de Estoque (Baixa Manual)

Funcionalidade principal do sistema.

Seleciona o livro

Informa quantidade retirada

Informa destino (ex: Turma A – Elétrica)

Sistema subtrai automaticamente

❗ Regra de Negócio:

Não permitir retirada maior que o saldo disponível.

Exibir mensagem: "Estoque Insuficiente"

5️⃣ Monitoramento de Estoque Baixo

Tela que exibe livros com quantidade abaixo de um valor mínimo (ex: 10 unidades).

Filtro por quantidade mínima

Alerta visual (cor vermelha)

Sugestão de reposição

6️⃣ Histórico de Movimentações

Cada entrada ou saída deve gerar um registro:

Campos:

Tipo (Entrada ou Saída)

Livro

Quantidade

Usuário responsável

Data e hora

Destino (no caso de saída)

Permite:

Filtro por data

Filtro por tipo

Relatório completo

🗄️ Modelo de Banco de Dados
Tabela: usuarios
CREATE TABLE usuarios (
    id SERIAL PRIMARY KEY,
    nome VARCHAR(100),
    email VARCHAR(100) UNIQUE,
    senha VARCHAR(255),
    perfil VARCHAR(20),
    criado_em TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
Tabela: livros
CREATE TABLE livros (
    id SERIAL PRIMARY KEY,
    titulo VARCHAR(150),
    isbn VARCHAR(20) UNIQUE,
    materia VARCHAR(100),
    quantidade INTEGER DEFAULT 0,
    criado_em TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
Tabela: movimentacoes
CREATE TABLE movimentacoes (
    id SERIAL PRIMARY KEY,
    tipo VARCHAR(10), -- ENTRADA ou SAIDA
    livro_id INTEGER REFERENCES livros(id),
    usuario_id INTEGER REFERENCES usuarios(id),
    quantidade INTEGER,
    destino VARCHAR(150),
    data_movimentacao TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
📂 Estrutura Completa do Projeto
senai-stock/
│
├── backend/
│   ├── controllers/
│   ├── services/
│   ├── repositories/
│   ├── middlewares/
│   ├── routes/
│   └── server.js
│
├── frontend/
│   ├── pages/
│   ├── components/
│   ├── services/
│   └── App.js
│
├── database/
│   └── schema.sql
│
├── .env
└── README.md
📊 Fluxo de Funcionamento

Usuário faz login

Acessa o painel principal

Visualiza estoque atual

Registra entrada ou saída

Sistema atualiza saldo

Movimentação é registrada no histórico

Sistema verifica automaticamente se estoque está abaixo do mínimo

🎨 Telas do Sistema

Tela de Login

Dashboard Principal

Cadastro de Livros

Entrada de Estoque

Saída de Estoque

Estoque Baixo

Histórico de Movimentações

Gerenciamento de Usuários

🔐 Segurança

Senhas com Bcrypt

Autenticação via JWT

Middleware de autorização

Validação de dados

Bloqueio de estoque negativo

🚀 Como Executar
Backend
cd backend
npm install
npm run dev
Frontend
cd frontend
npm install
npm start

Servidor:

http://localhost:3000
📈 Possíveis Melhorias Futuras

Dashboard com gráficos (Chart.js)

Exportação de relatório em PDF

Controle por múltiplas unidades

Integração com ERP

Controle por lote

Notificação automática de estoque baixo

🧠 Diferencial do Projeto

✔ Sistema completo (não apenas API)
✔ Controle real de movimentações
✔ Regras de negócio implementadas
✔ Autenticação com níveis de acesso
✔ Estrutura pronta para expansão

Se quiser, posso agora gerar:

🎨 Protótipo visual das telas

📊 Diagrama ER

🧩 Diagrama de Caso de Uso

💻 Código completo pronto (Node ou Java)

📘 Versão formatada em padrão ABNT para entrega acadêmica
