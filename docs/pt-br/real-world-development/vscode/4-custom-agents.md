---
title: "Exercício 4 - Agentes personalizados"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

## O que são agentes personalizados?

[Agentes personalizados][custom-agents-concept] são assistentes especializados definidos por arquivos Markdown em `.github/agents`.

Eles podem codificar práticas de acessibilidade, padrões de segurança e convenções de testes. Cada arquivo pode conter frontmatter YAML com `name` e `description`, seguido das instruções do agente.

### Agentes personalizados e habilidades

Agentes personalizados realizam o trabalho; [habilidades de agente][agent-skills-concept] são ferramentas que podem ser orquestradas durante esse trabalho.

## Cenário

A Tailspin Toys quer um modo de alto contraste para melhorar a legibilidade. Você revisará e usará o agente de acessibilidade.

## Revise o agente

```bash
git checkout main
git pull
git checkout -b accessibility-vscode
```

Abra `.github/agents/accessibility.md` e revise `name`, `description`, responsabilidades, práticas e exemplos.

> [!CAUTION]
> O frontmatter com `name` e `description` é obrigatório.

## Use o agente no Copilot Chat

1. Selecione **Agent** no seletor de agentes do Copilot Chat.
2. Escolha **Accessibility agent**.
3. Envie:

```plaintext
Add a high-contrast mode to the site. There should be a toggle for high contrast which the user can set, and the setting should persist across page reloads using local storage on the browser.
```

Revise cada diff e observe os arquivos alterados.

O agente explorará o código, proporá alterações e atualizará os arquivos Astro, CSS e testes relevantes. Revise cada diff conforme ele aparecer.

## Recursos

- [Sobre agentes personalizados][custom-agents]
- [Criar agentes personalizados no IDE][creating-custom-agents-ide]
- [Agentes personalizados no VS Code][custom-agents-vscode]
- [Configuração de agentes personalizados][custom-agents-config]
- [Agentes personalizados no awesome-copilot][awesome-copilot-agents]

## Resumo e próximos passos

Você usou um agente personalizado no modo Agente. Em seguida, [monitore o trabalho do agente][next-lesson].

[previous-lesson]: ../3-mcp/
[next-lesson]: ../5-managing-agents/
[custom-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
[custom-agents-concept]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
[agent-skills-concept]: https://docs.github.com/copilot/concepts/agents/about-agent-skills
[creating-custom-agents-ide]: https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/create-custom-agents-in-your-ide
[custom-agents-vscode]: https://code.visualstudio.com/docs/copilot/customization/custom-agents
[custom-agents-config]: https://docs.github.com/copilot/reference/custom-agents-configuration
[awesome-copilot-agents]: https://github.com/github/awesome-copilot/tree/main/agents
