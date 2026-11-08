---
title: "Ejercicio 2: Agente de GitHub Copilot en la nube"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

| [← Lección anterior: Instrucciones personalizadas][previous-lesson] |
|:--|

El agente de GitHub Copilot en la nube puede actualizar código y añadir funcionalidad de forma autónoma. Al terminar, crea una solicitud de incorporación de cambios preliminar para que una persona la revise.

En este ejercicio explorarás:

- la personalización del entorno de generación de código;
- las operaciones seguras;
- la importancia de delimitar bien las incidencias;
- la asignación de incidencias a Copilot.

## Escenarios

Tailspin Toys quiere resolver deuda técnica y añadir comentarios TSDoc a las funciones exportadas. Además, el equipo de diseño quiere mostrar juegos relacionados en la página de detalles. Ambos trabajos son buenos candidatos para realizarlos de forma asíncrona con el agente.

## Presentación del agente en la nube

[El agente de GitHub Copilot en la nube](https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent#overview-of-copilot-cloud-agent-formerly-copilot-coding-agent) puede ejecutar tareas en segundo plano. Puedes [asignarle una incidencia de GitHub](https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/start-copilot-sessions); Copilot creará una solicitud preliminar, preparará el entorno y comenzará el trabajo.

## La importancia de unas instrucciones bien delimitadas

No hay magia: debes pensar y delimitar las tareas. Trata el agente como un compañero de programación basado en IA, trabaja por etapas, aprende y adapta el enfoque.

## Instrucciones personalizadas de este repositorio

Antes de asignar trabajo, revisa `.github/copilot-instructions.md` y `.github/instructions/unit-tests.instructions.md`. Observa las convenciones de TypeScript, los comentarios TSDoc y el campo `applyTo`.

## Configura el entorno de desarrollo

El agente usa [GitHub Actions][github-actions]. El flujo `.github/workflows/copilot-setup-steps.yml` instala Node.js, las dependencias, los navegadores de Playwright y prepara la base de datos:

```yaml
name: "Copilot Setup Steps"

on: workflow_dispatch

env:
  ASTRO_TELEMETRY_DISABLED: "1"

jobs:
  copilot-setup-steps:
    runs-on: ubuntu-latest
    permissions:
      contents: read
    steps:
      - name: Checkout code
        uses: actions/checkout@v5
      - name: Set up Node.js
        uses: actions/setup-node@v6
        with:
          node-version: "lts/*"
          cache: "npm"
          cache-dependency-path: "./package-lock.json"
      - name: Install JavaScript dependencies
        run: npm ci
      - name: Install Playwright browsers
        run: npx playwright install --with-deps chromium
      - name: Set up the database
        run: npm run db:setup
```

El trabajo se llama `copilot-setup-steps` y el desencadenador `workflow_dispatch` permite probarlo manualmente desde **Actions**. El flujo prepara el entorno antes de que Copilot empiece a trabajar.

## Añade documentación

1. Ve al repositorio en github.com.
2. Selecciona **Issues**, después **New issue** y **Blank issue**.
3. Define el título como `Code lacks documentation`.
4. Describe que las funciones y métodos deben incluir comentarios TSDoc cuando aclaren su comportamiento.
5. Selecciona **Create** y, a la derecha, **Assign to Copilot**.
6. Selecciona **Assign** y abre la solicitud generada desde **Pull Requests**.

    ![Asignación de Copilot a una incidencia](../../../_images/shared-assign-copilot.png)

    ![Detalles de la asignación de Copilot](../../../_images/ex4-assign-copilot-details.png)

> [!NOTE]
> La lista de tareas puede tardar varios minutos en aparecer mientras Copilot prepara el entorno y analiza el proyecto.

7. Revisa la lista y las tareas que completará Copilot.
8. Desplázate por la cronología de la solicitud y observa la actualización que indica que Copilot ha empezado a trabajar.
9. Selecciona **View session** para seguir la sesión activa.

    ![Vista de la sesión de Copilot](../../../_images/ex4-view-session.png)

> [!CAUTION]
> Puede que tengas que actualizar la ventana para ver el indicador actualizado.

La sesión muestra cómo Copilot explora el código, analiza su estado, decide un plan y crea código. El proceso puede tardar varios minutos y se ejecuta de forma asíncrona.

## Añade una sección de juegos relacionados

Crea otra incidencia con el título `Show related games on the game details page` y solicita:

```markdown
- Add a data-access helper in `src/lib/` that returns other games in the same category as a given game, excluding that game
- Show a "Related games" section on the game details page that uses the helper
- Handle the case where a game has no related games
- There should be unit tests created for the new helper
- Before creating the PR, ensure all tests pass
```

Asígnala a Copilot con **Assign to Copilot**.

![Asignación de Copilot a una incidencia](../../../_images/shared-assign-copilot.png)

![Copilot indica que está trabajando en la incidencia con el emoji de ojos](../../../_images/ex4-issue-eyes-emoji.png)

Poco después, verás un conjunto de emojis 👀 en el primer comentario de la incidencia, lo que indica que Copilot está trabajando en ella. Puedes dejar que el agente trabaje mientras continúas con el ejercicio siguiente.

## Resumen y siguientes pasos

Has aprendido a personalizar el entorno, trabajar de forma segura, delimitar incidencias y asignarlas al agente. Continúa con los [agentes personalizados][next-lesson].

## Recursos

- [Acerca del agente en la nube][copilot-agents]
- [Asignar incidencias de GitHub a Copilot][assign-issue]
- [Prácticas recomendadas para el flujo de configuración][cloud-agent-best-practices]

[previous-lesson]: ../1-custom-instructions/
[next-lesson]: ../3-custom-agents/
[assign-issue]: https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/start-copilot-sessions
[copilot-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[cloud-agent-best-practices]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-environment
[github-actions]: https://docs.github.com/actions
