---
title: "Exercício 1 - Instruções personalizadas (VS Code)"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[← Lição anterior: Pré-requisitos][previous-lesson] · [Próxima lição: Modo Agente →][next-lesson]

O contexto é essencial ao trabalhar com IA generativa. [Arquivos de instruções][instruction-files] orientam a geração de código.

Neste exercício, você explorará instruções, gerará um helper de editoras, adicionará um padrão e repetirá o prompt.

> [!CAUTION]
> O código gerado pode divergir de alguns padrões definidos. O Copilot não é determinístico; o objetivo é observar a mudança de comportamento depois de atualizar as instruções.

## Arquivos de instruções

### Cenário

As diretrizes da Tailspin Toys incluem testes unitários na camada de dados, uma interface moderna em modo escuro, comentários TSDoc e cabeçalhos de arquivo.

### Instruções personalizadas

`.github/copilot-instructions.md` é enviado em todas as solicitações do repositório. Arquivos `.github/instructions/*.instructions.md` podem ser aplicados a tipos específicos de arquivos ou tarefas.

Explore `.github/copilot-instructions.md`, `.github/instructions/unit-tests.instructions.md` e `.github/instructions/drizzle.instructions.md` para observar o contexto do projeto, o campo `applyTo`, as convenções de testes e os links para exemplos.

> [!NOTE]
> No IDE, os arquivos de instruções são usados para geração de código no Copilot Chat, não para complementações de código ou sugestões de próxima edição.

## Crie uma branch

```bash
git checkout -b custom-instructions
```

## Use o Copilot Chat

Abra `src/lib/publishers.ts`, selecione **Agent** e envie:

```plaintext
Create or update src/lib/publishers.ts with a data-access helper that returns a list of all publishers with the name and id for each. Apply the file changes.
```

## Adicione um padrão

Adicione ao `.github/copilot-instructions.md`:

```markdown
- Every exported function should have a TSDoc comment describing its purpose, parameters, and return value.
- Before imports or any code, add a comment block to the file that explains its purpose.
```

Execute o mesmo prompt novamente e observe os comentários adicionados.

O arquivo agora deve começar com um bloco de comentários e a função exportada deve ter um comentário TSDoc com finalidade, parâmetros e retorno.

## Faça commit

```bash
git status
git add .github/copilot-instructions.md src/lib/publishers.ts
git commit -m "Add doc comment standards and publishers helper foundation"
git push -u origin custom-instructions
```

Depois, crie um pull request de `custom-instructions` para `main` e faça merge. O próximo exercício usará essas instruções e o helper de editoras.

## Resumo e próximos passos

Você observou como as instruções alteram a geração de código. Em seguida, use-as no [modo Agente][next-lesson].

[previous-lesson]: ../0-prerequisites/
[next-lesson]: ../2-agent-mode/
[instruction-files]: https://code.visualstudio.com/docs/copilot/copilot-customization
