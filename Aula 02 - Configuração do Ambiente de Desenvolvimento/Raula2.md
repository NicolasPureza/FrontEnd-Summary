# Resumo: Aula 02 - Configuração do Ambiente de Desenvolvimento

## Dados da Disciplina
* **Curso / Instituição:** SENAI[cite: 4]
* **Disciplina:** Frameworks Front-end[cite: 4]
* **Professor:** Prof. Me. Deivison S. Takatu (deivison.takatu@edu.senai.br)[cite: 4]

---

## 📑 Visão Geral do Conteúdo

### Versionamento e Versionamento Semântico (SemVer)
* **Versionamento vs. Backup:** O versionamento registra o histórico detalhado (quem, quando e por quê), permite colaboração simultânea e reversão granular[cite: 4]. O backup é apenas uma cópia estática pontual sem rastreabilidade de autoria[cite: 4].
* **Estrutura SemVer (`MAJOR.MINOR.PATCH`):**
  * **MAJOR:** Alterações incompatíveis ou que quebram o código anterior (ex: `2.0.0`)[cite: 4].
  * **MINOR:** Adição de novas funcionalidades com compatibilidade garantida (ex: `1.1.0`)[cite: 4].
  * **PATCH:** Correções de bugs sem afetar a API ou funcionalidades existentes (ex: `1.0.1`)[cite: 4].

### Ferramentas de Desenvolvimento e Controle de Versão
* **Git:** Sistema distribuído de controle de versão[cite: 4]. Permite criar **Tags** (marcadores para lançamentos de versões/releases) e utilizar **Branches** para isolar novas funcionalidades[cite: 4].
* **Boas Práticas no Git:** Fazer commits pequenos e frequentes, escrever mensagens claras e manter a branch principal sempre estável[cite: 4].
* **Node.js & NPM:** O Node.js executa JavaScript fora do navegador (ambiente servidor)[cite: 4]. O NPM gerencia bibliotecas/dependências e automatiza scripts de projeto através do arquivo `package.json`[cite: 4].

### Ecossistema React e Deploy
* **Inicialização com React:** Utilização do comando `npx create-react-app <nome>` para estruturar a aplicação com Webpack, Babel e servidor de desenvolvimento embutido[cite: 4].
* **Estrutura do Projeto:** Entendimento dos papéis do `index.js` (ponto de entrada no DOM), `App.js` (componente principal) e das pastas `public/`, `src/` e `node_modules/`[cite: 4].
* **Deploy na Vercel:** Publicação automatizada conectando o repositório do GitHub à plataforma Vercel, permitindo atualizações instantâneas via `git push` e distribuição global por CDN[cite: 4].

---

## 🛠️ Atividades da Aula

1. **Configuração e Criação:**
   * Instalação do Git, VS Code e Node.js[cite: 4].
   * Configuração das credenciais globais do Git (`user.name` e `user.email`)[cite: 4].
   * Criação de um projeto React inicial utilizando `npx create-react-app`[cite: 4].

2. **Publicação Prática:**
   * Versionamento do código local e publicação do repositório no GitHub[cite: 4].
   * Conexão do repositório com a Vercel para gerar o deploy automatizado da aplicação com uma URL pública acessível[cite: 4].