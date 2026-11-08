---
title: "Ejercicio 2: Modo agente"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

El modo agente permite que Copilot explore el repositorio, modifique varios archivos y ejecute herramientas para completar una tarea.

El modo agente trabaja de forma autónoma en el IDE: explora la estructura del proyecto, actualiza los archivos necesarios, ejecuta tareas como las pruebas y corrige los errores que encuentra.

> [!NOTE]
> Aunque los nombres se parecen, el modo agente y el agente en la nube ofrecen experiencias distintas. El modo agente trabaja en tu IDE para obtener comentarios rápidos; el agente en la nube trabaja de forma asíncrona mediante incidencias y solicitudes de incorporación de cambios.

## Escenario

Añadirás un filtro de publishers a la lista de juegos, con cambios en la interfaz, la capa de datos y las pruebas.

## Usa el modo agente

1. Abre Copilot Chat y selecciona **Agent**.
2. Describe el filtro y pide que implemente la funcionalidad.
3. Revisa el plan antes de aplicar los cambios.
4. Ejecuta las pruebas y comprueba la interfaz en el navegador.

Conserva las instrucciones del proyecto y revisa cada cambio que proponga Copilot.

## Ejecuta el sitio de Tailspin Toys

Antes de cambiar nada, explora el sitio. Es una aplicación Astro única que genera HTML estático y consulta directamente una base de datos SQLite local mediante Drizzle ORM. Los helpers reutilizables están en `src/lib/` y la interactividad usa scripts Astro pequeños con las API estándar del DOM.

1. Vuelve al codespace y crea una rama:

   ```bash
   git checkout main
   git pull
   git checkout -b filtering-vscode
   ```

    ![Selector de modo agente en la vista de Chat](../../../_images/shared-chat-mode-selector.png)

2. Inicia el sitio:

   ```bash
   npm run dev
   ```

3. Abre `http://localhost:4321` en el navegador. En un codespace, el enlace se redirige automáticamente a la URL privada del codespace.

Explora la página principal y una página de detalles del juego para conocer la funcionalidad actual.

## Explora la lista de incidencias con Copilot

Selecciona **Agent**, elige **Claude Sonnet 4.5** y pide:

```plaintext
Please show me the backlog of items from my GitHub repository. Help me prioritize them based on those which will be most useful to the user.
```

Selecciona **Continue** para listar las incidencias y revisa la lista generada.

## Revisa los archivos de instrucciones

Abre `.github/instructions/ui.instructions.md` y observa las directrices de arquitectura, diseño de componentes, pruebas, accesibilidad y enlaces a las instrucciones de Astro, Tailwind CSS y Drizzle.

## Implementa el filtrado

Para completar el filtrado tendrás que actualizar la lógica de datos en `src/lib/`, añadir o actualizar las pruebas y modificar la página de listado para incorporar la interfaz de filtrado.

1. Selecciona **Add Context**, **Instructions** y `ui`.
2. Confirma que **Agent** y **Claude Sonnet 4.5** siguen seleccionados.
3. Envía:

   ```plaintext
   Please update the site to include filtering by publisher and category based on the requirements from the related GitHub issue in the backlog. A publishers helper already exists from the previous exercise, so preserve and refine that work as needed while completing the remaining data-layer, UI, and tests. Ensure all tests are passing before completion. The server is already running, so you do not need to start it up.
   ```

4. Revisa los archivos modificados y selecciona **Continue** cuando Copilot pida ejecutar las pruebas.
5. Si alguna prueba falla, deja que Copilot itere y vuelve a revisar el código.
6. Prueba la nueva funcionalidad en el navegador y selecciona **Keep** cuando todo sea correcto.

![Copilot explora los archivos del proyecto](../../../_images/ex3-agent-mode-explores.png)

![Copilot solicita confirmación para ejecutar las pruebas](../../../_images/ex3-agent-mode-run-tests.png)

![Sesión completa de Copilot Agent Mode](../../../_images/ex3-agent-mode-proposed-changes.png)

## Resumen y siguientes pasos

Has usado el modo agente para crear una función en varias capas. Continúa con la integración de [MCP con Playwright][next-lesson].

### Ejercicio adicional: implementa la paginación

Cuando crezca la lista de juegos, puedes pedir a Copilot que añada paginación. Sigue las instrucciones existentes, decide si el tamaño de página será seleccionable o fijo y proporciona el contexto necesario en el prompt.

[next-lesson]: ../3-mcp/
