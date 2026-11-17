# Tablero de tareas — guía por fases

> Copia local de la guía. Versión editable y comentable: https://claude.ai/artifact/4EDthFTfHLdPJHukTFZkt7
> Última sincronización: 2026-11-17. Si cambias una de las dos, avísame para mantenerlas iguales.

## Cómo usar esta guía

Cada fase te da tareas pequeñas con un criterio de aceptación; el código lo escribes tú, siempre.

**Mi papel.** Cuando te atasques, te doy una pista. Si no basta, una explicación de cómo funciona el mecanismo. Solo como último recurso, un ejemplo, y preferiblemente de un caso parecido, no del tuyo. Pídemelo por el identificador de la tarea: *«pista de T3.2»*.

**Una tarea a la vez.** Cada tarea cabe en una sesión corta y termina en algo observable: algo que se ve en pantalla, o un test en verde. Si una tarea te lleva más de una sesión, pídeme que la parta.

**YAGNI.** Nada entra en el proyecto hasta que una tarea lo necesite. Por eso aquí hay cosas deliberadamente aplazadas: el drag & drop no llega hasta la Fase 13, el backend hasta la Fase 11, Tailwind hasta la Fase 8 y Storybook hasta la Fase 10. Mover tarjetas con un botón es suficiente durante doce fases.

**Accesibilidad como contrato, no como repaso final.** Tus E2E localizan por rol y nombre accesible. Un elemento sin nombre accesible no se puede testear, así que no está terminado. Esta regla ordena muchas decisiones de diseño por ti.

**Cómo leer una tarea.** El identificador (`T4.3`) es fase y número. *Hecho cuando* es el criterio de aceptación. *Para desbloquearte* son las preguntas que deberías saber responder al acabar: si puedes contestarlas, la tarea te ha enseñado lo que tenía que enseñarte.

## Antes de empezar: ajustes al proyecto

El scaffold ya está en TypeScript; queda una herramienta que no encaja con el curso.

**Ya está en TypeScript.** El proyecto usa la plantilla `react-ts` de Vite con TypeScript 7, y `npm run build` pasa primero por `tsc -b`. La Fase 0 sigue siendo HTML puro. En la Fase 1 no creas el `tsconfig`: revisas el que hay y entiendes cada opción.

**Trae `oxlint` y el curso usa ESLint.** El módulo 4 da ESLint con `typescript-eslint` y el 21 da Biome en el monorepo. Lo sustituirás en la Fase 1.

**Lo que NO vamos a instalar todavía**, aunque te tiente:

| Herramienta | Entra en | Por qué no antes |
| --- | --- | --- |
| Vitest + Testing Library | Fase 2 | No hay nada que testear hasta que haya un componente |
| Playwright | Fase 2 | Igual: primero una pantalla que visitar |
| Tailwind | Fase 8 | Hasta ahí, CSS a mano para entender el box model y grid |
| Storybook | Fase 10 | Necesita componentes ya estabilizados |
| axios, Zod, TanStack Query | Fase 11 | No hay servidor hasta entonces |
| Librería de drag & drop | Fase 13 | Y probablemente ni ahí: primero a mano |
| Router | Nunca, salvo que lo pidas | No está en el temario y el tablero no lo necesita |

Un `git init` y un commit por tarea te vendrá bien: cuando un test se ponga rojo, querrás saber qué cambió.

## Del temario a las fases

Cada fase usa solo lo que el curso ya te ha dado, con una excepción deliberada: los tests.

**La excepción.** El temario da testing en los módulos 9, 10 y 11, y Playwright en el 20, casi al final. Tú los quieres desde el principio. Así que desde la Fase 2 escribes tests con lo mínimo imprescindible, y cuando lleguen esos módulos no empiezas de cero: revisas y refinas una suíte que ya existe. Es mejor orden para aprender, porque llegarás a esos módulos con tests frágiles propios que arreglar.

| Módulo | Tema | Dónde lo usas |
| --- | --- | --- |
| 1 | HTML semántico y el DOM | Fase 0 |
| 2 | Accesibilidad del color y npm | Fase 0 |
| 3 | TypeScript sin framework | Fase 1 |
| 4 | Bundlers: esbuild y Vite | Fase 1 |
| 5 | Repaso: accesibilidad, TS y Lighthouse | Fase 1 y auditorías de cada fase |
| 6 | React: componentes, props y estado | Fases 2 y 3 |
| 7 | Estado derivado, efectos y context | Fase 4 |
| 8 | El sistema de tipos de TypeScript | Fase 5 |
| 9 | Testing: niveles y código testeable | Fase 6 |
| 10 | Testing: unitarios, componentes y cobertura | Fase 6 |
| 11 | Testing con dobles | Fase 6 |
| 12 | CSS | Fase 8 |
| 13 | TypeScript avanzado | Fase 5 (segunda vuelta) |
| 14 | React por dentro | Fases 7 y 12 |
| 15 | Librería de componentes y design system | Fase 10 |
| 16 | Rendimiento | Fase 12 |
| 17 | Estado fuera de React y MVVM | Fase 14 (opcional) |
| 18 | Asincronía y estado de servidor | Fase 11 |
| 19 | Movimiento e interacción | Fase 13 |
| 20 | QA Engineering | Fase 9 |
| 21 | Trabajar en el monorepo | Fase 15 |

## Fase 0 — El tablero como HTML

*Módulos 1 y 2. Sin React, sin build, sin TypeScript.* Un `index.html` estático con tres columnas y tarjetas escritas a mano. Suena a pérdida de tiempo y es la fase que más te va a ahorrar: aquí decides los roles y los nombres accesibles de los que luego colgarán todos los tests.

- [ ] **T0.1** Escribe el esqueleto de la página con sus landmarks. *Hecho cuando* la vista de accesibilidad del navegador muestra un banner, un main y, si lo pones, un nav, cada uno distinguible por su nombre.
- [ ] **T0.2** Pon el título del tablero y los de las columnas con la jerarquía de encabezados correcta. *Hecho cuando* el árbol de encabezados se lee solo, sin saltos de nivel.
- [ ] **T0.3** Representa cada columna con su lista de tarjetas. *Hecho cuando* un lector de pantalla anuncia cuántas tarjetas hay en la columna sin que tú lo escribas a mano en ningún sitio.
- [ ] **T0.4** Maqueta una tarjeta: título, identificador y prioridad. *Hecho cuando* la prioridad se entiende sin ver el color.
- [ ] **T0.5** Añade el formulario de nueva tarjeta con sus etiquetas y un estado de error. *Hecho cuando* el error se anuncia al llegar al campo y el campo se marca como inválido.
- [ ] **T0.6** Pasa Lighthouse en incógnito y arregla lo que salga en accesibilidad. *Hecho cuando* no queda ningún fallo de contraste ni de nombre accesible.

**Para desbloquearte.** ¿Qué elemento convierte «tres columnas» en algo que un lector de pantalla pueda contar y recorrer? ¿Qué diferencia hay entre el texto visible de un botón y su nombre accesible, y cuándo dejan de coincidir? Si dos columnas tienen botones «Añadir», ¿cómo distingue el test uno de otro? ¿Qué atributo ata un mensaje de error a su campo, y cuál dice que el campo está mal?

**Decisión que cierras aquí, y no se toca en doce fases:** cómo se llama cada cosa. Escribe esos nombres en un sitio aparte; son el contrato de tus E2E.

## Fase 1 — TypeScript estricto, Vite y capas

*Módulos 3, 4 y 5.* Revisas la configuración de TypeScript y le das al proyecto una estructura por capas. Sigue sin haber React en pantalla: lo último que quieres es depurar tipos y JSX a la vez.

- [ ] **T1.1** Revisa el `tsconfig` de la plantilla y entiende cada opción. *Hecho cuando* `tsc --noEmit` pasa limpio y `strict` está activo de verdad, no solo escrito.
- [ ] **T1.2** Define el tipo de una tarjeta y el de una columna, y escribe un tablero de ejemplo que los cumpla. *Hecho cuando* el compilador se queja si le quitas un campo obligatorio.
- [ ] **T1.3** Sustituye `oxlint` por ESLint con `typescript-eslint`. *Hecho cuando* el lint falla ante un `any` explícito.
- [ ] **T1.4** Crea las carpetas por capas y mueve ahí los tipos. *Hecho cuando* el dominio no importa nada de la interfaz; la flecha va siempre hacia dentro.
- [ ] **T1.5** Provoca tres errores del compilador a propósito y apunta qué te dice cada uno. *Hecho cuando* sabes leer el error sin buscarlo.

**Para desbloquearte.** ¿Qué te da exactamente `strict` que no tenías, y cuál de sus banderas te va a doler más al principio? ¿Por qué `import type` existe si `import` ya funciona? Si el dominio no puede importar de la interfaz, ¿dónde vive la función que mueve una tarjeta de columna? ¿Qué pasa en la pestaña Network cuando Vite sirve en desarrollo y qué cambia al construir para producción?

**Capas que vas a usar el resto del proyecto:** dominio (tipos y reglas, sin dependencias), aplicación (casos de uso y los puertos que necesitan), infraestructura (lo que habla con el mundo) e interfaz (React). En la Fase 6 esta separación es la que te deja inyectar dobles sin trucos.

## Fase 2 — El tablero en React, sin interacción

*Módulo 6.* Reproduces la maqueta de la Fase 0 con componentes y props. Nada se mueve todavía: el tablero se pinta desde datos fijos. Aquí nacen tus dos suítes de test.

- [ ] **T2.1** Monta la app con `createRoot` dentro de `StrictMode` y pinta el título del tablero. *Hecho cuando* se ve en el navegador.
- [ ] **T2.2** Extrae el componente de tarjeta con sus props tipadas. *Hecho cuando* el compilador te impide usarlo sin pasarle lo que necesita.
- [ ] **T2.3** Extrae el componente de columna, que recibe sus tarjetas y las pinta. *Hecho cuando* el HTML resultante conserva los roles y nombres que fijaste en la Fase 0.
- [ ] **T2.4** Pinta las tres columnas desde un array. *Hecho cuando* añadir una columna al array añade una columna en pantalla sin tocar el JSX.
- [ ] **T2.5** Instala Vitest y Testing Library y escribe el primer test de componente: la tarjeta muestra su título. *Hecho cuando* pasa y sigue el patrón AAA.
- [ ] **T2.6** Instala Playwright y escribe el primer E2E con su Page Object: la página carga y se ven las tres columnas. *Hecho cuando* pasa localizando por rol y nombre, sin un solo selector CSS.

**Para desbloquearte.** ¿Por qué `StrictMode` ejecuta algunas cosas dos veces en desarrollo, y qué clase de error pretende sacarte a la luz? ¿Qué hace falta para que React no te avise sobre las `key` de una lista, y qué valor es mala idea usar ahí? En el test de la tarjeta, ¿qué consulta de Testing Library se parece más a lo que hace una persona? ¿Qué debería saber el Page Object y qué debería quedarse en el test?

**Nota sobre React Compiler.** El temario lo menciona en el módulo 6. Déjalo desactivado hasta la Fase 12: ahí vas a querer ver primero los re-renders que evita.

## Fase 3 — Mover tarjetas entre columnas

*Módulo 6.* La primera interacción de verdad, y la funcionalidad central del producto. Con botones, no arrastrando: el drag & drop llega en la Fase 13 y hasta entonces no aporta nada que no tengas.

- [ ] **T3.1** Sube el tablero a estado en la página y pásalo hacia abajo. *Hecho cuando* la pantalla se sigue viendo igual pero el dato ya vive en `useState`.
- [ ] **T3.2** Escribe en el dominio la función que mueve una tarjeta a otra columna. *Hecho cuando* es pura: mismos argumentos, mismo resultado, y no muta lo que recibe.
- [ ] **T3.3** Test unitario de esa función en AAA, incluido el caso de mover a la columna en la que ya está. *Hecho cuando* el test fallaría si mutaras el array original.
- [ ] **T3.4** Añade a la tarjeta los botones de mover y conéctalos con un callback hacia arriba. *Hecho cuando* el nombre accesible de cada botón dice qué tarjeta mueve y adónde.
- [ ] **T3.5** Oculta o desactiva el movimiento imposible en los extremos. *Hecho cuando* la razón es perceptible sin ver el estilo.
- [ ] **T3.6** Test de componente: al pulsar el botón, la tarjeta aparece en la otra columna. *Hecho cuando* usa `user-event` y no toca el estado por dentro.
- [ ] **T3.7** E2E: mover una tarjeta de la primera a la segunda columna. *Hecho cuando* pasa tres veces seguidas sin esperas fijas.

**Para desbloquearte.** ¿Por qué el estado vive en la página y no dentro de cada columna? ¿Qué se rompe si lo pones en la columna? Si dos tarjetas se llaman igual, ¿qué distingue sus botones para el test? ¿Por qué una función pura es más fácil de testear que el componente que la usa, y cuál de los dos tests te daría más miedo perder?

**Trampa del movimiento imposible.** Un botón deshabilitado desaparece para el teclado y para muchos lectores de pantalla, y tu E2E dejará de encontrarlo. Decide a conciencia entre deshabilitar, ocultar o dejarlo activo explicando por qué no hace nada.

## Fase 4 — Crear tickets: formulario, modal y context

*Módulo 7.* Ahora el tablero crece desde la interfaz. Es la fase más larga; pártela en dos sesiones si hace falta, con el corte en T4.5.

- [ ] **T4.1** Formulario controlado de nueva tarjeta dentro de la columna. *Hecho cuando* el valor del campo y el estado no se pueden desincronizar.
- [ ] **T4.2** Ata etiquetas y campos con identificadores únicos generados por React. *Hecho cuando* tres formularios en la misma página no colisionan.
- [ ] **T4.3** Valida que el título no esté vacío y anuncia el error. *Hecho cuando* el error se oye al enfocar el campo y el campo queda marcado como inválido.
- [ ] **T4.4** Confirma la creación con un mensaje en una región viva. *Hecho cuando* se anuncia sin robar el foco.
- [ ] **T4.5** Tests: unitario del caso de uso de crear y de componente del formulario, los dos en AAA. *Hecho cuando* el de componente comprueba el error por su texto, no por una clase CSS.
- [ ] **T4.6** Mueve la creación a un modal siguiendo la APG. *Hecho cuando* el foco entra al abrir, queda atrapado dentro, vuelve al botón que lo abrió y `Escape` lo cierra.
- [ ] **T4.7** Crea el contexto del tablero con su proveedor y un hook propio. *Hecho cuando* usar el hook fuera del proveedor falla con un error que se entiende.
- [ ] **T4.8** Quita el paso de props que el contexto hace innecesario. *Hecho cuando* ningún componente recibe props que solo está reenviando.
- [ ] **T4.9** E2E: crear una tarjeta desde el modal y verla en su columna. *Hecho cuando* el Page Object expone «crear tarjeta» como una sola acción.

**Para desbloquearte.** ¿Qué parte del estado del formulario es derivada y no debería guardarse? ¿Cuándo necesita limpieza un efecto, y qué pasa exactamente si no la pones en el listener de `Escape`? ¿Por qué un hook propio sobre el contexto es mejor que exportar el contexto? El contexto, ¿qué problema resuelve y cuál no? ¿Cuántos componentes tenían que reenviar props antes de que doliera?

**No metas en el contexto** lo que solo usa una pantalla. Si acaba dentro todo el estado de la app, has cambiado paso de props por un objeto global.

## Fase 5 — El modelo de dominio, en serio

*Módulos 8 y 13.* No añades funcionalidad: endureces lo que ya tienes para que el compilador cace lo que hoy cazan tus tests. Es la fase que más código borra.

- [ ] **T5.1** Convierte el estado de la tarjeta en una unión de literales, sin `enum`. *Hecho cuando* asignar un estado que no existe no compila.
- [ ] **T5.2** Deriva de un único sitio la lista de columnas y el tipo de sus estados. *Hecho cuando* añadir una columna solo se toca en un lugar.
- [ ] **T5.3** Escribe la función que da el color o la etiqueta de cada prioridad con comprobación exhaustiva. *Hecho cuando* añadir una prioridad nueva rompe la compilación en ese punto exacto.
- [ ] **T5.4** Modela la tarjeta nueva, todavía sin identificador, distinta de la ya creada. *Hecho cuando* no puedes pasar una sin guardar donde se espera una guardada.
- [ ] **T5.5** Repasa el código buscando `any` y aserciones, y sustituye cada una. *Hecho cuando* no queda ninguna sin un comentario que justifique por qué.
- [ ] **T5.6** Borra los tests que ahora comprueban cosas que el compilador garantiza. *Hecho cuando* la suíte es más corta y no ha perdido cobertura real.

**Para desbloquearte.** ¿Por qué el temario te pide evitar `enum` si parece justo lo que necesitas? ¿Qué diferencia hay entre anotar un tipo y usar `satisfies`, y cuál conserva la información concreta del valor? ¿Cómo consigues que el compilador te avise al añadir un caso, en vez de enterarte en ejecución? ¿Qué te da `unknown` que `any` no?

**Señal de que esta fase ha funcionado:** varios tests tuyos dejan de tener sentido porque su caso ya no se puede escribir. Bórralos sin pena; esa es la ganancia.

## Fase 6 — La red de tests, ordenada

*Módulos 9, 10 y 11.* Llegas aquí con tests escritos desde la Fase 2. Esta fase no los crea: los ordena, y rompe a propósito los que no valían.

- [ ] **T6.1** Clasifica tus tests por nivel y mira la forma que sale. *Hecho cuando* sabes decir si tienes una pirámide, un trofeo o un cono invertido.
- [ ] **T6.2** Rompe cada test a propósito cambiando el código que prueba. *Hecho cuando* todos fallan; el que no falle, sobra o está mal escrito.
- [ ] **T6.3** Busca tests atados a la implementación y reescríbelos contra el comportamiento. *Hecho cuando* puedes renombrar una función interna sin tocar ningún test.
- [ ] **T6.4** Crea factorías de fixtures para tarjetas y tableros. *Hecho cuando* un test solo escribe los datos que le importan a ese test.
- [ ] **T6.5** Define el puerto del repositorio de tableros y escribe un doble falso completo. *Hecho cuando* la pantalla funciona con el doble sin saber que lo es.
- [ ] **T6.6** Test de pantalla con el doble inyectado. *Hecho cuando* espera por una consulta asíncrona y no con un tiempo fijo.
- [ ] **T6.7** Inyecta lo no determinista: identificadores y fechas. *Hecho cuando* dos ejecuciones dan exactamente el mismo resultado.
- [ ] **T6.8** Activa cobertura y mírala una vez. *Hecho cuando* puedes señalar una línea cubierta que no está realmente probada.

**Para desbloquearte.** ¿Qué diferencia hay entre un test frágil y uno flaky, y cuál de los dos te miente peor? Si un test pasa tanto con el código bien como con el código mal, ¿qué está probando? ¿Por qué inyectar el generador de identificadores en vez de simularlo globalmente? ¿Qué te dice un 90% de cobertura sobre la calidad de la suíte, y qué no te dice?

**Regla que te va a ahorrar horas:** un test que no has visto fallar no es un test, es una decoración verde.

## Fase 7 — Varios paneles

*Módulo 14, la parte de `key` e identidad.* Hasta ahora había un tablero. Ahora hay una lista y uno seleccionado, y eso saca a la luz bugs de identidad muy instructivos.

- [ ] **T7.1** Modela la lista de tableros y cuál está activo. *Hecho cuando* el estado no permite representar «ningún tablero activo» por accidente, o lo permite explícitamente porque lo has decidido.
- [ ] **T7.2** Pinta el selector de tableros y marca cuál es el actual. *Hecho cuando* el actual se anuncia como tal, no solo se ve distinto.
- [ ] **T7.3** Crear un tablero nuevo, reutilizando el modal de la Fase 4. *Hecho cuando* no has duplicado el modal.
- [ ] **T7.4** Renombrar y borrar un tablero, con confirmación antes de borrar. *Hecho cuando* el foco acaba en un sitio razonable después de borrar.
- [ ] **T7.5** Cambia de tablero con un formulario a medio escribir y observa qué pasa. *Hecho cuando* entiendes por qué el texto se queda o se va, y lo has decidido tú.
- [ ] **T7.6** E2E: crear un tablero, añadirle una tarjeta, volver al primero y comprobar que no se mezclaron. *Hecho cuando* pasa.

**Para desbloquearte.** Cuando cambias de tablero, ¿por qué React a veces reutiliza el componente anterior con su estado dentro? ¿Qué le dice a React que esto es *otra* cosa y no la misma con otros datos? ¿Qué pasa si usas el índice del array como `key` y reordenas? ¿Por qué el bug de T7.5 no lo caza ningún test unitario?

**Esta fase es la primera que duele de verdad** y es buena señal: el error de identidad en React es de los que solo se aprenden viviendo.

## Fase 8 — Que parezca un tablero

*Módulo 12.* Ocho fases sin apenas CSS. Ahora el layout de columnas en paralelo, que es un buen ejercicio de grid y de scroll.

- [ ] **T8.1** Coloca las columnas en paralelo, ocupando el alto disponible. *Hecho cuando* funciona con tres columnas y con siete.
- [ ] **T8.2** Haz que cada columna haga scroll por dentro y la página no. *Hecho cuando* la cabecera de la columna no se va al hacer scroll.
- [ ] **T8.3** Dale forma a la tarjeta: espaciado, jerarquía tipográfica y la prioridad visible. *Hecho cuando* se distingue sin color.
- [ ] **T8.4** Saca los valores repetidos a tokens. *Hecho cuando* cambiar un token cambia toda la interfaz de forma coherente.
- [ ] **T8.5** Estados de foco visibles en todo lo interactivo. *Hecho cuando* puedes recorrer el tablero entero con el teclado viendo siempre dónde estás.
- [ ] **T8.6** Comprueba que nada se rompe al ampliar el texto al 200%. *Hecho cuando* no se corta ni se superpone nada.
- [ ] **T8.7** Decide si entra Tailwind y, si entra, migra solo un componente. *Hecho cuando* puedes argumentar la decisión en dos frases.

**Para desbloquearte.** ¿Qué hace falta para que un hijo con scroll no desborde su contenedor en grid o en flex? ¿Por qué `height: 100%` falla tan a menudo y qué unidades te evitan el problema en móvil? ¿Qué diferencia hay entre `rem` y `px` cuando alguien amplía el texto? ¿Qué problema resuelve `@layer` que la especificidad te estaba causando?

**Sobre Tailwind:** el temario lo plantea como herramienta, no como religión. Si lo metes, que sea porque has visto el problema que resuelve en *tu* CSS.

## Fase 9 — La suíte E2E en condiciones

*Módulo 20.* Tienes E2E sueltos desde la Fase 2. Aquí se convierten en una suíte con estrategia, y refactorizas el POM que escribiste sin saber del todo lo que hacías.

- [ ] **T9.1** Decide qué merece E2E y qué no. *Hecho cuando* tienes una lista corta de recorridos críticos y puedes justificar lo que dejas fuera.
- [ ] **T9.2** Revisa los Page Objects: qué exponen y qué esconden. *Hecho cuando* ningún test contiene un locator y ningún Page Object contiene una aserción.
- [ ] **T9.3** Saca a un componente de POM lo que se repite entre tableros, columnas y tarjetas. *Hecho cuando* añadir una columna nueva no obliga a tocar los tests.
- [ ] **T9.4** Elimina toda espera fija. *Hecho cuando* no queda ni un `waitForTimeout`.
- [ ] **T9.5** Haz que cada test prepare y limpie su propio estado. *Hecho cuando* puedes ejecutar la suíte en paralelo y en orden aleatorio.
- [ ] **T9.6** Ejecútala veinte veces seguidas. *Hecho cuando* han pasado veinte de veinte.
- [ ] **T9.7** Añade regresión visual a una pantalla estable. *Hecho cuando* un cambio de espaciado la hace fallar y un dato distinto no.
- [ ] **T9.8** Prueba el recorrido crítico solo con teclado. *Hecho cuando* se puede crear y mover una tarjeta sin ratón.

**Para desbloquearte.** Si un test E2E falla una vez de cada veinte, ¿qué suele estar mal, el test o la aplicación? ¿Qué tiene el locator por rol que no tiene un selector CSS, más allá de la accesibilidad? ¿Por qué un Page Object que devuelve locators en bruto acaba filtrando detalles al test? ¿Qué hace falta para que una captura visual no falle por el ancho de un scrollbar?

**Si algo aquí se te resiste mucho**, mira si el problema es la aplicación: un recorrido difícil de testear suele ser difícil de usar.

## Fase 10 — Componentes como librería

*Módulo 15.* Diez fases de componentes nacidos a demanda. Ahora miras los que se repiten y les das una API pensada. Storybook entra aquí, cuando ya hay algo que documentar.

- [ ] **T10.1** Inventaria qué se repite: botón, campo, diálogo, etiqueta de prioridad. *Hecho cuando* tienes la lista y descartas lo que solo aparece una vez.
- [ ] **T10.2** Formaliza los tokens de la Fase 8. *Hecho cuando* están agrupados por intención, no por valor.
- [ ] **T10.3** Diseña la API del botón y aplícala. *Hecho cuando* no tiene props que solo existan para un caso concreto.
- [ ] **T10.4** Monta Storybook con las historias del botón, incluidos sus estados. *Hecho cuando* están el foco, el deshabilitado y el texto largo.
- [ ] **T10.5** Haz lo mismo con el campo de formulario, con su estado de error. *Hecho cuando* la historia del error muestra también cómo se anuncia.
- [ ] **T10.6** Documenta en cada componente cuándo *no* usarlo. *Hecho cuando* cada uno tiene su línea de «cuándo no».

**Para desbloquearte.** ¿Qué distingue una prop que configura de una que filtra decisiones de diseño al que la usa? Si un botón acumula seis variantes, ¿qué suele significar? ¿Por qué Storybook sirve como especificación y no solo como escaparate? ¿Qué estado se olvida siempre al documentar un componente?

**No conviertas esto en una librería de verdad.** Para un tablero, cuatro componentes bien pensados son más útiles que veinte genéricos.

## Fase 11 — Que no se pierda al recargar

*Módulo 18.* Once fases con los datos en memoria. El puerto que definiste en la Fase 6 hace que esta fase sea casi un cambio de implementación, y comprobarlo es media lección.

- [ ] **T11.1** Implementa el puerto contra `localStorage`. *Hecho cuando* recargas y el tablero sigue ahí, sin tocar ningún componente.
- [ ] **T11.2** Valida en la frontera lo que lees de fuera. *Hecho cuando* unos datos corruptos dan un error claro en vez de romper la pantalla.
- [ ] **T11.3** Levanta una API falsa y haz una implementación HTTP del mismo puerto. *Hecho cuando* puedes cambiar de implementación en un solo punto.
- [ ] **T11.4** Pinta los tres estados de la carga. *Hecho cuando* el cambio de estado se anuncia y no solo se ve.
- [ ] **T11.5** Cancela la petición pendiente al cambiar de tablero rápido. *Hecho cuando* la respuesta tardía de un tablero no pisa a la del otro.
- [ ] **T11.6** Mete MSW en los tests de componente. *Hecho cuando* no hacen peticiones de verdad y el de pantalla con el doble sigue existiendo.
- [ ] **T11.7** Introduce TanStack Query y borra lo que deje obsoleto. *Hecho cuando* has quitado más código del que has añadido.
- [ ] **T11.8** Maneja el fallo al guardar. *Hecho cuando* la persona sabe que no se guardó y puede reintentar.

**Para desbloquearte.** ¿Qué pasa si llegan dos respuestas en orden distinto al que las pediste, y por qué `AbortController` lo arregla? ¿Por qué validar en la frontera y no confiar en los tipos de TypeScript, si ya los tienes? ¿Qué diferencia hay entre el estado de tu aplicación y el estado del servidor, y por qué una librería entera se dedica solo al segundo? ¿Qué aporta MSW frente a tu doble falso, y por qué quieres los dos?

**Comprobación de arquitectura:** si para cambiar de `localStorage` a HTTP has tenido que tocar un componente, la frontera estaba mal puesta. Buen momento para arreglarla.

## Fase 12 — Mirar React por dentro

*Módulos 14 y 16.* El tablero ya hace todo lo importante. Ahora mides antes de optimizar: primero ves qué se re-renderiza y por qué, y solo después decides si merece la pena tocarlo.

- [ ] **T12.1** Activa el resaltado de renders del Profiler de React DevTools y mueve una tarjeta. *Hecho cuando* puedes decir qué componentes se pintaron y cuáles no hacía falta pintar.
- [ ] **T12.2** Graba una sesión con el Profiler y localiza el render más caro. *Hecho cuando* sabes qué prop o qué estado lo disparó.
- [ ] **T12.3** Provoca a propósito una closure obsoleta: un temporizador o un listener que lee un estado viejo. *Hecho cuando* puedes explicar qué valor capturó y arreglarlo sin desactivar el linter.
- [ ] **T12.4** Memoiza solo donde el Profiler lo justifique. *Hecho cuando* cada `memo`, `useMemo` o `useCallback` tiene detrás una medición, y has quitado los que no la tenían.
- [ ] **T12.5** Activa React Compiler y compara con tu memoización a mano. *Hecho cuando* sabes qué memoizaciones tuyas sobran ahora.
- [ ] **T12.6** Genera un tablero con 500 tarjetas en una columna y mide. *Hecho cuando* sabes si necesitas virtualizar, con un número que lo respalde.
- [ ] **T12.7** Mide LCP, CLS e INP con Lighthouse y con el panel Performance. *Hecho cuando* cada métrica está en verde o tienes apuntado por qué no.

**Para desbloquearte.** ¿Qué dispara un re-render: un cambio de props, de estado, de contexto o que el padre se pinte? ¿Por qué un objeto o una función creados en el render rompen `memo` en el hijo? Si memoizar es gratis, ¿por qué no se hace siempre? ¿Qué mide INP que no mide el tiempo de carga, y qué interacción de tu tablero es la candidata a empeorarlo?

**Regla de esta fase:** sin medición no hay optimización. Un `useMemo` puesto por intuición es deuda con apariencia de cuidado.

## Fase 13 — Arrastrar tarjetas, sin dejar a nadie fuera

*Módulo 19.* Por fin el drag & drop. Llega tarde a propósito: los botones de la Fase 3 siguen siendo la alternativa por teclado, y tus E2E ya cubren el movimiento. El arrastre es una capa nueva sobre una función de dominio que ya existe y está probada.

- [ ] **T13.1** Detecta el gesto de arrastre con pointer events sobre una tarjeta. *Hecho cuando* funciona igual con ratón, con táctil y con lápiz, y un clic corto sigue siendo un clic.
- [ ] **T13.2** Haz que la tarjeta siga al puntero mientras arrastras. *Hecho cuando* el movimiento usa `transform` y no provoca reflujo de layout en cada frame.
- [ ] **T13.3** Calcula la columna y la posición de destino al soltar, y llama a la función de dominio de la Fase 3. *Hecho cuando* no has escrito una segunda forma de mover tarjetas.
- [ ] **T13.4** Enseña dónde va a caer la tarjeta mientras arrastras. *Hecho cuando* se entiende el destino antes de soltar.
- [ ] **T13.5** Cancela con `Escape` y al soltar fuera del tablero. *Hecho cuando* la tarjeta vuelve a su sitio sin cambiar el estado.
- [ ] **T13.6** Anuncia el resultado del movimiento en la región viva de la Fase 4. *Hecho cuando* un lector de pantalla oye dónde ha quedado la tarjeta.
- [ ] **T13.7** Anima el cambio de posición y respeta `prefers-reduced-motion`. *Hecho cuando* con movimiento reducido no hay animación y todo funciona igual.
- [ ] **T13.8** E2E del arrastre con las APIs de ratón de Playwright. *Hecho cuando* el test pasa veinte de veinte y el E2E de los botones sigue en verde.

**Para desbloquearte.** ¿Por qué pointer events y no la API nativa de drag & drop de HTML, y qué te da `setPointerCapture`? ¿Qué propiedades CSS se pueden animar sin forzar layout? ¿Cómo distingues un clic de un arrastre corto? Si alguien no puede arrastrar, ¿qué camino le queda y dónde lo pruebas?

**Sobre las librerías:** hazlo primero a mano. Si después quieres probar una librería de drag & drop, sabrás exactamente qué problemas te resuelve y podrás juzgar si lo hace bien.

## Fase 14 — El estado fuera de React (opcional)

*Módulo 17.* Es opcional porque el tablero no lo necesita para funcionar. Te sirve para entender el patrón que verás en apps grandes y para comprobar tu arquitectura: si el dominio está bien separado, React acaba siendo solo la vista.

- [ ] **T14.1** Escribe un store del tablero en TypeScript puro, con `subscribe` y `getSnapshot`, sin importar React. *Hecho cuando* tiene tests unitarios que no renderizan nada.
- [ ] **T14.2** Conéctalo a React con `useSyncExternalStore`. *Hecho cuando* la UI se actualiza igual que antes y el contexto de la Fase 4 ya no guarda el tablero.
- [ ] **T14.3** Haz que `getSnapshot` devuelva la misma referencia mientras nada cambie. *Hecho cuando* no aparece el aviso de bucle infinito y el Profiler no muestra renders de más.
- [ ] **T14.4** Modela el ciclo de vida del modal de crear tarjeta como una máquina de estados explícita. *Hecho cuando* las transiciones imposibles no se pueden escribir.
- [ ] **T14.5** Separa un view model para la columna: datos listos para pintar y acciones, sin JSX. *Hecho cuando* el componente de columna no contiene ninguna decisión, solo pinta.
- [ ] **T14.6** Pasa toda la suíte. *Hecho cuando* unitarios, componentes y E2E siguen en verde sin haber cambiado ningún E2E.

**Para desbloquearte.** ¿Por qué React necesita `useSyncExternalStore` y no le basta con un `useEffect` que se suscriba? ¿Qué es el *tearing* y cuándo puede pasar? ¿Qué te da una máquina de estados frente a tres booleanos? Si quitaras React mañana, ¿qué parte del código sobreviviría?

**Si los E2E no se han tocado,** la refactorización ha salido bien: has cambiado el cómo sin cambiar el qué.

## Fase 15 — Que la calidad no dependa de acordarse

*Módulo 21.* Todo lo que hoy compruebas a mano pasa a comprobarse solo: al guardar, al hacer commit y en cada push. Es la fase que convierte tu práctica en un proyecto que otra persona podría clonar y mantener.

- [ ] **T15.1** Sustituye ESLint y el formateador por Biome. *Hecho cuando* un solo comando formatea y hace lint, y has decidido qué reglas de la Fase 1 conservas.
- [ ] **T15.2** Define en `package.json` los scripts que usará la CI: tipos, lint, unitarios y E2E. *Hecho cuando* cada uno funciona por separado y falla con código de salida distinto de cero.
- [ ] **T15.3** Añade Husky con un hook de pre-commit que revise solo los archivos cambiados. *Hecho cuando* un commit con un error de lint se bloquea y uno limpio tarda menos de unos segundos.
- [ ] **T15.4** Crea un workflow de GitHub Actions que compruebe tipos, lint y unitarios en cada push. *Hecho cuando* un push con un test roto sale en rojo en GitHub.
- [ ] **T15.5** Añade los E2E de Playwright a la CI con el informe como artefacto. *Hecho cuando* puedes abrir la traza de un fallo desde GitHub sin reproducirlo en local.
- [ ] **T15.6** Cachea las dependencias y los navegadores de Playwright. *Hecho cuando* la segunda ejecución es claramente más rápida que la primera.
- [ ] **T15.7** Protege la rama principal para que solo entre código con la CI en verde. *Hecho cuando* no puedes hacer merge de una PR en rojo.

**Para desbloquearte.** ¿Qué debe ir en el hook de pre-commit y qué solo en la CI, y por qué no todo en el hook? ¿Qué diferencia hay entre `npm install` y `npm ci`, y cuál quieres en la CI? ¿Por qué un E2E que pasa en local puede fallar en la CI? ¿Qué ganas guardando la traza de Playwright solo en los fallos?

**Cierre del proyecto:** si alguien clona el repo, ejecuta `npm ci` y un solo comando, y le sale todo en verde, has terminado.

## Anexo A — Convenciones de test

Las reglas que se repiten en todas las fases, en un solo sitio.

**Estructura AAA.** Cada test tiene tres bloques separados por una línea en blanco: preparar (*Arrange*), actuar (*Act*) y comprobar (*Assert*). Un test comprueba un solo comportamiento; si necesitas dos *Act*, son dos tests.

**Nombres.** El nombre describe el comportamiento visto desde fuera, no la implementación: «mueve la tarjeta a la columna siguiente», no «llama a setState».

**Localizar elementos, por orden de preferencia:** rol y nombre accesible, después etiqueta, después texto. Un `data-testid` solo cuando no hay nada accesible que buscar, y apuntado como deuda. Nunca clases CSS.

| Nivel | Qué prueba | Herramientas | Dónde vive |
| --- | --- | --- | --- |
| Unitario | Funciones del dominio y casos de uso, sin DOM | Vitest | Junto al archivo, `*.test.ts` |
| Componente | Un componente o una pantalla con dobles inyectados | Vitest, Testing Library, `user-event`, MSW | Junto al componente, `*.test.tsx` |
| E2E | Recorridos críticos en un navegador real | Playwright con Page Object Model | Carpeta `e2e/` en la raíz |

**Qué va en cada nivel.** Una regla de negocio se prueba en unitario. Lo que la persona ve y hace con un componente, en test de componente. En E2E solo los recorridos que, si se rompen, dejan el tablero inservible: crear, mover, cambiar de tablero y persistir.

**Estructura del POM.**

- Una clase de página por pantalla, y componentes de POM para las piezas que se repiten: tablero, columna, tarjeta, modal.
- Los métodos son acciones de la persona usuaria («crear tarjeta», «mover a»), no pasos técnicos («pulsar botón»).
- Los locators viven en el POM y nunca salen de él. Las aserciones viven en el test y nunca entran en el POM.
- Ningún test usa esperas fijas: se espera a un estado visible de la interfaz.

## Anexo B — Definición de hecho

Una tarea está terminada cuando pasa todo esto, no cuando «funciona en mi máquina». Repásala antes de marcar cada casilla.

1. Se cumple el criterio *Hecho cuando* de la tarea, y lo has comprobado tú, no supuesto.
2. Hay un test nuevo o modificado que cubre el cambio, y lo has visto fallar antes de verlo pasar.
3. Toda la suíte está en verde: tipos, lint, unitarios, componentes y E2E.
4. Lo que has añadido tiene rol y nombre accesible, y se puede usar solo con teclado.
5. No queda ningún `any`, `console.log`, test con `.only` o código comentado que no tenga su porqué.
6. No has añadido nada que una tarea posterior vaya a necesitar pero esta no (YAGNI).
7. Un commit con un mensaje que dice qué cambia y por qué, con el identificador de la tarea.
8. Puedes responder las preguntas de *Para desbloquearte* que tocan esa tarea.
