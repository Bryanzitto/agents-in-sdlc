---
title: "Exercício 1 - Instruções personalizadas (agente na nuvem)"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[← Lição anterior: Pré-requisitos][previous-lesson] · [Próxima lição: Agente na nuvem do Copilot →][next-lesson]

O contexto é essencial ao trabalhar com IA generativa. [Arquivos de instruções][instruction-files] fornecem orientação para que o Copilot entenda não apenas *o que* fazer, mas também *como* fazer.

Neste exercício, você irá:

- explorar como o contexto do projeto, as diretrizes de código e os padrões de documentação chegam ao Copilot;
- adicionar um novo padrão do repositório a `.github/copilot-instructions.md`.

> [!NOTE]
> Ao contrário dos ambientes do VS Code e da CLI, aqui você não executará um prompt antes e depois. O agente na nuvem trabalha de forma assíncrona em issues do GitHub; você verá a influência do arquivo de instruções ao revisar os pull requests que ele produzirá.

## Arquivos de instruções

### Cenário

Como toda boa equipe de desenvolvimento, a Tailspin Toys tem diretrizes para as práticas de desenvolvimento:

- a camada de dados sempre precisa de testes unitários;
- a interface deve usar modo escuro e ter aparência moderna;
- a documentação deve ser adicionada ao código na forma de comentários TSDoc;
- um bloco de comentários deve descrever a finalidade de cada arquivo.

### Instruções personalizadas

`.github/copilot-instructions.md` é enviado em todas as solicitações do repositório. Arquivos `.github/instructions/*.instructions.md` podem ser direcionados a linguagens, tipos de arquivo ou tarefas específicas.

> [!NOTE]
> No IDE, os arquivos de instruções são usados para geração de código no Copilot Chat, não para complementações de código. O Copilot Chat, o Copilot CLI e o agente na nuvem usam os arquivos do repositório.

## Explore os arquivos de instruções deste projeto

Leia os arquivos de instruções fornecidos pelo repositório: há um `copilot-instructions.md` principal e vários arquivos `*.instructions.md` para tarefas diferentes.

1. Abra `.github/copilot-instructions.md` e observe a descrição do projeto e seções como **Agent notes**, **Code standards**, **Scripts** e **Repository Structure**. Em **Code standards**, observe também as orientações aninhadas sobre workflows do GitHub Actions.
2. Explore a pasta `.github/instructions`, que contém instruções para arquivos Astro, a camada de dados Drizzle, testes e outros arquivos.
3. Abra `.github/instructions/unit-tests.instructions.md` e observe o campo `applyTo`, que define o padrão de arquivos ao qual as instruções se aplicam.
4. Observe as instruções específicas para criar testes unitários.
5. Abra `.github/instructions/drizzle.instructions.md` e veja, no final, os links para outros arquivos de instruções e arquivos existentes no projeto.

> [!NOTE]
> A seção **Code formatting requirements** documenta os padrões de código do projeto, mas ainda não exige documentação no código. Nas próximas etapas, você adicionará regras para comentários TSDoc e cabeçalhos de arquivo.

## Práticas recomendadas para gerenciar arquivos de instruções

- Mantenha `copilot-instructions.md` focado no contexto do projeto, na estrutura e nos padrões globais.
- Use arquivos `*.instructions.md` para tipos de arquivo, como testes unitários, componentes Astro e a camada de dados.
- Escreva instruções em linguagem natural e inclua exemplos do que fazer e do que evitar.

Não existe uma única forma correta de criar arquivos de instruções. Teste e ajuste as instruções conforme o projeto evolui.

## Adicione um novo padrão do repositório

Crie uma branch:

```bash
git checkout -b custom-instructions-cloud
```

Antes de editar, crie e alterne para essa branch, pois o agente lerá as instruções da branch associada à issue.

Adicione estas linhas abaixo dos padrões existentes:

```markdown
- Every exported function should have a TSDoc comment describing its purpose, parameters, and return value.
- Before imports or any code, add a comment block to the file that explains its purpose.
```

Salve o arquivo, faça commit, envie a branch e abra um pull request para `main`. Faça merge depois que as verificações passarem.

## Faça commit, envie e faça merge da atualização

1. Prepare e faça commit:

   ```bash
   git add .github/copilot-instructions.md
   git commit -m "Add doc comment and file-header standards to copilot instructions"
   ```

2. Envie a branch:

   ```bash
   git push -u origin custom-instructions-cloud
   ```

3. Abra um pull request de `custom-instructions-cloud` para `main` no github.com e faça merge.

> [!TIP]
> Se preferir trabalhar diretamente em `main`, você pode pular a etapa da branch e fazer commit diretamente nessa branch.

## Resumo e próximos passos

Você explorou os arquivos de instruções e adicionou um padrão ao repositório. Em seguida, [atribua sua primeira issue ao agente na nuvem][next-lesson].

## Recursos

- [Arquivos de instruções para personalização do Copilot][instruction-files]
- [Práticas recomendadas para instruções personalizadas][instructions-best-practices]
- [Cinco dicas para escrever instruções melhores][copilot-instructions-five-tips]

[previous-lesson]: ../0-prerequisites/
[next-lesson]: ../2-cloud-agent/
[instruction-files]: https://docs.github.com/copilot/customizing-copilot/about-customizing-github-copilot-chat-responses
[instructions-best-practices]: https://docs.github.com/enterprise-cloud@latest/copilot/using-github-copilot/coding-agent/best-practices-for-using-copilot-to-work-on-tasks#adding-custom-instructions-to-your-repository
[copilot-instructions-five-tips]: https://github.blog/ai-and-ml/github-copilot/5-tips-for-writing-better-custom-instructions-for-copilot/
