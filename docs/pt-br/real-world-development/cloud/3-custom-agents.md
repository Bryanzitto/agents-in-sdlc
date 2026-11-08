---
title: "Exercício 3 - Agentes personalizados"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

## O que são agentes personalizados?

[Agentes personalizados][custom-agents-concept] são assistentes especializados definidos por arquivos Markdown em `.github/agents`. Eles podem aplicar práticas de acessibilidade, como conformidade com [WCAG][wcag], segurança e testes.

Eles também podem ser definidos globalmente em `~/.copilot/agents`. Cada arquivo deve conter frontmatter YAML com pelo menos `name` e `description`, seguido do prompt que define o comportamento do agente.

### Agentes personalizados e habilidades de agente

Agentes personalizados e [habilidades de agente][agent-skills-concept] têm alguma sobreposição. A distinção mais simples é: o **agente personalizado** executa o trabalho, enquanto as **habilidades** são ferramentas que ele pode orquestrar.

> [!NOTE]
> Não existe uma única forma correta de criar um agente personalizado. Teste e itere para encontrar a abordagem adequada ao seu ambiente.

## Cenário

A Tailspin Toys quer um modo de alto contraste. Você usará o agente de acessibilidade para gerar a funcionalidade.

## Revise o agente de acessibilidade

1. Abra `.github/agents/accessibility.md`.
2. Observe `name` e `description` no frontmatter.
3. Revise responsabilidades, práticas recomendadas, exemplos e erros comuns.

> [!CAUTION]
> O frontmatter com `name` e `description` é obrigatório.

## Crie e atribua uma issue

1. Navegue até o repositório e selecione **Issues**, **New issue** e **Blank issue**.
2. Defina o título como `Add high contrast mode to website`.
3. Descreva um modo de alto contraste com um alternador cuja configuração seja persistida no armazenamento local do navegador.
4. Selecione **Create**, **Assign to Copilot**, **Accessibility agent** e **Assign**.

## Resumo e próximos passos

Você explorou agentes personalizados. Em seguida, [monitore a sessão do agente][next-lesson].

[previous-lesson]: ../2-cloud-agent/
[next-lesson]: ../4-managing-agents/
[custom-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
[custom-agents-concept]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
[agent-skills-concept]: https://docs.github.com/copilot/concepts/agents/about-agent-skills
[wcag]: https://www.w3.org/WAI/standards-guidelines/wcag/
