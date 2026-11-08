---
slug: pt-br/real-world-development/cloud
title: "Agente na nuvem do GitHub Copilot"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

O **[agente na nuvem do GitHub Copilot](https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent)** permite que o GitHub Copilot trabalhe de forma assíncrona na nuvem. Você atribui o trabalho no GitHub, e o agente o executa em segundo plano — explorando o repositório, fazendo alterações e abrindo um pull request — enquanto você pode fazer outras coisas.

Nestes exercícios, você adicionará instruções personalizadas que o agente seguirá, atribuirá uma issue e deixará que ele implemente o trabalho. Você revisará e usará agentes personalizados, monitorará sessões no painel de agentes e finalizará revisando os pull requests e iterando nos resultados.

## Exercícios

| Exercício | Tópico | Descrição |
|----------|-------|-------------|
| [0. Pré-requisitos][ex0] | Configuração | Crie seu repositório e codespace |
| [1. Instruções personalizadas][ex1] | Contexto | Adicione as instruções que o agente seguirá |
| [2. Agente na nuvem][ex2] | Agente assíncrono | Atribua issues ao agente na nuvem |
| [3. Agentes personalizados][ex3] | Agentes especializados | Revise e use agentes personalizados |
| [4. Gerenciamento de agentes][ex4] | Monitoramento | Monitore e conduza sessões |
| [5. Iteração][ex5] | Revisão | Revise PRs e itere no trabalho do Copilot |

## Pré-requisitos

Antes de participar deste workshop, verifique se você tem:

- [ ] Uma conta do GitHub com um plano **Copilot Student, Pro, Pro+, Business ou Enterprise** ativo
- [ ] O agente na nuvem habilitado para sua conta ou organização

> [!TIP]
> Não tem um plano pago? Estudantes verificados podem obter o GitHub Copilot gratuitamente pelo [GitHub Education][callout-student-plan-education]. O plano **Copilot Student** inclui o agente, MCP, revisão de código e os recursos do Copilot CLI usados neste workshop.

[callout-student-plan-education]: https://github.com/education/students

> [!NOTE]
> O agente na nuvem está disponível no **Copilot Student, Pro, Pro+, Business e Enterprise**. No Copilot Business ou Enterprise, um administrador precisa habilitá-lo.

> [!NOTE]
> O MCP não é abordado neste laboratório. Para explorar servidores MCP, consulte o [laboratório do CLI](../cli/) ou o [laboratório do VS Code](../vscode/).

## Comece agora

**[Comece pelo Exercício 0: Pré-requisitos →][ex0]**

[ex0]: 0-prerequisites/
[ex1]: 1-custom-instructions/
[ex2]: 2-cloud-agent/
[ex3]: 3-custom-agents/
[ex4]: 4-managing-agents/
[ex5]: 5-iterating/
