---
title: "Exercício 5: Iterando no trabalho do GitHub Copilot"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

## Revisando o trabalho

Ao longo do laboratório, você pediu ao Copilot para adicionar documentação, criar jogos relacionados e implementar os modos de alto contraste e claro. Revise as alterações e forneça feedback quando necessário.

## Segurança e o agente na nuvem

- O Copilot tem acesso de escrita apenas à branch de trabalho.
- O agente executa em um ambiente efêmero separado no GitHub Actions.
- Workflows exigem aprovação humana.
- O acesso a recursos externos é limitado por padrão.

## Revise a documentação gerada

1. Abra o pull request criado para a documentação.
2. Selecione **Files changed** e procure comentários TSDoc, convenções TypeScript e cabeçalhos de arquivo.
3. Na guia **Conversation**, aprove os workflows quando necessário e aguarde a conclusão das verificações.
4. Adicione um comentário mencionando **@copilot** para solicitar alterações e selecione **View Session** para acompanhar a nova sessão.

## Revise a funcionalidade de jogos relacionados

Abra o pull request com título semelhante a `Show related games on the game details page`, revise os arquivos alterados, aprove os workflows quando necessário e confirme que os testes passam. Opcionalmente, alterne para a branch do Copilot no Codespace para testar manualmente:

## Revise os pull requests

Abra cada pull request, selecione **Files changed**, revise comentários TSDoc, convenções TypeScript, cabeçalhos, testes e acessibilidade. Aprove os workflows quando necessário.

Para solicitar alterações, adicione um comentário mencionando **@copilot** e selecione **View Session**.

## Teste uma branch opcionalmente

```bash
git fetch origin
git checkout <branch-name>
```

## Revise os recursos de acessibilidade

Abra o pull request do modo de alto contraste e verifique os alternadores, o armazenamento local, os estilos de alto contraste e claro, os atributos ARIA e a navegação por teclado. Aprove os workflows e teste as alterações no navegador quando possível.

## Exercício opcional — continue delegando

- Crie um formulário de interesse na página de detalhes.
- Implemente paginação.
- Adicione validação de entrada e tratamento de erros.

## Resumo

Você concluiu o laboratório: revisou instruções, atribuiu issues, usou um agente personalizado e iterou nos pull requests.

## Recursos

- [GitHub Copilot][github-copilot]
- [Sobre agentes do Copilot][copilot-agents]
- [Atribuir issues ao Copilot][assign-issue]
- [Configurar o firewall do agente][agent-firewall]

[previous-lesson]: ../4-managing-agents/
[github-copilot]: https://github.com/features/copilot
[copilot-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[assign-issue]: https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/start-copilot-sessions
[agent-firewall]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-firewall
