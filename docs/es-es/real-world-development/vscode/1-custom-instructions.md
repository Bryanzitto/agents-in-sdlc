---
title: "Ejercicio 1: Instrucciones personalizadas (VS Code)"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[← Lección anterior: Requisitos previos][previous-lesson] · [Siguiente lección: Modo agente →][next-lesson]

El contexto es fundamental para la IA generativa. Los [archivos de instrucciones][instruction-files] proporcionan directrices para generar código.

En este ejercicio explorarás las instrucciones, generarás un helper de publishers, añadirás un estándar a `.github/copilot-instructions.md`, repetirás la solicitud y confirmarás el resultado en `main`.

> [!CAUTION]
> El código generado puede no seguir siempre todas las normas. Copilot no es determinista; observa la tendencia después de actualizar las instrucciones.

## Archivos de instrucciones

Tailspin Toys requiere pruebas unitarias para la capa de datos, una interfaz moderna en modo oscuro, comentarios TSDoc y una cabecera de comentarios en cada archivo.

`.github/copilot-instructions.md` se aplica a todas las solicitudes del repositorio. `.github/instructions/*.instructions.md` se aplica a tareas o tipos de archivo concretos.

> [!NOTE]
> En el IDE, las instrucciones se usan para generar código en Copilot Chat, no para completar código.

## Explora las instrucciones

Revisa `.github/copilot-instructions.md`, `.github/instructions/unit-tests.instructions.md` y `.github/instructions/drizzle.instructions.md`. Observa `applyTo` y las convenciones de la capa de datos.

## Crea una rama para los cambios

Vuelve al codespace y crea una rama nueva para este trabajo:

1. Abre un terminal nuevo pulsando <kbd>Control</kbd>+<kbd>`</kbd> (Mac) o <kbd>Ctrl</kbd>+<kbd>`</kbd> (Windows/Linux).
2. Crea y cambia a la rama:

   ```bash
   git checkout -b custom-instructions
   ```

## Usa Copilot antes de actualizar las instrucciones

Antes de actualizar las instrucciones, envía el prompt con el archivo actual para poder comparar el resultado.

1. Cierra las pestañas abiertas del editor y abre `src/lib/publishers.ts`.
2. Selecciona **Agent** en el selector de agentes de Chat.
3. Envía:

   ```plaintext
   Create or update src/lib/publishers.ts with a data-access helper that returns a list of all publishers with the name and id for each. Apply the file changes.
   ```

   ![Selector de modo agente en la vista de Chat](../../../_images/shared-chat-mode-selector.png)

4. Copilot explorará el proyecto y aplicará los cambios, normalmente en el helper y sus pruebas.
5. Observa que el helper usa un cliente `db` y devuelve una matriz tipada, según las convenciones de `.github/instructions/drizzle.instructions.md`.
6. Observa que el código propuesto no incluye comentarios TSDoc ni una cabecera de comentarios.

> [!CAUTION]
> Como Copilot es probabilístico, puede que añada comentarios incluso sin que se le solicite. No pasa nada: el objetivo es observar la mejora de consistencia después de actualizar las instrucciones.

## Usa Copilot antes de actualizar las instrucciones

1. Abre `src/lib/publishers.ts`.
2. Selecciona **Agent** en Chat.
3. Envía:

   ```plaintext
   Create or update src/lib/publishers.ts with a data-access helper that returns a list of all publishers with the name and id for each. Apply the file changes.
   ```

Copilot suele generar una función tipada con un cliente `db`, pero sin comentarios TSDoc ni cabecera.

## Añade un estándar

Añade estas líneas a `.github/copilot-instructions.md`:

```markdown
- Every exported function should have a TSDoc comment describing its purpose, parameters, and return value.
- Before imports or any code, add a comment block to the file that explains its purpose.
```

Repite la misma solicitud en un chat nuevo y comprueba que el archivo incluye una cabecera y un comentario TSDoc.

## Vuelve a ejecutar el prompt y observa el cambio

1. Vuelve a Copilot Chat y selecciona **New Chat**.
2. Haz clic en `src/lib/publishers.ts` y envía el mismo prompt.
3. Comprueba que el archivo empieza con un bloque de comentarios y que la función incluye un comentario TSDoc con sus parámetros y valor devuelto.

## Confirma y publica los cambios

## Confirma y publica los cambios

Usa:

```bash
git status
git add .github/copilot-instructions.md src/lib/publishers.ts
git commit -m "Add doc comment standards and publishers helper foundation"
git push -u origin custom-instructions
```

Después, crea y combina una solicitud de incorporación de cambios en `main`.

## Crea y combina una solicitud de incorporación de cambios

Pide a Copilot que busque la incidencia relacionada con los archivos de instrucciones y cree una solicitud desde la rama actual:

```text
Find the issue related to updating the instructions file. Create a new PR from the current branch, highlight that the PR closes that issue, and include that we also added the publishers helper foundation for the upcoming filtering work.
```

Cuando la solicitud esté creada, pide a Copilot que la combine en `main` y actualice la rama local:

```text
Merge the PR into main. Then return to main locally, and pull the latest code so we are up to date.
```

## Resumen y siguientes pasos

Has observado cómo las instrucciones cambian el código generado. Continúa con el [modo agente][next-lesson].

[previous-lesson]: ../0-prerequisites/
[next-lesson]: ../2-agent-mode/
[instruction-files]: https://code.visualstudio.com/docs/copilot/copilot-customization
