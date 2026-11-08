---
title: "Ejercicio 5: Supervisar y administrar agentes"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

Aunque Copilot trabaja de forma autónoma, debes revisar sus sesiones y orientar el trabajo cuando cambie el alcance.

En este ejercicio observarás cada llamada a herramienta y edición de archivos, aceptarás o rechazarás cambios y ampliarás la tarea sin salir del editor.

## Revisa la sesión

Observa el plan, los archivos modificados, las herramientas utilizadas y los resultados de las pruebas. Si algo no es correcto, detén la sesión o proporciona una instrucción más concreta.

En la vista de Copilot Chat, cada edición aparece con controles **Keep** y **Undo**. También puedes abrir **Files changed** para revisar todo el conjunto de trabajo.

1. Vuelve a Copilot Chat desde el ejercicio anterior.
2. Desplázate por la conversación para ver las lecturas, ediciones y comandos.
3. Selecciona **Keep** para aceptar una edición o **Undo** para revertirla.
4. Si una llamada solicita permiso, revisa el comando y aprueba solo las operaciones que consideres seguras.
5. Espera al mensaje final que resume la implementación del modo de alto contraste.

## Orienta el trabajo

Mientras Copilot implementa el modo de alto contraste, pide también un modo claro:

```plaintext
While we are working on a high contrast mode, let's also add a light mode. There should be a switch for this mode as well where users can select their desired display mode.
```

Revisa los cambios adicionales, ejecuta las comprobaciones y confirma que las preferencias persisten tras recargar la página.

Envía el siguiente prompt en la misma conversación:

```plaintext
Nice work! Now add a light-mode toggle alongside the high-contrast toggle. Light mode should follow the same pattern — persist via local storage and be accessible from the same area of the UI. The user should be able to enable high-contrast and light mode independently.
```

Revisa cada edición con **Keep** o **Undo**. Si Copilot toma una dirección incorrecta, usa **Stop** y envía una aclaración.

> [!TIP]
> Orientar una sesión en curso es más rápido que empezar de nuevo. Puedes pedir que simplifique el CSS, integre el modo claro en el panel existente o añada atajos de teclado.

## Revisa el conjunto de trabajo

Antes de confirmar los cambios:

1. Abre la vista **Source Control**.
2. Revisa los archivos modificados, incluidos los componentes Astro, los estilos y las pruebas.
3. Comprueba los atributos ARIA, la navegación con teclado, el HTML semántico y la persistencia en el almacenamiento local.
4. Cuando estés satisfecho, prepara y confirma los cambios. Los publicarás en la siguiente lección.

## Resumen y siguientes pasos

Has aprendido a supervisar y orientar sesiones de agentes en VS Code. Continúa con [Iterar sobre el trabajo de Copilot][next-lesson].

[next-lesson]: ../6-iterating/
