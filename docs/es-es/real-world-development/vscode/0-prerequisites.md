---
title: "Ejercicio 0: Requisitos previos"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

Antes de empezar los ejercicios de VS Code, crea una copia de Tailspin Toys, abre un [codespace][codespaces] y confirma que GitHub Copilot Chat funciona en el editor.

## Configura el repositorio del laboratorio

1. Abre la [plantilla de Tailspin Toys][tailspin-template].
2. Selecciona **Use this template** y **Create a new repository**.

    ![Botón Use this template](../../../_images/ex0-use-template.png)

    ![Configuración de la plantilla del repositorio](../../../_images/ex0-repository-settings.png)

3. Sigue las instrucciones de los mentores si participas en un evento; de lo contrario, crea el repositorio donde tengas acceso a Copilot.
4. Anota la ruta (**organization-or-user-name/repository-name**).

> [!NOTE]
> Al crear el repositorio a partir de la plantilla, se crea automáticamente una lista de incidencias pendientes. Trabajarás con esas incidencias durante el taller; no tienes que crear ninguna.

## Crea un codespace

[GitHub Codespaces][codespaces] es un entorno de desarrollo en la nube para escribir, ejecutar y depurar código desde el navegador.

1. Ve al repositorio.
2. Selecciona **Code**.

    ![Botón Code](../../../_images/ex0-code-button.png)
3. Selecciona **Codespaces** y **+**.

    ![Crear un codespace](../../../_images/ex0-create-codespace.png)

> [!CAUTION]
> Volverás al codespace en un ejercicio futuro. Déjalo abierto en una pestaña.

> [!NOTE]
> También puedes usar un [contenedor de desarrollo][dev-containers] local y seleccionar **Reopen in Container** en VS Code.

[codespaces]: https://github.com/features/codespaces
[dev-containers]: https://code.visualstudio.com/docs/devcontainers/containers

## Usa GitHub Copilot Chat y el modo agente

Para acceder al modo agente de GitHub Copilot Chat, necesitas tener instalada la extensión GitHub Copilot Chat en el IDE. Si usas un GitHub Codespace, ya debería estar instalada.

> [!TIP]
> Si no tienes instalada la extensión GitHub Copilot Chat, [instálala desde Visual Studio Code Marketplace][copilot-chat-extension]. También puedes abrir la vista **Extensions** de Visual Studio Code, buscar **GitHub Copilot Chat** y seleccionar **Install**.

Después de instalarla, puede que tengas que autenticarte con tu cuenta de GitHub.

1. Vuelve al codespace.
2. Selecciona el icono **Copilot Chat**.
3. Si no ves Copilot Chat a la derecha del editor, selecciona el icono **Copilot Chat** en la parte superior del codespace.
4. Escribe «Hello world» en la ventana de Copilot Chat y pulsa Enter.
5. Si no te has autenticado, sigue las instrucciones para iniciar sesión en tu cuenta de GitHub.

    ![Solicitud de autenticación de Copilot Chat](../../../_images/ex1-copilot-authentication.png)

6. Después de autenticarte, debería aparecer la ventana de Copilot Chat.

## Resumen

Has creado el repositorio y comenzado el codespace que usarás para escribir código.

## Siguiente paso

Continúa con el [Ejercicio 1: Instrucciones personalizadas][next-lesson].

## Recursos

- [Introducción a GitHub Codespaces][codespaces]
- [Crear un repositorio a partir de una plantilla][template-repository]
- [Introducción a Codespaces][codespaces-quickstart]

[tailspin-template]: https://github.com/github-samples/tailspin-toys
[template-repository]: https://docs.github.com/repositories/creating-and-managing-repositories/creating-a-template-repository
[codespaces-quickstart]: https://docs.github.com/codespaces/getting-started/quickstart
[copilot-chat-extension]: https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-chat
[next-lesson]: ../1-custom-instructions/
