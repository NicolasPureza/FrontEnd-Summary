# Aula 04 — Consumindo APIs no Front-end

**Disciplina:** Frameworks Front-end
**Foco:** APIs REST, Protocolo HTTP, formato JSON, criação de APIs com Express.js, deploy no Render e consumo no front-end.
**Instituição:** SENAI
**Professor:** Prof. Me. Deivison S. Takatu (`deivison.takatu@edu.senai.br`)

---

## 📌 Sumário

- Introdução às APIs e Arquitetura REST
- Protocolo HTTP e Métodos
- Como Funciona uma Requisição na Prática
- Endpoints e Repositórios de APIs Públicas
- Formato JSON (JavaScript Object Notation)
- Atividade Prática 01 (Pesquisa de Projetos)
- Servidor Backend e Web Services
- Framework Express.js (Node.js vs. Express)
- Passo a Passo: Criando uma API REST com Express
- Plataforma Render para Hospedagem em Nuvem
- Atividade Prática 02 (Deploy e Consumo de API)
- Resumo do Fluxo
- Referências Bibliográficas

---

## 1. Introdução às APIs e Arquitetura REST

Uma **API** (*Application Programming Interface*) é um conjunto de protocolos, rotinas e ferramentas padronizadas para a construção de software. Ela define as regras de como diferentes componentes de software devem interagir, permitindo a comunicação transparente entre sistemas distintos.

### REST (Representational State Transfer)
REST é um estilo arquitetural para desenvolvimento de sistemas distribuídos aplicados na web. Seus princípios fundamentais incluem:
- **Comunicação Cliente-Servidor sem Estado (*Stateless*):** O servidor não armazena o estado da sessão do cliente entre as requisições.
- **Uso Padrão do Protocolo HTTP:** Métodos nativos para operações de manipulação de dados.
- **Identificação de Recursos:** Recursos são mapeados e acessados através de URIs/URLs universais.
- **Representação Padronizada de Dados:** Comunicação realizada através de formatos estruturados, como JSON.

---

## 2. Protocolo HTTP e Métodos

O **HTTP** (*Hypertext Transfer Protocol*) é o protocolo base da World Wide Web que dita as regras para a troca de informações entre clientes (navegadores/aplicações) e servidores.

### Principais Conceitos
- **Modelo Cliente-Servidor:** O cliente envia uma requisição ao servidor, que processa o pedido e retorna uma resposta.
- **Stateless:** Cada requisição é independente e executada isoladamente sem dependência de chamadas anteriores.
- **Baseado em Texto:** Mensagens de requisição e resposta são legíveis por humanos.

### Métodos HTTP Principais

| Método | Finalidade | Características |
|---|---|---|
| **GET** | Recuperar informações do servidor. | **Seguro** (não altera dados) e **Idempotente** (múltiplas chamadas iguais geram o mesmo resultado). |
| **POST** | Criar novos recursos no servidor. | **Não idempotente** (chamadas repetidas criam múltiplos recursos duplicados). |
| **PUT** | Substituir integralmente um recurso existente. | **Idempotente**; atualiza todas as propriedades do objeto indicado. |
| **PATCH** | Atualizar parcialmente um recurso existente. | Modifica apenas os campos específicos enviados na requisição. |
| **DELETE** | Remover um recurso específico. | **Idempotente** (remover um recurso já excluído não gera efeito colateral novo). |

---

## 3. Como Funciona uma Requisição na Prática

1. **Navegador / Front-end:** O usuário interage com a interface (clique em botão ou carregamento de tela).
2. **Requisição HTTP:** O navegador dispara uma requisição configurada (GET, POST, PUT, DELETE) para um servidor.
3. **Servidor Express.js (Backend):** O servidor recebe o pedido, identifica a rota correspondente e executa a lógica de negócios.
4. **Banco de Dados / API Externa:** O backend consulta, grava ou atualiza informações no banco de dados ou serviços terceiros.
5. **Resposta JSON:** O servidor formata os dados obtidos e devolve uma resposta estruturada em formato JSON.
6. **Atualização da Tela:** O front-end processa os dados JSON recebidos e atualiza os componentes da interface sem recarregar a página.

---

## 4. Endpoints e Repositórios de APIs Públicas

Um **endpoint** é uma URL específica que fornece acesso a um recurso ou funcionalidade dentro de uma API, atuando como ponto final de comunicação entre o cliente e o servidor.

- **Exemplo de endpoint:** `https://github.com/awesomeapibrasil/awesomeapi-cep`
  - `GET /users` — Lista todos os usuários.
  - `POST /users` — Adiciona um novo usuário.

### APIs Públicas
Para fins de testes e estudo de integrações reais, utilizam-se catálogos de APIs públicas (como o [Free Public APIs](https://www.freepublicapis.com/)), que reúnem fontes de dados variadas para consumo direto nas aplicações.

---

## 5. Formato JSON (JavaScript Object Notation)

O **JSON** é um formato leve de troca de dados, de fácil leitura e escrita para humanos, além de rápido processamento (*parsing*) para máquinas.

### Estruturas Base
1. **Coleção de Pares Nome/Valor (Objetos):** Delimitados por chaves `{}`.
2. **Listas Ordenadas de Valores (Arrays):** Delimitados por colchetes `[]`.

```json
{
  "id": "USER-001",
  "nome": "Carlos Silva",
  "email": "carlos@exemplo.com",
  "idade": 28,
  "ativo": true,
  "endereco": {
    "cidade": "São Paulo",
    "estado": "SP"
  },
  "interesses": ["tecnologia", "esportes"]
}
```

---

## 6. Atividade Prática 01

A atividade exige a pesquisa de **10 projetos no GitHub** que realizem consumo de APIs.

### Passos da Atividade
1. Pesquisar e selecionar 10 projetos públicos no GitHub que utilizem integração com APIs.
2. Clonar e analisar os repositórios, mapeando os frameworks front-end aplicados e as APIs consumidas.
3. Criar um arquivo **Markdown (`README.md`)** contendo uma tabela explicativa detalhando os projetos encontrados, frameworks e APIs.

---

## 7. Servidor Backend e Web Services

- **Servidor Backend:** Sistema responsável por processar requisições, aplicar regras de negócio, realizar operações no banco de dados e fornecer respostas aos clientes.
- **Web Service:** Serviço disponibilizado via rede através dos protocolos HTTP/HTTPS. Sua principal função é permitir a interoperabilidade entre **sistemas heterogêneos** (diferentes linguagens, plataformas e tecnologias) de forma padronizada.

---

## 8. Framework Express.js

O **Express.js** é um framework minimalista, flexível e altamente rápido desenvolvido para Node.js, focado em simplificar a criação de servidores web e APIs REST.

### Node.js Puro vs. Express.js

| Recurso | Node.js Puro (`http` module) | Express.js |
|---|---|---|
| **Complexidade de Código** | Exige tratamento manual extenso de requisições e rotas. | Sintaxe limpa, declarativa e simplificada. |
| **Roteamento** | Estruturas condicionais verbosas (`if/else` no `req.url`). | Métodos nativos diretos (`app.get()`, `app.post()`). |
| **Middlewares** | Difícil implementação e encadeamento manual. | Suporte nativo via `app.use()`. |

#### Comparativo de Código:

**Node.js Puro:**
```javascript
const http = require('http');

const server = http.createServer((req, res) => {
  if (req.url === '/') {
    res.end('Olá, mundo!');
  } else {
    res.end('Rota não encontrada!');
  }
});

server.listen(3000);
```

**Express.js:**
```javascript
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Olá, mundo!');
});

app.listen(3000);
```

### Casos de Uso
- **Ideal para:** APIs REST, backends para SPAs, microsserviços, middleware para autenticação e rotas web gerais.
- **Evitar em:** Processamentos matemáticos intensivos (onde é recomendado *Worker Threads*) ou conexões com foco puramente em tempo real (onde deve-se optar por WebSockets nativos).

---

## 9. Passo a Passo: Criando uma API REST com Express

### Passo 1: Inicializar o Projeto Node
Crie o diretório do projeto, abra no VS Code e inicialize o Node:
```bash
mkdir minha-api-express
cd minha-api-express
npm init -y
```

### Passo 2: Instalar as Dependências
Instale o Express e o CORS para gerenciamento de requisições entre domínios:
```bash
npm install express cors
```

> **CORS (*Cross-Origin Resource Sharing*):** Mecanismo de segurança dos navegadores que controla a permissão de requisições vindas de domínios diferentes da origem da API.

### Passo 3: Criar o Código da API (`api.js`)
Crie o arquivo `api.js` configurando as variáveis de ambiente e uma rota GET de teste:

```javascript
import express from 'express';
import cors from 'cors';

const app = express();

// Habilita o CORS para requisições externas
app.use(cors());

// Rota para consulta de status e data/hora
app.get('/', (req, res) => {
  res.json({
    date: new Date().toLocaleString('pt-BR'),
    status: 'API no Render funcionando!'
  });
});

// Porta dinâmica ajustada para ambientes de nuvem (Render) ou porta 3000 local
const PORT = process.env.PORT || 3000;

app.listen(PORT, () => {
  console.log(`Servidor rodando na porta ${PORT}`);
});
```

### Passo 4: Executar o Servidor Localmente
```bash
node api.js
```

---

## 10. Plataforma Render para Hospedagem em Nuvem

O **Render** é uma plataforma de nuvem moderna para hospedagem de aplicações, APIs e bancos de dados.

- **Vantagens:** Integração nativa com GitHub, suporte ao Node.js, deploy contínuo (*CI/CD*) automatizado, plano gratuito e certificado SSL (HTTPS) incluído nativamente.

### Publicando a API no Render
1. Suba o código da sua API para um **repositório público ou privado no GitHub**.
2. Acesse o painel [dashboard.render.com](https://dashboard.render.com) e crie uma conta.
3. Clique no botão **New** e selecione a opção **Web Service**.
4. Conecte sua conta do GitHub e selecione o repositório da API.
5. Defina as configurações de execução:
   - **Build Command:** `npm install` (ou `node`)
   - **Start Command:** `node api.js`
6. Confirme o deploy. Sua API estará online em uma URL pública no padrão `seu-projeto.onrender.com`.

---

## 11. Atividade Prática 02

A segunda atividade foca no ciclo completo de desenvolvimento: **Backend (API) + Nuvem + Front-end (Consumo)**.

### Requisitos da Atividade
1. **API com Express:** Criar uma API em Express contendo uma rota que retorne a data e hora atual do servidor.
2. **Deploy da API no Render:** Fazer o deploy do projeto no Render integrado ao repositório do GitHub.
3. **Aplicação Front-end:** Desenvolver uma interface gráfica front-end que consuma o endpoint da API no Render e mostre os dados formatados na tela.
4. **Separação em Repositórios:** Utilizar repositórios **separados** no GitHub para a API e para a aplicação Front-end.
5. **Documentação de Entrega:** Elaborar um documento contendo:
   - Prints do código-fonte e da aplicação rodando.
   - Prints dos painéis de controle do **Render** (API) e **Vercel** (Front-end).
   - Links diretos para os dois repositórios no GitHub.

---

## 📝 Resumo do Fluxo

```
Conceito de API REST & HTTP
       │
       ▼
Construção do Backend em Express.js (Com CORS)
       │
       ▼
Commit e Push do código no GitHub
       │
       ▼
Deploy automatizado do Web Service no Render
       │
       ▼
Desenvolvimento do Front-end consumindo a API remota
```

---

## 📚 Referências Bibliográficas

- EIS, Diego. **Guia Front-end: o caminho das pedras para ser um dev front-end.** São Paulo: Casa do Código, 2015.
- GONÇALVES, Edson. **Desenvolvendo aplicações Web com JSP, Servlets, JavaServer Faces, Hibernate, EJB 3 Persistence e Ajax.** Rio de Janeiro: Ciência Moderna, c2007.
- HARTCOPP, Patrícia Ferreira. **Métrica Web.** São Paulo: Contentus, 2020.
- MACHADO, Kheronn Khennedy. **Angular 11 e Firebase: construindo uma aplicação integrada com a plataforma do Google.** São Paulo: Casa do Código, 2021.
- NIEDERAUER, Juliano. **Desenvolvendo Websites com PHP: aprenda a criar Websites dinâmicos e interativos com PHP e banco de dados.** 3. ed. São Paulo: Novatec, 2017.
- PREECE, J.; ROGERS, Y.; SHARP, H. **Design de Interação: além da interação Homem-Computador.** 3. ed. Porto Alegre: Bookman, 2013.
- SOUSA, Roque Fernando Marcos. **Canvas HTML 5: composição gráfica e interatividade na Web.** Rio de Janeiro: Brasport, 2014.
- SOUZA, Natan. **Bootstrap 4: conheça a biblioteca front-end mais utilizada no mundo.** São Paulo: Casa do Código, 2018.