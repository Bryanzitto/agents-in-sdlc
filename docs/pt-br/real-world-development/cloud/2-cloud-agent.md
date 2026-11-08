---
title: "Exercício 2 - Agente na nuvem do GitHub Copilot"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

O agente na nuvem do GitHub Copilot executa tarefas em segundo plano, atualiza código e abre pull requests para revisão humana.

Neste exercício, você explorará a personalização do ambiente, operações seguras, issues bem delimitadas e a atribuição de issues ao Copilot.

Você verá como o agente pode lidar com dívida técnica e implementar funcionalidades enquanto você trabalha em outras tarefas.

## Cenários

A Tailspin Toys quer adicionar comentários TSDoc às funções exportadas e mostrar jogos relacionados na página de detalhes. Essas tarefas são bons candidatos para execução assíncrona e podem ser revisadas depois em pull requests.

## Introdução ao agente na nuvem

O [agente na nuvem do GitHub Copilot](https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent) trabalha em segundo plano como um desenvolvedor humano. Você pode [atribuir uma issue ao Copilot](https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/start-copilot-sessions); ele cria um pull request de rascunho, configura o ambiente e inicia a tarefa.

## Instruções bem delimitadas

Delimite as tarefas cuidadosamente e trate o Copilot como um parceiro de programação: trabalhe em etapas, aprenda, experimente e adapte o processo.

## Instruções personalizadas neste repositório

Nas lições anteriores, você conheceu os arquivos de instruções personalizados. Antes de atribuir trabalho ao agente, leia `.github/copilot-instructions.md` e `.github/instructions/unit-tests.instructions.md` para observar as convenções de TypeScript, TSDoc e testes que orientarão o resultado.

## Configurando o ambiente

O agente usa [GitHub Actions][github-actions]. O workflow `.github/workflows/copilot-setup-steps.yml` prepara Node.js, dependências, navegadores do Playwright e o banco SQLite.

```yaml
name: "Copilot Setup Steps"
on: workflow_dispatch

env:
  ASTRO_TELEMETRY_DISABLED: "1"

jobs:
  copilot-setup-steps:
    runs-on: ubuntu-latest
    permissions:
      contents: read
    steps:
      - name: Checkout code
        uses: actions/checkout@v5
      - name: Set up Node.js
        uses: actions/setup-node@v6
        with:
          node-version: "lts/*"
          cache: "npm"
          cache-dependency-path: "./package-lock.json"
      - name: Install JavaScript dependencies
        run: npm ci
      - name: Install Playwright browsers
        run: npx playwright install --with-deps chromium
      - name: Set up the database
        run: npm run db:setup
```

O job `copilot-setup-steps` é executado antes do trabalho do Copilot. `workflow_dispatch` permite testá-lo manualmente na guia **Actions**.

O workflow também instala as dependências do projeto, os navegadores do Playwright e configura o banco de dados SQLite local. O agente trabalha em um ambiente efêmero separado, e os workflows exigem aprovação humana antes de serem executados.

## Adicionando documentação

1. No repositório do github.com, abra a guia **Issues**, selecione **New issue** e depois **Blank issue**.
2. Defina o título como `Code lacks documentation`.
3. Na descrição, informe que funções e métodos devem receber comentários TSDoc quando eles esclarecem o comportamento.
4. Selecione **Create** e depois **Assign to Copilot**.
5. Abra o pull request gerado, revise a lista de tarefas e selecione **View session** para acompanhar o trabalho.

## Jogos relacionados

1. Crie outra issue com o título `Show related games on the game details page`.
2. Peça um helper em `src/lib/` que retorne outros jogos da mesma categoria, uma seção **Related games**, tratamento para ausência de resultados, testes unitários e execução bem-sucedida de todos os testes.
3. Atribua a issue ao Copilot e revise o pull request quando ele estiver pronto.

## Resumo e próximos passos

Você aprendeu a usar o agente para tratar dívida técnica e criar funcionalidades. Agora, crie e use agentes personalizados.

## Recursos

- [Sobre o agente na nuvem][copilot-agents]
- [Atribuir issues ao Copilot][assign-issue]
- [Práticas recomendadas do workflow][cloud-agent-best-practices]

[previous-lesson]: ../1-custom-instructions/
[next-lesson]: ../3-custom-agents/
[assign-issue]: https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/start-copilot-sessions
[copilot-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[cloud-agent-best-practices]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-environment
[github-actions]: https://docs.github.com/actions
[cloud-agent-mcp]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/extend-cloud-agent-with-mcp
