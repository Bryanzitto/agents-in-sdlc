---
title: "Ejercicio 0: Requisitos previos"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

Antes de empezar los ejercicios del agente de Copilot en la nube, prepara todo lo necesario. Crearás tu propia copia del repositorio Tailspin Toys y abrirás un [codespace][codespaces] para editar archivos de instrucciones y revisar el trabajo del agente.

## Configura el repositorio del laboratorio

Para crear una copia del repositorio, crea una instancia a partir de la [plantilla][template-repository].
La nueva instancia incluirá todos los archivos necesarios para el taller y la usarás durante los ejercicios.

1. En una ventana nueva del navegador, ve a la [plantilla de Tailspin Toys][tailspin-template].
2. Selecciona **Use this template** y después **Create a new repository**.

    ![Botón Use this template](../../../_images/ex0-use-template.png)

3. Si participas en un evento dirigido por GitHub o Microsoft, sigue las instrucciones de los mentores. De lo contrario, crea el repositorio en una organización donde tengas acceso a GitHub Copilot.

    ![Configuración de la plantilla del repositorio](../../../_images/ex0-repository-settings.png)

4. Anota la ruta (**organization-or-user-name/repository-name**), porque la necesitarás más adelante.

## Crea un codespace

Usarás un codespace para completar los ejercicios. [GitHub Codespaces][codespaces] es un entorno de desarrollo en la nube que permite escribir, ejecutar y depurar código directamente en el navegador. Proporciona un IDE completo con compatibilidad con varios lenguajes de programación, extensiones y herramientas.

1. Ve al repositorio que acabas de crear.
2. Selecciona el botón verde **Code**.

    ![Botón Code](../../../_images/ex0-code-button.png)

3. Selecciona la pestaña **Codespaces** y, después, **+** para crear un Codespace.

    ![Crear un codespace](../../../_images/ex0-create-codespace.png)

La creación del codespace puede tardar varios minutos, aunque sigue siendo mucho más rápida que instalar todos los servicios manualmente. Mientras tanto, puedes explorar otras funciones de GitHub Copilot.

> [!CAUTION]
> Volverás al codespace en un ejercicio futuro. Por ahora, déjalo abierto en una pestaña del navegador.

> [!NOTE]
> Este taller funciona en un codespace o en un [contenedor de desarrollo][dev-containers] local. Ambos garantizan que el entorno tenga todos los requisitos previos necesarios. Para ejecutarlo localmente, abre el repositorio clonado en VS Code y selecciona **Reopen in Container** cuando se solicite; VS Code creará el mismo contenedor de desarrollo que usa el codespace.

[codespaces]: https://github.com/features/codespaces
[dev-containers]: https://code.visualstudio.com/docs/devcontainers/containers

## Resumen

Has creado una copia del repositorio del laboratorio y has iniciado la creación del codespace que usarás junto al agente de Copilot en la nube.

## Siguiente paso

Añadamos las instrucciones personalizadas que seguirá el agente. Continúa con el [Ejercicio 1: Instrucciones personalizadas][next-lesson].

## Recursos

- [Introducción a GitHub Codespaces][codespaces]
- [Crear un repositorio a partir de una plantilla][template-repository]
- [Introducción a Codespaces][codespaces-quickstart]

[tailspin-template]: https://github.com/github-samples/tailspin-toys
[template-repository]: https://docs.github.com/repositories/creating-and-managing-repositories/creating-a-template-repository
[codespaces-quickstart]: https://docs.github.com/codespaces/getting-started/quickstart
[next-lesson]: ../1-custom-instructions/
