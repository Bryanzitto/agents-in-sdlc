---
title: "Exercício 5 - Monitoramento e gerenciamento de agentes"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

O Copilot Chat mostra chamadas de ferramenta e edições em tempo real. Você pode revisar diffs, aceitar ou desfazer alterações e conduzir a sessão.

Neste exercício, você monitorará o trabalho do agente de acessibilidade, revisará as edições e orientará a sessão para adicionar um alternador de modo claro.

## Cenário

Enquanto o agente implementa o modo de alto contraste, a equipe solicita também um alternador de modo claro.

## Monitore o progresso

1. Retorne ao Copilot Chat.
2. Observe leituras, edições e comandos.
3. Selecione **Keep** para aceitar ou **Undo** para desfazer.
4. Abra **Files changed** para revisar o conjunto de trabalho.

5. Aguarde a conclusão da implementação do modo de alto contraste e leia o resumo final do agente.

> [!NOTE]
> Aprove somente comandos que você considera seguros.

## Adicione o modo claro

Envie:

```plaintext
Nice work! Now add a light-mode toggle alongside the high-contrast toggle. Light mode should follow the same pattern — persist via local storage and be accessible from the same area of the UI. The user should be able to enable high-contrast and light mode independently.
```

Revise cada diff. Use **Stop** e envie uma mensagem de esclarecimento se necessário.

O agente mantém o contexto da conversa anterior, incluindo os componentes alterados, a abordagem de estilos e o padrão usado no armazenamento local.

> [!TIP]
> Conduzir uma sessão em andamento é mais rápido do que começar novamente.

## Revise o conjunto de trabalho

Abra **Source Control**, confirme atributos ARIA, navegação por teclado, HTML semântico e persistência no armazenamento local. Faça commit quando estiver satisfeito.

Antes do commit, revise a lista completa de arquivos alterados e confirme as alterações nos componentes Astro, estilos e testes. Você publicará o trabalho na próxima lição.

## Recursos

- [Copilot Chat no VS Code][copilot-chat-vscode]
- [Usar o modo Agente][agent-mode]

## Resumo e próximos passos

Você monitorou e conduziu uma sessão do modo Agente. Na [próxima lição][next-lesson], publique seu trabalho como pull request.

[previous-lesson]: ../4-custom-agents/
[next-lesson]: ../6-iterating/
[copilot-chat-vscode]: https://code.visualstudio.com/docs/copilot/chat/copilot-chat
[agent-mode]: https://code.visualstudio.com/docs/copilot/chat/chat-agent-mode
