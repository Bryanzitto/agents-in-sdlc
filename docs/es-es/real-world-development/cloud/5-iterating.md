---
title: "Ejercicio 5: Iterar sobre el trabajo de GitHub Copilot"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

| [← Lección anterior: Administración de agentes][previous-lesson] |
|:--|

## Revisa el trabajo

Has pedido a Copilot que añada documentación, cree una función de juegos relacionados e implemente modos de alto contraste y claro. Revisa los cambios y proporciona comentarios si es necesario.

Como siempre, revisa el código generado y sigue el proceso habitual de desarrollo. Revisa las sugerencias de Copilot antes de habilitar la revisión para el resto del equipo.

## Seguridad y agente de Copilot en la nube

- Copilot solo tiene acceso de lectura al repositorio y acceso de escritura a su propia rama.
- El agente se ejecuta en GitHub Actions, dentro de un entorno efímero independiente.
- Los flujos de GitHub Actions requieren aprobación humana.
- [El acceso a recursos externos está limitado de forma predeterminada](https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-firewall), incluidos los servidores MCP.

## Revisa la documentación generada

1. Abre la solicitud de incorporación de cambios de documentación.
2. Selecciona **Files changed** y revisa los comentarios TSDoc, las convenciones de TypeScript y las cabeceras.
3. En **Conversation**, selecciona **Approve and run workflows** si se solicita.

    ![Aprobar y ejecutar flujos de trabajo](../../../_images/shared-approve-workflows.png)

Revisa el código generado y, si todo es correcto, convierte la solicitud de borrador en lista para revisión antes de combinarla.

Puedes mencionar a **@copilot** en un comentario para pedir cabeceras, comentarios TSDoc o un README de la aplicación Astro. Selecciona **View Session** para seguir la nueva sesión y revisa el commit resultante.

Si la solicitud todavía está en curso, puede mostrar la marca **[WIP]**. Espera a que Copilot termine antes de revisar los cambios. Cuando todo sea correcto, puedes convertir la solicitud de borrador en lista para revisión y combinarla.

## Revisa la función de juegos relacionados

Abre la solicitud titulada de forma similar a **Show related games on the game details page**, revisa **Files changed**, aprueba los flujos si es necesario y comprueba que pasan las verificaciones. De forma opcional, prueba la rama en Codespaces:

```bash
git fetch origin
git checkout <branch-name>
```

![Pestaña Files changed de la solicitud](../../../_images/shared-pr-files-changed.png)

Puedes seguir iterando con Copilot desde la pestaña **Conversation**, por ejemplo para cambiar el número de juegos relacionados o añadir cabeceras y comentarios TSDoc.

## Revisa las funciones de accesibilidad

Revisa la solicitud de **Add high contrast mode to website** y comprueba:

- los controles para cambiar de modo;
- el almacenamiento local de las preferencias;
- los estilos de alto contraste y claro;
- los atributos de accesibilidad y la navegación con teclado;
- el código que administra el cambio de modo.

Después, aprueba los flujos y prueba los controles en el navegador. Puedes mencionar a **@copilot** para solicitar mejoras.

La solicitud debería incluir tanto el modo de alto contraste como el modo claro solicitado durante la supervisión de la sesión.

![Aprobar y ejecutar flujos de trabajo](../../../_images/shared-approve-workflows.png)

## Ejercicio opcional: sigue delegando

Asigna más incidencias al agente, por ejemplo un formulario de interés, paginación en la lista de juegos o validación de entradas.

## Resumen

Has completado el itinerario del agente en la nube: inspeccionaste instrucciones, asignaste incidencias, usaste un agente personalizado, supervisaste sesiones y revisaste e iteraste sobre solicitudes de Copilot.

## Revisión y siguientes pasos

- 🖥️ **[Itinerario de VS Code](../../vscode/)**: explora el modo agente y MCP.
- 💻 **[Itinerario de CLI](../../cli/)**: trabaja desde el terminal con Plan, Autopilot, habilidades y Playwright MCP.

En tu propio repositorio, asigna una incidencia de refactorización, crea un agente para otro dominio y configura `copilot-setup-steps.yml`.

## Recursos

- [GitHub Copilot][github-copilot]
- [Acerca de los agentes de Copilot][copilot-agents]
- [Asignar incidencias de GitHub a Copilot][assign-issue]
- [Configurar el firewall del agente][agent-firewall]

[previous-lesson]: ../4-managing-agents/
[github-copilot]: https://github.com/features/copilot
[copilot-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[assign-issue]: https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/start-copilot-sessions
[agent-firewall]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-firewall
