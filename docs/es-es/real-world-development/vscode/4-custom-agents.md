---
title: "Ejercicio 4: Agentes personalizados"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

Los agentes personalizados son asistentes especializados definidos en archivos Markdown dentro de `.github/agents`. Pueden aplicar normas de accesibilidad, seguridad o pruebas y codificar conocimientos del equipo en instrucciones reutilizables.

Cada agente tiene un frontmatter YAML con al menos `name` y `description`, seguido de un prompt que define su comportamiento y experiencia.

## Escenario

Usarás el agente de accesibilidad para implementar un modo de alto contraste en Tailspin Toys.

## Revisa y usa el agente

1. Abre `.github/agents/accessibility.md`.
2. Revisa `name`, `description`, responsabilidades y ejemplos.
3. Crea una incidencia para añadir un modo de alto contraste.
4. Asigna la tarea al agente **Accessibility agent** desde Copilot Chat.
5. Revisa el código, ejecuta las pruebas y comprueba la navegación con teclado.

## Usa el agente personalizado en Copilot Chat

VS Code muestra los agentes definidos en `.github/agents` en el selector de agentes de Copilot Chat.

1. Selecciona **Agent** y abre el selector de agentes.
2. Selecciona **Accessibility agent**.

   ![Selector de modo agente en la vista de Chat](../../../_images/shared-chat-mode-selector.png)
3. Envía:

    ```plaintext
    Add a high-contrast mode to the site. There should be a toggle for high contrast which the user can set, and the setting should persist across page reloads using local storage on the browser.
    ```

4. Revisa los cambios en línea y el indicador **Files changed**.

> [!NOTE]
> El proceso puede tardar varios minutos mientras Copilot explora el código y modifica componentes Astro, estilos y pruebas relacionadas.

> [!CAUTION]
> El frontmatter con `name` y `description` es obligatorio.

## Resumen y siguientes pasos

Has usado un agente especializado para aplicar prácticas de accesibilidad. Continúa con la [administración de agentes][next-lesson].

[next-lesson]: ../5-managing-agents/
