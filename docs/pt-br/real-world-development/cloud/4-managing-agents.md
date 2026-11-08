---
title: "Exercício 4 - Monitoramento e gerenciamento de agentes"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

O agente na nuvem trabalha de forma assíncrona, mas ainda é importante monitorar as tarefas na [página de agentes][agents-page].

Você pode revisar as operações executadas e conduzir uma sessão em andamento para orientar o agente.

## Cenário

Enquanto o agente implementa o modo de alto contraste, a equipe decide adicionar também um modo claro.

## Revise as tarefas

1. Navegue até a [página de agentes do Copilot](https://github.com/copilot/agents).
2. Revise a lista de tarefas e selecione uma em execução.
3. Observe o checkout do código, a criação do ambiente, a configuração de servidores MCP e as demais etapas.

> [!NOTE]
> As etapas exatas variam conforme o estado do trabalho e a abordagem do Copilot.

## Conduza o agente

Envie:

```plaintext
While we are working on a high contrast mode, let's also add a light mode. There should be a switch for this mode as well where users can select their desired display mode.
```

Pressione <kbd>Enter</kbd> e observe como o Copilot incorpora a solicitação.

Você também pode selecionar a sessão relacionada ao modo de alto contraste, aguardar o início do trabalho e enviar a mensagem no diálogo **Steer active session while Copilot is working**.

## Resumo e próximos passos

Você explorou a página de agentes e conduziu uma sessão. Agora, [itere nos pull requests do Copilot][next-lesson].

[previous-lesson]: ../3-custom-agents/
[next-lesson]: ../5-iterating/
[agents-page]: https://github.blog/changelog/2025-07-03-agents-page-for-copilot-coding-agent-in-public-preview
[custom-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
