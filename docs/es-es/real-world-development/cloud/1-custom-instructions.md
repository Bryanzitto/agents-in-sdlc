---
title: "Ejercicio 1: Instrucciones personalizadas (agente en la nube)"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[← Lección anterior: Requisitos previos][previous-lesson] · [Siguiente lección: Agente de Copilot en la nube →][next-lesson]

El contexto es fundamental al trabajar con IA generativa. Los [archivos de instrucciones][instruction-files] proporcionan a Copilot la información necesaria sobre qué hacer y cómo hacerlo.

En este ejercicio:

- explorarás cómo el contexto, las directrices de código y las normas de documentación llegan a Copilot mediante instrucciones del repositorio y archivos con ámbito de ruta;
- añadirás un estándar para todo el repositorio en `.github/copilot-instructions.md`.

> [!NOTE]
> A diferencia de los itinerarios de VS Code y CLI, aquí no ejecutarás una solicitud «antes/después». El agente en la nube trabaja de forma asíncrona en incidencias de GitHub, por lo que su efecto se verá más adelante al revisar las solicitudes que genere.

## Archivos de instrucciones

### Escenario

Tailspin Toys tiene varias directrices: la capa de datos necesita pruebas unitarias, la interfaz debe usar un modo oscuro moderno, el código debe incluir comentarios TSDoc y cada archivo debe comenzar con un bloque de comentarios que describa su finalidad.

### Instrucciones personalizadas

Las instrucciones personalizadas proporcionan contexto y preferencias para que Copilot entienda el estilo y los requisitos del proyecto. Puedes definirlas para todo el repositorio o para tipos concretos de archivos.

Hay dos tipos:

- `.github/copilot-instructions.md` se envía a Copilot en cada solicitud del repositorio y contiene información y normas generales.
- `.github/instructions/*.instructions.md` contiene instrucciones para tareas o tipos de archivo concretos, como TypeScript, componentes Astro o pruebas unitarias.

> [!NOTE]
> En el IDE, los archivos de instrucciones se usan para generar código en Copilot Chat, no para completar código ni para sugerir la siguiente edición.
>
> Copilot Chat, Copilot CLI y el agente en la nube usan ambos tipos de archivo.

### Prácticas recomendadas

- Mantén `copilot-instructions.md` centrado en el proyecto, su estructura y las normas globales.
- Usa `*.instructions.md` para tipos de archivo y tareas concretas.
- Escribe en lenguaje natural, con instrucciones claras y ejemplos.

No existe una única forma correcta de crear archivos de instrucciones. Experimenta para descubrir qué funciona mejor.

> [!TIP]
> Todo proyecto que use GitHub Copilot debería tener una colección sólida de archivos de instrucciones. Consulta [awesome-copilot][awesome-copilot] para ver plantillas y recursos.

## Explora los archivos de instrucciones personalizados del proyecto

Lee los archivos de instrucciones que incluye este repositorio: hay un `copilot-instructions.md` principal y una colección de archivos `*.instructions.md` para distintas tareas.

1. Abre `.github/copilot-instructions.md`.
2. Explora el archivo y observa la breve descripción del proyecto y secciones como **Agent notes**, **Code standards**, **Scripts** y **Repository Structure**. En **Code standards**, observa la guía anidada de **GitHub Actions Workflows**.
3. Abre la carpeta `.github/instructions` y examínala. Contiene instrucciones para archivos Astro, la capa de datos Drizzle, las pruebas y otras tareas.
4. Abre `.github/instructions/unit-tests.instructions.md` y observa el campo `applyTo`, que determina los archivos a los que se aplican las instrucciones.
5. Observa las instrucciones específicas para crear pruebas unitarias.
6. Abre `.github/instructions/drizzle.instructions.md` y desplázate hasta el final. Observa los enlaces a otros archivos de instrucciones y a archivos existentes del proyecto.

> [!NOTE]
> La sección **Code formatting requirements** de `copilot-instructions.md` documenta los estándares de código del proyecto, pero todavía no exige documentación dentro del código. En los pasos siguientes añadirás reglas para los comentarios TSDoc y las cabeceras de comentarios de los archivos.

## Añade un estándar para todo el repositorio

Añade estas líneas de Markdown a `.github/copilot-instructions.md`:

```markdown
- Every exported function should have a TSDoc comment describing its purpose, parameters, and return value.
- Before imports or any code, add a comment block to the file that explains its purpose.
```

Guarda el archivo y confirma que las nuevas reglas quedan debajo de los estándares existentes.

## Confirma y publica los cambios

Los archivos de instrucciones se administran mediante el control de código fuente como cualquier otro archivo.

1. Crea y cambia a una rama nueva:

   ```bash
   git checkout -b custom-instructions-cloud
   ```

2. Prepara y confirma los cambios:

   ```bash
   git add .github/copilot-instructions.md
   git commit -m "Add doc comment and file-header standards to copilot instructions"
   ```

3. Publica la rama:

   ```bash
   git push -u origin custom-instructions-cloud
   ```

4. Abre una solicitud de incorporación de cambios desde `custom-instructions-cloud` hacia `main` y combínala. El agente en la nube leerá estas instrucciones cuando trabajes en incidencias en el siguiente ejercicio.

> [!TIP]
> Si prefieres trabajar directamente en `main`, puedes omitir la rama y confirmar los cambios directamente allí.

## Resumen y siguientes pasos

Has explorado cómo Copilot obtiene el contexto de los archivos de instrucciones del proyecto y has añadido un estándar para todo el repositorio. Verás este estándar en las solicitudes que genere el agente en la nube.

Después, [asigna tu primera incidencia al agente de Copilot en la nube][next-lesson].

## Recursos

- [Archivos de instrucciones para personalizar GitHub Copilot][instruction-files]
- [Prácticas recomendadas para crear instrucciones personalizadas][instructions-best-practices]
- [5 consejos para escribir mejores instrucciones personalizadas para Copilot][copilot-instructions-five-tips]
- [Awesome Copilot: colección de archivos de instrucciones y otros recursos][awesome-copilot]

[instruction-files]: https://docs.github.com/copilot/customizing-copilot/about-customizing-github-copilot-chat-responses
[instructions-best-practices]: https://docs.github.com/enterprise-cloud@latest/copilot/using-github-copilot/coding-agent/best-practices-for-using-copilot-to-work-on-tasks#adding-custom-instructions-to-your-repository
[copilot-instructions-five-tips]: https://github.blog/ai-and-ml/github-copilot/5-tips-for-writing-better-custom-instructions-for-copilot/
[awesome-copilot]: https://github.com/github/awesome-copilot
[previous-lesson]: ../0-prerequisites/
[next-lesson]: ../2-cloud-agent/
