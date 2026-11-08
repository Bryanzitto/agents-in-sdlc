---
title: "Exercício 0: Pré-requisitos"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

Antes de começar os exercícios do agente na nuvem, prepare tudo. Você criará sua própria cópia do repositório Tailspin Toys e iniciará um [codespace][codespaces] para editar arquivos de instruções e revisar o trabalho produzido pelo agente.

## Configurando o repositório do laboratório

Para criar uma cópia do repositório do laboratório, crie uma instância a partir do [template][template-repository]. A nova instância conterá todos os arquivos necessários para o laboratório.

1. Em uma nova janela, navegue até o [template do Tailspin Toys][tailspin-template].
2. Crie sua cópia selecionando o botão **Use this template** e depois **Create a new repository**.

![Botão Use this template](../../../_images/ex0-use-template.png)

3. Se estiver participando de um evento conduzido pelo GitHub ou pela Microsoft, siga as instruções dos mentores. Caso contrário, crie o repositório em uma organização na qual você tenha acesso ao GitHub Copilot.

![Inserção das configurações do template do repositório](../../../_images/ex0-repository-settings.png)

4. Anote o caminho criado (**organization-or-user-name/repository-name**), pois você o usará mais adiante no laboratório.

## Criando um codespace

Em seguida, você usará um codespace para concluir os exercícios.

[GitHub Codespaces][codespaces] é um ambiente de desenvolvimento na nuvem que permite escrever, executar e depurar código diretamente no navegador. Ele fornece um IDE completo com suporte a várias linguagens, extensões e ferramentas.

1. Navegue até o repositório recém-criado.
2. Selecione o botão verde **Code**.

![Selecione o botão Code](../../../_images/ex0-code-button.png)

3. Selecione a guia **Codespaces** e depois o botão **+** para criar um novo Codespace.

![Criar um codespace](../../../_images/ex0-create-codespace.png)

A criação do codespace levará alguns minutos. Enquanto isso, explore outros recursos do GitHub Copilot.

> [!CAUTION]
> Você retornará ao codespace em um exercício futuro. Por enquanto, deixe-o aberto em uma guia do navegador.

> [!NOTE]
> Este workshop foi criado para ser executado em um codespace ou em um [dev container][dev-containers] local. Ambos fornecem os pré-requisitos necessários. Se preferir executá-lo localmente, abra o repositório clonado no VS Code e selecione **Reopen in Container** quando solicitado.

[codespaces]: https://github.com/features/codespaces
[dev-containers]: https://code.visualstudio.com/docs/devcontainers/containers

## Resumo

Parabéns, você criou uma cópia do repositório e iniciou o codespace.

## Próximo passo

Adicione as instruções personalizadas que o agente seguirá. Continue para o [Exercício 1 - Instruções personalizadas][next-lesson].

## Recursos

- [Visão geral do GitHub Codespaces][codespaces]
- [Criar um repositório a partir de um template][template-repository]
- [Introdução aos Codespaces][codespaces-quickstart]

[tailspin-template]: https://github.com/github-samples/tailspin-toys
[template-repository]: https://docs.github.com/repositories/creating-and-managing-repositories/creating-a-template-repository
[codespaces-quickstart]: https://docs.github.com/codespaces/getting-started/quickstart
[next-lesson]: ../1-custom-instructions/
