---
title: "Exercício 0: Pré-requisitos"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

Antes de começar os exercícios do VS Code, crie sua cópia do Tailspin Toys, inicie um [codespace][codespaces] e confirme que o GitHub Copilot Chat funciona.

## Configurando o repositório

Para criar uma cópia do repositório do laboratório, crie uma instância a partir do [template][template-repository].

1. Em uma nova janela, navegue até o [template do Tailspin Toys][tailspin-template].
2. Selecione **Use this template** e depois **Create a new repository**.
3. Se estiver participando de um evento do GitHub ou da Microsoft, siga as instruções dos mentores. Caso contrário, crie o repositório em uma organização com acesso ao GitHub Copilot.

![Botão Use this template](../../../_images/ex0-use-template.png)

4. Anote o caminho criado (**organization-or-user-name/repository-name**).

## Criando um codespace

1. Navegue até o repositório recém-criado.
2. Selecione o botão verde **Code**.
3. Selecione a guia **Codespaces** e depois **+** para criar um novo Codespace.

![Criar um codespace](../../../_images/ex0-create-codespace.png)

> [!CAUTION]
> Você retornará ao codespace mais adiante. Deixe-o aberto em uma guia.

## Usando o Copilot Chat e o modo Agente

O GitHub Copilot Chat deve estar instalado no IDE se você estiver usando um GitHub Codespace. Caso contrário, [instale a extensão no Visual Studio Code Marketplace][copilot-chat-extension].

1. Retorne ao codespace.
2. Se o **Copilot Chat** não aparecer no lado direito do editor, selecione o ícone **Copilot Chat**.
3. Digite `Hello world` e pressione <kbd>Enter</kbd>.
4. Se solicitado, autentique sua conta do GitHub.

![Solicitação de autenticação do Copilot Chat](../../../_images/ex1-copilot-authentication.png)

## Resumo

Você criou uma cópia do repositório e iniciou o codespace. Agora o Copilot Chat está pronto para uso.

## Próximo passo

Continue para o [Exercício 1 - Instruções personalizadas][next-lesson].

## Recursos

- [Visão geral do GitHub Codespaces][codespaces]
- [Criar um repositório a partir de um template][template-repository]
- [Introdução aos Codespaces][codespaces-quickstart]

[tailspin-template]: https://github.com/github-samples/tailspin-toys
[template-repository]: https://docs.github.com/repositories/creating-and-managing-repositories/creating-a-template-repository
[codespaces]: https://github.com/features/codespaces
[codespaces-quickstart]: https://docs.github.com/codespaces/getting-started/quickstart
[copilot-chat-extension]: https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-chat
[next-lesson]: ../1-custom-instructions/
