---
title: "Ejercicio 3: Agentes personalizados"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

## ¿Qué son los agentes personalizados?

Los [agentes personalizados][custom-agents-concept] son asistentes de IA especializados para tareas o dominios concretos. Se definen mediante archivos Markdown en `.github/agents` y pueden incluir instrucciones, buenas prácticas y conocimiento específico. Los equipos pueden convertir su experiencia en agentes reutilizables, como un agente de accesibilidad que aplica las normas [WCAG][wcag], uno de seguridad o uno de pruebas.

Los agentes personalizados se definen mediante archivos Markdown en `.github/agents` o globalmente en `~/.copilot/agents`. Cada archivo tiene un frontmatter YAML con, como mínimo, `name` y `description`, seguido de un prompt Markdown que define el comportamiento, la experiencia y las instrucciones del agente.

### Agentes personalizados y habilidades

Los agentes personalizados y las [habilidades][agent-skills-concept] se solapan parcialmente. Ambos se definen principalmente mediante archivos Markdown y explican a una IA cómo realizar operaciones. La distinción más clara es que un **agente personalizado** es el trabajador y las **habilidades** son sus herramientas.

Los agentes personalizados tienen su propia ventana de contexto y están diseñados para orquestar habilidades e incluso otros agentes. En este taller, el agente personalizado de accesibilidad revisa y actualiza el sitio conforme a las directrices de accesibilidad; como parte del trabajo podría llamar a habilidades para gestionar solicitudes de incorporación de cambios o ejecutar pruebas.

> [!NOTE]
> No existe una única forma correcta de crear un agente. Prueba e itera para encontrar lo que funciona en tu entorno.

[custom-agents-concept]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
[agent-skills-concept]: https://docs.github.com/copilot/concepts/agents/about-agent-skills
[wcag]: https://www.w3.org/WAI/standards-guidelines/wcag/

Explorarás cómo se definen los agentes personalizados y cómo se les asigna una tarea.

## Escenario

Tailspin Toys quiere que su plataforma sea accesible. El equipo ha pedido un modo de alto contraste que las personas puedan activar y desactivar. Usarás un agente personalizado para generar esta funcionalidad.

## Revisa el agente de accesibilidad

1. Abre `.github/agents/accessibility.md`.
2. Observa los campos `name` y `description`.

> [!CAUTION]
> El frontmatter con `name` y `description` es obligatorio.

3. Revisa sus responsabilidades, buenas prácticas, ejemplos de HTML, CSS y JavaScript, y errores habituales.

## Crea y asigna una incidencia

1. Ve al repositorio.
2. Selecciona **Issues**, **New issue** y **Blank issue**.
3. Define el título como `Add high contrast mode to website`.
4. Usa esta descripción:

    ```plaintext
    We need a high contrast mode for the site. There should be a toggle for high contrast which the user can set. It should store the setting in local storage on the browser.
    ```

5. Selecciona **Create**, después **Assign to Copilot**.
6. Selecciona **Accessibility agent** y **Assign**.

    ![Asignación del agente en la nube con el agente de accesibilidad seleccionado](../../../_images/ex5-select-custom-agent.png)

El agente empezará a trabajar en segundo plano.

## Resumen y siguientes pasos

Has explorado los [agentes personalizados][custom-agents], asistentes especializados que codifican la experiencia del equipo en instrucciones reutilizables. Continúa con la [supervisión y administración de la sesión][next-lesson].

## Recursos

- [Acerca de los agentes personalizados][custom-agents]
- [Preparar agentes personalizados en una organización][org-custom-agents]
- [Preparar agentes personalizados en una empresa][enterprise-custom-agents]

[previous-lesson]: ../2-cloud-agent/
[next-lesson]: ../4-managing-agents/
[custom-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
[org-custom-agents]: https://docs.github.com/copilot/how-tos/administer-copilot/manage-for-organization/prepare-for-custom-agents
[enterprise-custom-agents]: https://docs.github.com/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-agents/prepare-for-custom-agents
