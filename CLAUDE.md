# ProyectoReact — tablero de tareas (proyecto de práctica del curso de React)

Proyecto de aprendizaje: un tablero tipo Jira hecho con React 19.3.1 + TypeScript 7 + Vite (plantilla `react-ts`), siguiendo la guía por fases.

## Cómo debe ayudar Claude aquí

- No escribir ni completar el código de la persona. Escalado: 1) pista, 2) explicación del mecanismo, 3) ejemplo solo como último recurso, preferiblemente de un caso análogo.
- Revisar o depurar código que ya ha escrito sí, señalando dónde está el problema sin reescribirlo.
- Las tareas se piden por identificador (`T3.2`): situarse siempre en la fase y tarea de la guía.
- Respetar YAGNI: no proponer herramientas ni código que la fase actual no necesite.
- La guía va en pasos atómicos (`T0.1.1`…): una acción y una comprobación por paso, con un bloque *Repasa* por tarea (qué conceptos buscar, nunca la solución). Cuando la persona empiece una fase que aún tiene tareas grandes, atomizarla primero, en el documento online y en `guia.md`.

## Progreso

Fase actual: Fase 0. Actualizar esta sección al acabar cada sesión.

- Hecho: T0.0.1 (`maqueta/index.html` creado) y T0.0.2 (esqueleto HTML con `lang="es"` y título «Tablero», generado con Emmet `!` + Tab; ya se le explicó cada línea). Vio la página en `http://localhost:5173/maqueta/` con `npm run dev`.
- Hecho: T0.0.3 (ve `RootWebArea "Tablero"`; en su Chrome la casilla se llama «Show accessibility tree»).
- Hecho: T0.1.1 (`<header>Tablero</header>` → `banner`; necesitó que le dijera la etiqueta: la pista abstracta no bastó).
- Hecho: T0.1.2 (`<main></main>` debajo del header → `main`).
- Hecho: T0.1.3 (`<nav>` con dos `<a href="#">` → `navigation` con dos `link`). Costó: la sintaxis de atributo + texto no la entendió con explicación; hizo falta un ejemplo análogo (`<a href="#">Inicio</a>`). También guardó tarde una vez (punto ● en la pestaña de VS Code).
- Hecho: T0.1.4 (`<nav aria-label="Tableros">`). Funcionó explicar atributos con una tabla etiqueta/nombre/valor comparando con su `<html lang="es">`.
- Hecho: T0.1.5 (`aria-current="page"` en Sprint 12; preguntó para qué sirve ponerlo a mano: se le explicó que la maqueta es el modelo que React reproducirá en la Fase 7) y T0.1.6 (commit 203cd52, solo `maqueta/`, con `git add maqueta` + `git commit maqueta -m ...`).
- Pendiente aparte: la limpieza de la plantilla (borrados en `src/`, `public/`) y los cambios de `guia.md`/`CLAUDE.md` siguen sin commit.
- Hecho: T0.2.1 (`<h1>Sprint 12</h1>` dentro de `<main>`).
- Hecho: T0.2.2 (tres `<section>` con `<h2>`; primero puso el texto suelto en la section sin `<h2>`, lo corrigió con una pista; eligió el nivel 2 solo).
- Hecho: T0.2.3. Decisión: «Tablero» NO es encabezado («no presenta ningún contenido, es información de la app»). Llegó tras reducirlo a una pregunta sí/no.
- Hecho: T0.2.4 (confirmó las tres `region`). Le costó: puso las dos cosas en el `<h2>`. Lo desbloqueó la analogía de las cajas de mudanza (caja = section, papel = h2) y ver el resultado en el árbol. Ojo: Chrome NO muestra las section sin nombre (no salen como `generic`); me equivoqué al decirlo.
- Hecho: T0.2.5 (oyó «Sprint 12» nivel 1 y las tres columnas nivel 2 en orden con `H`; Narrador dijo «ajustar arriba» porque hizo clic debajo del último encabezado: es el aviso de volver al principio, no un error).
- Hecho: T0.3.1. Decisión: `<ol>`, «el usuario puede ordenar los tickets dentro de la columna y esa posición se tiene que guardar». Primero dijo `<ul>`; lo cambió él solo con una pregunta sí/no (¿quieres que siga arriba al recargar?).
- Hecho: T0.3.2 (`<ol>` con tres `<li>` en «Por hacer»). Primero puso `<h3>` dentro del `<ol>` (se adelantó a T0.4.1); no sacó la etiqueta con pista, hizo falta decirle `<li>` y un ejemplo análogo (receta).
- Hecho: T0.3.3 (2 `<li>` en «En curso», 1 en «Hecho»; a la primera, sin ayuda).
- Hecho: T0.3.4 (oyó «lista de 3 elementos»; dijo que lo saca del `ol`, se le precisó que cuenta los `li`).
- Hecho: T0.3.5 (commit 2ad7df8, «T0.2 y T0.3», solo `maqueta/`). No recordaba cómo hacer commit: se le dieron los dos comandos de nuevo. `origin/main` va 2 commits por detrás; el push toca en T0.6.6.
- Hecho: T0.4.1 (`<h3>` dentro del primer `<li>`, a la primera).
- Hecho: T0.4.2 (`<p>TAB-1</p>` bajo el `<h3>`; con la pista «etiqueta de una letra, de *paragraph*» le bastó).
- Hecho: T0.4.3 (`<p>Prioridad: alta</p>`, a la primera).
- Hecho: T0.4.4. Decisión: `<article>` dentro del `<li>` («tiene sentido por sí sola»). Le sirvió la tabla de ejemplos sí/no y la pregunta de recortar la tarjeta en un papel.
- 2026-11-18: revisada la guía contra el temario (el usuario lo pegó; módulos 17 y 19 son opcionales y no los hará). Pidió no quitar nada, solo cubrir todo, con énfasis en React. Añadido: Fase 0 (`<time>` en T0.4.6, nueva T0.6 tabla + DOM en consola, auditoría pasa a T0.7), Fase 1 (formateador, package.json, DOM tipado, esbuild/Network, Vite por dentro), Fase 2 (ciclo de vida, presentacionales), Fase 3 (subir/bajar en columna, `vi.fn()`), T4.10 (WebP/srcSet), Fase 5 (type/interface, Partial, guard con `in`, genéricos, mapped types), T6.5 como clase, Fase 8 (apilamiento, @layer/BEM, clamp/dvh, reduced motion, figure, cx()), Fase 11 (Zod, axios, env, CLI fetch, unión discriminada), Fase 12 (escribir en render, refs, layout thrashing, import() dinámico, peso de carga), Fase 13 marcada opcional, Fase 15 (pnpm y paquetes). Sincronizado también el doc online. El repo de WIC (módulos 8 y 11) queda fuera.
- T0.4.5 en curso: `<style>` en el `<head>`, `class="prioridad-alta"` en el `<p>` y regla `.prioridad-alta { color: firebrick; }`. Le funcionó la tabla selector/propiedad/valor con un ejemplo análogo (`.aviso`). Comprobó cortando el `<style>`: «se entiende porque pone Prioridad: alta en el texto». Añadió `.prioridad-media { color: orange; }` y `.prioridad-baja { color: green; }`. T0.4.5 hecho. Ojo: `orange` sobre blanco no pasa AA; se le dejó para que lo descubra en T0.7.4 (se le avisó solo de que «habrá sorpresa»).
- Hecho: T0.4.6 (`<p>Fecha límite: <time datetime="2026-11-25">25 de noviembre</time></p>`). Le costó: primero sin `datetime`, luego lo puso en el `<p>`. Con dos correcciones a la vez dijo «no estoy entendiendo nada»; lo desbloqueó un ejemplo análogo de una línea + UNA sola acción concreta («entre la palabra time y el >»). Lección: una corrección por mensaje.
- T0.4.7: seis tarjetas TAB-1…TAB-6 con `<article>`, prioridades variadas y `<time>`. Copiar y pegar le fue bien; al coger ritmo hizo dos tarjetas de golpe. Errores típicos de copiar y pegar (TAB-2 repetido, errata), corregidos con una indicación cada uno. Falta la comprobación con Narrador.
- Hecho (2026-11-19): T0.4.7 comprobado con Narrador; las seis tarjetas suenan igual. Narrador lee todo el `<article>` de golpe al llegar con `H` (no hacen falta las flechas).
- Chrome se cerraba al activar «Show accessibility tree» (2026-11-19); se resolvió solo durante la sesión. Si vuelve a pasar, comprobar con Narrador + `Tab`.
- Hecho: T0.4.8 (commit f1d7bb7, solo `maqueta/`). T0.4 completa.
- Hecho: T0.5.1 (`<form></form>` tras el `</ol>` de «Por hacer») y T0.5.2 (`<label for="titulo">` + `<input id="titulo" type="text">`). Preguntó por qué no un `<h2>` en vez de `<label>`: se le explicó con el árbol de encabezados (parecería una cuarta columna) y los dos efectos del label. Le sirvió probar el clic ANTES de atar (no pasa nada) y comparar `for`/`id` con su `aria-labelledby`/`id`; hizo los dos atributos de golpe sin ayuda.
- Hecho: T0.5.3 (select + label `for="prioridad"`, a la primera; le sirvió la tabla `ol/li` ↔ `select/option`), T0.5.4 (`<button type="submit">Añadir tarjeta</button>`), T0.5.5 (`<p>` de error; una errata de tilde), T0.5.6 (`aria-describedby="error-message"`; comparado con `aria-labelledby`), T0.5.7 (`aria-invalid="true"`) y T0.5.8 (Narrador dice «Título», no válido y el error). Esta parte fue fluida: las tablas etiqueta/atributo/valor y reutilizar mecanismos ya vistos funcionan muy bien.
- Hecho: T0.5.9 (commit 006d536, solo `maqueta/`). T0.5 completa.
- Siguiente: T0.6.1 (tabla «Resumen del sprint» con `<caption>`, debajo de las tres columnas, dentro de `<main>`). Ya se le explicó el paso (tabla `<table>`/`<caption>` y analogía caja/papel), pero no lo empezó.
- 2026-11-24: se cambia de PC con Windows a un **Mac**. A partir de ahí: VoiceOver (`Cmd`+`F5`) en lugar de Narrador; adaptar a VoiceOver T0.6.5 y los demás pasos con lector de pantalla, en `guia.md` y en el doc online, antes de pedírselos. Atajos con `Cmd`. Si la primera vez que hace commit en el Mac le pide nombre, email o login de GitHub, ayudarle. La memoria local de Claude no viajó: las preferencias de ritmo están en esta sección.
- Lo que le funciona para conceptos nuevos: una analogía cotidiana (cajas de mudanza), una tabla etiqueta/nombre/atributo/valor, y ver el resultado en el árbol enseguida. La jerga sin explicar («nodos generic») lo pierde.
- Ritmo que funciona: UN paso cada vez, en lenguaje llano, esperando a que diga «hecho» y revisando su archivo antes de seguir. Con listas largas de pasos se pierde («no entiendo nada»). Detalles prácticos de VS Code incluidos (en un momento creó un archivo en vez de una carpeta).

## Guía

@guia.md
