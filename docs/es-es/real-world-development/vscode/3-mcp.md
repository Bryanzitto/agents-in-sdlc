---
title: "Ejercicio 3: MCP con Playwright"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

El [Model Context Protocol](https://modelcontextprotocol.io/) permite conectar herramientas externas con Copilot. En este ejercicio usarás el servidor MCP de Playwright para probar la aplicación en un navegador.

Acabas de crear la funcionalidad de filtrado con el modo agente. Antes de abrir una solicitud de incorporación de cambios, confirmarás que funciona en el navegador y publicarás la rama.

## ¿Qué es Model Context Protocol (MCP)?

MCP permite que Copilot se comunique con herramientas y servicios externos en tiempo real. Un servidor MCP actúa como puente entre el agente y esas herramientas, y proporciona recursos para consultar información y herramientas para realizar acciones.

Algunos servidores MCP habituales son [GitHub MCP Server](https://github.com/github/github-mcp-server), para trabajar con repositorios e incidencias, y [Playwright MCP Server](https://github.com/microsoft/playwright-mcp), para automatizar un navegador.

> [!CAUTION]
> Trata los servidores MCP como cualquier otra dependencia. Revisa el código fuente, verifica el editor y evalúa las implicaciones de seguridad antes de conceder acceso a recursos sensibles.

## Configura Playwright MCP

Configura el servidor MCP en VS Code siguiendo la documentación del proyecto. Inicia la aplicación y concede los permisos que solicite Copilot.

El archivo `.vscode/mcp.json` configura los servidores disponibles en el workspace. Añade una entrada `playwright` junto a `github`:

```json
{
  "servers": {
    "github": {
      "type": "http",
      "url": "https://api.githubcopilot.com/mcp/"
    },
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest", "--headless"]
    }
  }
}
```

![Diagrama del modo agente y sus herramientas MCP](../../../_images/ex1-mcp-diagram.png)

Guarda el archivo. VS Code inicia el servidor local bajo demanda; si solicita confirmar que confías en él, revisa la configuración y selecciona la opción para confiar.

## Prueba la función

Pide a Copilot que abra la aplicación, seleccione un publisher y confirme que la lista se filtra correctamente. Revisa las acciones del navegador y los resultados.

Con la aplicación ejecutándose en `http://localhost:4321`, envía:

```text
Using the Playwright MCP server, open a browser to the running app at http://localhost:4321 and verify the new game filtering feature:

1. Go to the games page and note how many games are listed.
2. Apply a category filter and confirm the list updates to only show games in that category.
3. Clear it, then apply a publisher filter and confirm the list updates to that publisher.
4. Combine a category and a publisher filter and confirm the results respect both.

Report what you observe at each step, and call out anything that does not behave as expected.
```

El servidor usa el árbol de accesibilidad de la página en lugar de capturas de pantalla, por lo que esta prueba también ofrece una comprobación básica de accesibilidad.

> [!NOTE]
> No compartas credenciales ni concedas más permisos de los necesarios.

## Publica la rama y crea una solicitud de incorporación de cambios

1. Abre el panel **Source Control** y revisa los cambios.
2. Selecciona **+** para prepararlos y usa **Sparkle** para generar el mensaje de confirmación.
3. Selecciona **Publish** para publicar la rama `filtering-vscode`.

    ![Panel Source Control con los cambios realizados](../../../_images/ex3-source-control-changes.png)
4. En Copilot Chat, abre **New Chat**, confirma que está seleccionado **Agent** y pide:

   ```plaintext
   Find the issue in the repo related to filtering by category and publisher. Create a new pull request for the current branch, and associate it with the correct issue.
   ```

5. Selecciona **Continue** cuando sea necesario y revisa la solicitud creada. No la combines todavía.

## Resumen y siguientes pasos

Has conectado una herramienta externa y probado la función antes de crear una solicitud. Continúa con [agentes personalizados][next-lesson].

[next-lesson]: ../4-custom-agents/
