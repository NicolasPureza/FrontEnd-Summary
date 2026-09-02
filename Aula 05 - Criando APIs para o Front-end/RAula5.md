# Aula 05 — Criando APIs para o Front-end

**Disciplina:** Frameworks Front-end  
**Foco:** Construção de API REST com Express.js, manipulação de JSON (CRUD completo), deploy no Render/Vercel, testes/documentação com Postman e reflexões sobre backend.  
**Instituição:** SENAI  
**Professor:** Prof. Me. Deivison S. Takatu (`deivison.takatu@edu.senai.br`)

---

## 📌 Sumário

- Revisão de Conceitos (APIs, HTTP, JSON e Endpoints)
- Atividade 01 (Atualização e Envio do Repositório)
- Evolução do Projeto Express: Aplicação de Notas (CRUD)
- Definição das Rotas da API REST (`/api/notes`)
- Passo a Passo: Construindo o Backend em Express com `data.json`
- Implementação do Código (`server.js` e `data.json`)
- Integração e Deploy (Render + React + Vercel)
- Questões para Reflexão (Segurança e Persistência em JSON)
- Documentação e Testes de APIs com Postman
- Atividade Prática 02 (Desenvolvimento, Deploy e Coleção no Postman)
- Referências Bibliográficas

---

## 1. Revisão de Conceitos Base

A aula inicia com uma breve recapitulação dos pilares para construção e consumo de APIs web:

### Métodos HTTP Nativos
- **GET:** Recupera informações do servidor. É seguro e idempotente.
- **POST:** Cria novos recursos no servidor. Não é idempotente (chamadas repetidas geram múltiplos registros).
- **PUT / PATCH:** Atualizam informações no servidor. O `PUT` substitui o recurso por completo, enquanto o `PATCH` altera apenas os campos especificados.
- **DELETE:** Remove um recurso específico. É idempotente.

### Endpoints e Formato JSON
- **Endpoint:** URL específica que funciona como ponto de comunicação para acessar determinados recursos da aplicação.
- **JSON (*JavaScript Object Notation*):** Formato leve e legível para estruturação de dados, baseado em objetos (pares chave/valor `{}`) e listas ordenadas (`arrays []`).

---

## 2. Atividade Prática 01

Envio e sincronização do repositório contendo as bases desenvolvidas na aula anterior.

### Instruções
1. Atualizar o repositório da disciplina no GitHub com todos os arquivos das práticas anteriores.
2. Garantir que a versão esteja completa e acessível.
3. Submeter o link do repositório por meio do formulário oficial (`https://forms.gle/L7iL7jx1RzyiXBnk9`).

---

## 3. Evolução do Projeto Express: Aplicação de Notas (CRUD)

Em substituição à API simples que apenas retornava a data e hora do servidor, o projeto é expandido para uma **API RESTful de gerenciamento de notas**, implementando as operações fundamentais de **CRUD** (*Create, Read, Update, Delete*).

- **Estratégia de Persistência:** Uso do sistema de arquivos com um arquivo local `data.json` para persistir dados sem a necessidade de banco de dados relacional ou NoSQL em um primeiro momento.
- **Exemplo de Aplicação Frontend:** `https://notas-app-react.vercel.app/`

---

## 4. Definição das Rotas da API RESTful

A API expõe as seguintes rotas sob o prefixo `/api/notes`:

| Operação | Método | Rota | Descrição |
|---|---|---|---|
| **Listar Tudo** | `GET` | `/api/notes` | Retorna o array completo com todas as notas do `data.json`. |
| **Obter por ID** | `GET` | `/api/notes/:id` | Retorna uma única nota cujo `id` corresponda ao parâmetro enviado. |
| **Criar Nota** | `POST` | `/api/notes` | Cria uma nova nota. Exige `titulo` e `texto` no corpo. Gera `id` via `Date.now().toString()`. |
| **Editar Nota** | `PUT` | `/api/notes/:id` | Atualiza o `titulo` e `texto` da nota com o `id` correspondente. |
| **Excluir Nota** | `DELETE` | `/api/notes/:id` | Remove a nota correspondente do arquivo `data.json`. |

---

## 5. Passo a Passo: Construindo a API no Backend

### Passo 1: Inicialização do Projeto
Crie o diretório do projeto e abra no editor:
```bash
mkdir projeto-notas
cd projeto-notas