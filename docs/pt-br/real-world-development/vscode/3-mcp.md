---
title: "Exercício 3 - Testando seu recurso com o servidor MCP do Playwright"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[← Lição anterior: Modo Agente][previous-lesson] · [Próxima lição: Agentes personalizados →][next-lesson]

Você acabou de criar a filtragem. Conecte o **servidor MCP do Playwright** para que o Copilot controle um navegador real.

Nesta lição, você aprenderá o que é MCP, adicionará o servidor do Playwright, testará a funcionalidade no navegador e abrirá um pull request.

## O que é MCP?

O [Model Context Protocol (MCP)](https://github.blog/ai-and-ml/llms/what-the-heck-is-mcp-and-why-is-everyone-talking-about-it/) permite que agentes de IA se comuniquem com ferramentas e serviços externos.

Servidores MCP funcionam como pontes entre o agente e ferramentas externas. Por exemplo, o servidor do GitHub fornece APIs para repositórios e issues, enquanto o servidor do Playwright fornece automação de navegador.

![Diagrama mostrando o modo Agente interagindo com contexto, LLM e ferramentas, incluindo ferramentas fornecidas por servidores MCP e extensões do VS Code](../../../_images/ex1-mcp-diagram.png)

> [!CAUTION]
> Trate servidores MCP como qualquer outra dependência. Revise o código-fonte, verifique o publicador e conceda acesso somente a servidores confiáveis.

## Revise a configuração do MCP

Em `.vscode/mcp.json`, confirme que o servidor remoto `github` já está configurado e adicione o servidor local `playwright`:

```json
{
  "servers": {
    "github": {
      "type": "http",
      "url": "https://api.githubcopilot.com/mcp/"
    },
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest", "--headless"]
    }
  }
}
```

Salve e confie no servidor quando solicitado.

O VS Code inicia servidores MCP sob demanda. Se aparecer **Start** acima da entrada `playwright`, selecione-o para iniciar o servidor e confirme que você confia na configuração.

## Teste a filtragem

Com o aplicativo em `http://localhost:4321`, peça ao Copilot:

```text
Using the Playwright MCP server, open a browser to the running app at http://localhost:4321 and verify the new game filtering feature:

1. Go to the games page and note how many games are listed.
2. Apply a category filter and confirm the list updates to only show games in that category.
3. Clear it, then apply a publisher filter and confirm the list updates to that publisher.
4. Combine a category and a publisher filter and confirm the results respect both.

Report what you observe at each step, and call out anything that does not behave as expected.
```

Peça um relatório sobre filtros de categoria, editora e a combinação dos dois.

Use um prompt que peça para abrir a página de jogos, aplicar cada filtro, combinar os filtros e relatar qualquer comportamento inesperado.

## Publique a branch e crie um pull request

Revise as alterações no painel **Source Control**, faça commit e selecione **Publish**. Depois, peça ao Copilot:

```plaintext
Find the issue in the repo related to filtering by category and publisher. Create a new pull request for the current branch, and associate it with the correct issue.
```

Não faça merge ainda.

Na primeira vez que o Copilot usar uma ferramenta do GitHub, autentique-se quando solicitado. Revise o pull request criado e não faça merge ainda.

## Recursos

- [O que é MCP e por que todos estão falando sobre isso?][mcp-blog-post]
- [Servidor MCP do Microsoft Playwright][playwright-mcp-server]
- [Servidor MCP do GitHub][github-mcp-server]
- [Registro de servidores MCP][mcp-registry]
- [MCP no VS Code][vscode-mcp-config]

## Resumo e próximos passos

Você aprendeu sobre MCP, adicionou o Playwright, testou a filtragem e abriu um pull request. Em seguida, [crie um agente personalizado][next-lesson].

[previous-lesson]: ../2-agent-mode/
[next-lesson]: ../4-custom-agents/
[playwright-mcp-server]: https://github.com/microsoft/playwright-mcp
[mcp-blog-post]: https://github.blog/ai-and-ml/llms/what-the-heck-is-mcp-and-why-is-everyone-talking-about-it/
[github-mcp-server]: https://github.com/github/github-mcp-server
[mcp-registry]: https://github.com/mcp
[remote-github-mcp-server]: https://github.blog/changelog/2025-06-12-remote-github-mcp-server-is-now-available-in-public-preview/
[vscode-mcp-config]: https://code.visualstudio.com/docs/agents/reference/mcp-configuration
