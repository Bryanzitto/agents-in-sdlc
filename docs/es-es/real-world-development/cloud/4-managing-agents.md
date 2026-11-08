---
title: "Ejercicio 4: Supervisar y administrar agentes"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

Has asignado varias tareas al agente de Copilot en la nube. Aunque trabaja de forma asíncrona y autónoma, es importante supervisarlo.

En esta lección explorarás la página de agentes y orientarás una sesión activa para solicitar funcionalidad adicional.

## Escenario

Después de pedir el modo de alto contraste, el equipo decide añadir también un modo claro. Orientarás al agente para que implemente ambos modos.

## Revisa las tareas del agente

1. Ve a la [página de agentes de Copilot](https://github.com/copilot/agents).
2. Revisa las tareas activas, como actualizar documentación, generar API y añadir el modo de alto contraste.
3. Selecciona una tarea en ejecución y revisa sus operaciones:
   - descargar el código del repositorio;
   - crear el entorno para que Copilot trabaje;
   - configurar servidores MCP;
   - completar los pasos necesarios para la tarea.
4. Revisa también el panel de la solicitud de incorporación de cambios, que aparece a la derecha y permite ver la solicitud y los archivos modificados.

> [!NOTE]
> Los pasos exactos dependen del estado y del enfoque de Copilot.

## Orienta al agente en la nube

1. Selecciona la sesión del modo de alto contraste.

    ![Sesión de accesibilidad en el centro de control](../../../_images/ex6-accessibility-session.png)

2. Espera a que termine la configuración y empiece a trabajar.
3. En el cuadro **Steer active session while Copilot is working**, añade:

    ```plaintext
    While we are working on a high contrast mode, let's also add a light mode. There should be a switch for this mode as well where users can select their desired display mode.
    ```

    ![Cuadro para orientar la sesión activa del agente en la nube](../../../_images/ex6-steer-cloud-agent-task.png)

4. Pulsa <kbd>Enter</kbd> y observa cómo Copilot confirma la solicitud y la incorpora a su flujo.

## Deja que Copilot trabaje

Copilot incorporará la nueva solicitud al terminar el paso en curso. El proceso puede tardar varios minutos, así que puedes aprovechar para repasar lo aprendido.

## Resumen y siguientes pasos

Has usado la página de agentes como centro de control para supervisar y orientar tareas activas. Continúa con la [iteración sobre las solicitudes de Copilot][next-lesson].

## Recursos

- [Página de agentes de Copilot][agents-page]
- [Acerca de los agentes personalizados][custom-agents]

[previous-lesson]: ../3-custom-agents/
[next-lesson]: ../5-iterating/
[agents-page]: https://github.blog/changelog/2025-07-03-agents-page-for-copilot-coding-agent-in-public-preview
[custom-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
