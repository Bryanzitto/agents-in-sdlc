---
title: "Exercício 2 - Adicionando funcionalidades com o modo Agente do Copilot"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

O modo Agente explora o projeto, atualiza arquivos, executa testes e corrige problemas. Neste exercício, você implementará filtragem por categoria e editora.

> [!NOTE]
> O modo Agente executa tarefas no IDE e permite ciclos rápidos de feedback. O agente na nuvem trabalha de forma assíncrona no GitHub por meio de issues e pull requests.

## Cenário

A lista de jogos cresceu. Você já criou um helper de editoras e agora concluirá a camada de dados, a interface e os testes.

## Execute o site

O Tailspin Toys é um aplicativo Astro que renderiza páginas estáticas a partir de um banco SQLite local. Helpers reutilizáveis ficam em `src/lib/`, e a interatividade usa scripts Astro pequenos com APIs DOM padrão.

```bash
git checkout main
git pull
git checkout -b filtering-vscode
npm run dev
```

Abra `http://localhost:4321` e explore o site.

A página inicial lista jogos; a página de detalhes mostra título, descrição, editora e categoria.

## Explore o backlog

Selecione **Agent**, escolha **Claude Sonnet 4.5** e envie:

```plaintext
Please show me the backlog of items from my GitHub repository. Help me prioritize them based on those which will be most useful to the user.
```

Selecione **Continue** para permitir a leitura das issues e revise a lista priorizada.

## Revise as instruções

Abra `.github/instructions/ui.instructions.md` e observe a arquitetura, testabilidade, acessibilidade e links para Astro, Tailwind CSS e Drizzle.

## Implemente a filtragem

Selecione **Add Context**, **Instructions** e `ui`, mantenha **Agent** e envie:

```plaintext
Please update the site to include filtering by publisher and category based on the requirements from the related GitHub issue in the backlog. A publishers helper already exists from the previous exercise, so preserve and refine that work as needed while completing the remaining data-layer, UI, and tests. Ensure all tests are passing before completion. The server is already running, so you do not need to start it up.
```

Revise os arquivos, execute os testes e selecione **Keep** quando estiver satisfeito.

Selecione **Continue** quando o Copilot solicitar autorização para executar os testes. O processo pode falhar e tentar novamente enquanto o agente corrige os problemas; revise sempre o código gerado antes de mantê-lo.

### Exploração adicional — implemente paginação

Como a lista de jogos cresce, peça ao Copilot para implementar paginação. Considere o tamanho da página, as instruções existentes e a necessidade de iterar no prompt.

## Resumo e próximos passos

Você usou o modo Agente para coordenar alterações na interface e na camada de dados. Agora [teste o recurso com o servidor MCP do Playwright][next-lesson].

[previous-lesson]: ../1-custom-instructions/
[next-lesson]: ../3-mcp/
