# Curso: Construye tu propio agente de noticias de IA (NotiAgente Hered-IA)

Guía de producción para grabar el curso desde cero. Incluye diálogos verbatim,
qué mostrar en pantalla en cada momento, checkpoints del alumno y errores
comunes con su fix.

---

## Cómo usar este documento

Cada módulo está pensado para grabarse como una clase independiente. Dentro de
cada módulo encontrás:

- **🎯 Objetivo** — qué saldrá sabiendo el alumno.
- **⏱️ Duración** — minutos de clase final ya editada.
- **🧠 Concepto clave** — la idea que tiene que entender sí o sí.
- **🎬 Guion** — lo que decís frente a cámara. Está numerado por bloques cortos.
- **🖥️ Apoyos en pantalla** — qué se ve mientras hablás, sincronizado con el
  guion por número.
- **✅ Checkpoint** — qué debe tener funcionando el alumno al cerrar el módulo.
- **⚠️ Errores comunes** — los tropiezos más probables y cómo desbloquearlos.

El guion no es para leerlo robóticamente. Es la línea base; adaptalo a tu tono.
Lo que sí debe quedar son los conceptos clave y los apoyos en pantalla en el
orden indicado, porque están sincronizados con la lógica de la app.

---

## Equipo y setup de grabación

Antes de arrancar a grabar:

- Pantalla en 1920×1080 mínimo, escala al 125% para que el código se lea.
- Editor (VS Code o el de tu preferencia) con tema oscuro y fuente ≥ 16 pt.
- Terminal en oscuro con fuente ≥ 18 pt.
- Cuenta de Telegram con un chat dedicado al curso para que el alumno te vea
  trabajar en vivo.
- Webcam encuadrada arriba a la derecha, recuadro pequeño.
- Conviene tener una carpeta `assets-curso/` con capturas pre-hechas del flujo
  para no depender de la conexión durante grabación (más abajo lista cuáles).

---

## Esquema general del curso

| # | Módulo | Duración estimada |
|---|---|---|
| 0 | Visión general y demo | 12 min |
| 1 | Cuentas y herramientas | 15 min |
| 2 | Setup local del proyecto | 20 min |
| 3 | Radar de releases (RSS + Hacker News + scoring) | 35 min |
| 4 | Capa editorial con LLM | 30 min |
| 5 | Imagen estilo magazine cover | 35 min |
| 6 | Entrega a Telegram | 15 min |
| 7 | Automatización con GitHub Actions | 25 min |
| 8 | Selección interactiva con Cloudflare Worker | 25 min |
| 9 | Operación, memoria editorial y monitoreo | 15 min |
| 10 | Cierre, costos y próximos pasos | 8 min |

Total ≈ 3 h 35 min de clase editada. Recomiendo grabar uno o dos módulos por
sesión para no quemar la voz.

---

## Capturas que conviene tener listas antes de grabar

Tenelas en tu carpeta `assets-curso/` con estos nombres para referenciarlas en
los apoyos en pantalla:

- `arquitectura.png` — diagrama del flujo completo.
- `top3-telegram.png` — captura del brief en Telegram.
- `cover-instagram.png` — captura de la portada final 1080×1080.
- `gh-actions-secrets.png` — pantalla de Secrets en GitHub.
- `worker-dashboard.png` — Cloudflare Workers con el nuestro deployado.
- `editorial-prompt.png` — pantallazo del prompt editorial con anotaciones.

Cada apoyo en pantalla del guion referencia "captura" cuando aplique.

---

## Módulo 0 — Visión general y demo

### 🎯 Objetivo

Que el alumno entienda en 10 minutos qué problema resolvemos, qué va a
construir y cómo se verá el resultado final.

### ⏱️ Duración

12 min.

### 🧠 Concepto clave

> "Un agente de IA no es un chatbot. Es una pieza de software que decide qué
> hacer y cuándo, sin que vos estés sentado al frente. NotiAgente Hered-IA
> decide cada mañana qué lanzamiento de IA merece publicación y arma el
> material para que vos lo grabes."

### 🎬 Guion

1. "Hoy te voy a enseñar a construir un agente que cada mañana pesca las
   noticias de IA más relevantes, decide cuál es la más fuerte para tu
   audiencia, te escribe el guion para TikTok, Instagram, LinkedIn y X, y te
   diseña la portada para Instagram. Todo solo. Mientras vos dormís."

2. "Esto no es teoría. Es la misma app que yo uso todos los días. Se llama
   NotiAgente Hered-IA y al terminar este curso vas a tener tu propia versión
   corriendo en tu Telegram, con tu marca, tu tono y tus colores."

3. "Antes que nada, mirá el resultado." *(mostrás Telegram con el Top 3 y la
   imagen final)*

4. "Esto que ves es lo que llega cada día a las siete de la mañana. Un Top 3
   curado de lanzamientos reales, no rumores ni opiniones, y al pulsar un
   número en Telegram, el sistema arma el contenido completo y la imagen lista
   para publicar."

5. "El stack es sencillo: Python para la lógica, GitHub Actions para la
   automatización gratis, OpenAI para la inteligencia, Pillow para componer
   imágenes, Telegram como tu interfaz, y Cloudflare Workers para que puedas
   pedir contenido escribiendo un número en el chat."

6. "Lo más importante de todo el curso: no vas a aprender a usar una IA. Vas a
   aprender a construir un sistema que usa la IA por vos. Esa es la diferencia
   entre quien sigue prompts y quien construye agentes."

### 🖥️ Apoyos en pantalla

1. Diapositiva con título "NotiAgente Hered-IA" + tu logo.
2. Diapositiva con la frase del concepto clave a pantalla completa.
3. Captura `top3-telegram.png` + `cover-instagram.png` lado a lado.
4. Misma captura del Top 3, con el cursor recorriendo cada uno de los tres
   ítems.
5. Diapositiva con los seis íconos del stack (Python, GitHub Actions, OpenAI,
   Pillow, Telegram, Cloudflare).
6. Diapositiva de cierre del módulo con tres palabras grandes: "PESCAR ·
   DECIDIR · ENTREGAR".

### ✅ Checkpoint

El alumno entiende qué hace la app, ve el resultado y acepta el alcance del
curso. No tiene que tener nada instalado todavía.

### ⚠️ Errores comunes

- "Esto es solo para programadores": frenalo. El curso asume cero Python pero
  sí cero miedo a copiar comandos. Decílo explícito al final del módulo.
- Tentación de mostrar el código aquí: no. Acá solo se vende el qué, no el
  cómo. Si abrís el editor, perdés el hilo.

---

## Módulo 1 — Cuentas y herramientas

### 🎯 Objetivo

Que el alumno tenga las 4 cuentas necesarias y las 3 herramientas locales
listas para empezar.

### ⏱️ Duración

15 min.

### 🧠 Concepto clave

> "Antes de escribir una sola línea de código, vamos a abrir las cuentas que
> el sistema necesita. Cada una tiene un rol claro y cuesta cero o casi cero
> por mes."

### 🎬 Guion

1. "Vas a necesitar cuatro cuentas: GitHub, OpenAI, Telegram y Cloudflare. Las
   cuatro tienen plan gratis suficiente para que el sistema corra durante
   meses. El único costo real va a ser OpenAI, y son centavos al día."

2. "GitHub es donde va a vivir el código y donde se va a ejecutar la
   automatización gratis. Si ya tenés cuenta, perfecto. Si no, te creás una en
   github.com en dos minutos."

3. "OpenAI es el cerebro: vamos a usar gpt-5-mini para texto y gpt-image-1 para
   imágenes. Andá a platform.openai.com, creás un API key y la guardás. Te
   advierto: cargás cinco dólares de crédito y te van a alcanzar para más de
   un mes."

4. "Telegram es la cara que te va a hablar. Vamos a crear un bot con BotFather
   y un chat dedicado. Si nunca usaste un bot, no te asustes: son tres
   comandos y te toma menos de cinco minutos."

5. "Cloudflare lo usamos solo para que puedas responder números en Telegram y
   disparar contenido. Plan gratis, sobra. Si no querés esa interacción podés
   saltártelo, pero te recomiendo hacerlo porque cierra el círculo."

6. "Del lado de tu máquina necesitás tres cosas: Python 3.11 o más nuevo,
   Git para subir el código, y un editor decente. Yo uso VS Code, pero el que
   uses está bien."

### 🖥️ Apoyos en pantalla

1. Diapositiva con los 4 logos: GitHub, OpenAI, Telegram, Cloudflare.
2. Navegador en github.com mostrando el botón "Sign up".
3. Navegador en platform.openai.com → API keys. Mostrar dónde se crea uno y
   tachá tu key real con barra negra en post.
4. Telegram abierto + chat con @BotFather. Mostrá el flujo de `/newbot`.
5. Dashboard de Cloudflare con la sección Workers.
6. Terminal con `python3 --version` y `git --version` ejecutándose.

### ✅ Checkpoint

El alumno tiene:
- Cuenta GitHub.
- API key de OpenAI guardada en un gestor de contraseñas.
- Bot de Telegram creado y el token a mano.
- `chat_id` obtenido enviando un mensaje al bot y abriendo `getUpdates`.
- Cuenta Cloudflare creada (sin Worker todavía).
- Python 3.11+, Git y editor instalados localmente.

### ⚠️ Errores comunes

- Confundir Bot Token con Chat ID. Mostralo bien: token es del bot, chat id
  es del destino donde el bot debe escribir.
- No agregar saldo a OpenAI. Sin saldo, las llamadas devuelven 429 / error de
  billing. Pedíles que carguen mínimo cinco dólares antes del módulo 4.
- Python 2 en sistemas viejos. Si `python --version` dice 2.x, hay que usar
  `python3` explícito durante todo el curso.

---

## Módulo 2 — Setup local del proyecto

### 🎯 Objetivo

Clonar el repo, crear entorno virtual, instalar dependencias y dejar el `.env`
listo para correr el script en modo de prueba.

### ⏱️ Duración

20 min.

### 🧠 Concepto clave

> "Antes de tocar la lógica, queremos verlo correr en nuestra máquina. Si
> arranca local con datos falsos, sabemos que el entorno está sano. A partir
> de ahí, todo lo que toquemos será código real."

### 🎬 Guion

1. "Vamos a clonar el repo del curso. Es la misma versión final de
   NotiAgente. Vos vas a partir de ahí y le vas a poner tu marca."

2. "Primer paso, terminal abierta, te vas a la carpeta donde tengas tus
   proyectos y clonás. Después entrás a la carpeta y abrís el editor en ese
   directorio."

3. "Lo segundo, y esto es importante porque mucha gente lo saltea: vamos a
   crear un entorno virtual. Es una caja aislada donde instalamos las
   librerías sin ensuciar el Python global de tu compu. Un comando, lo
   activás, y listo."

4. "Tercer paso, instalamos requirements. Son cinco librerías: requests,
   feedparser, python-dotenv, openai y Pillow. Pip se encarga del resto."

5. "Cuarto paso, el archivo `.env`. Copiamos el `.env.example`, lo renombramos
   a `.env` sin el example, y ahí adentro pegamos las claves que conseguimos
   en el módulo anterior. Este archivo nunca va a Git. Es secreto."

6. "Y el último paso para cerrar este módulo: lo corremos en modo prueba.
   Hay una variable de entorno que activa artículos falsos, así no
   dependemos de RSS reales para verificar que el flujo funciona. Si te llega
   un mensaje a Telegram con un Top 3 simulado, el setup está sano."

### 🖥️ Apoyos en pantalla

1. Terminal con `git clone <url> ai-trend-agent && cd ai-trend-agent`.
2. Terminal con `code .` o `cursor .` abriendo el editor.
3. Terminal con `python3 -m venv .venv && source .venv/bin/activate`. Mostrá
   cómo cambia el prompt para indicar venv activo.
4. Terminal con `pip install -r requirements.txt`. Dejá que se vean las cinco
   líneas instalándose.
5. Editor abierto en `.env.example`, lo duplicás a `.env`, abrís `.env` y
   completás cada variable. Recordá tachar tu key real en post.
6. Terminal con `TEST_MODE=1 RADAR_MODE=brief python daily_brief.py` corriendo,
   seguido de mostrar el Top 3 que llega a tu Telegram.

### ✅ Checkpoint

- Carpeta clonada y abierta en editor.
- `.venv` creado y activado.
- Dependencias instaladas sin errores.
- `.env` lleno con las cuatro variables principales.
- Mensaje de prueba recibido en Telegram con los artículos `TEST_MODE=1`.

### ⚠️ Errores comunes

- Olvidar activar el venv y `pip install` ensucia el global. Si pasa, deletear
  el venv y rehacer.
- `ValueError: Falta OPENAI_API_KEY en .env` — abrieron el `.env.example` en
  vez del `.env`, o lo guardaron con extensión `.txt`.
- Telegram no responde: el chat_id está mal, o el bot todavía no recibió un
  primer mensaje del usuario. Pedíles que abran el chat con el bot y digan
  "hola" antes de correr el script.

---

## Módulo 3 — Radar de releases

### 🎯 Objetivo

Entender de dónde vienen los lanzamientos, cómo se filtran y cómo se evita
publicar dos veces el mismo.

### ⏱️ Duración

35 min.

### 🧠 Concepto clave

> "Un agente sin buena curaduría es solo ruido automatizado. La diferencia
> entre un radar útil y uno irrelevante es qué fuentes mira y cómo decide
> qué tirar."

### 🎬 Guion

1. "Acá empieza la parte interesante. El radar es lo que separa noticias
   reales de chismes de internet. Tenemos cuatro tipos de fuente, cada una
   con un rol distinto."

2. "Fuentes oficiales: RSS de OpenAI, Anthropic con Claude Code, Google con
   Gemini, Vertex AI y DeepMind. Son las que publican los lanzamientos
   formales. Cuando algo sale acá, es real."

3. "Fuentes editoriales: TechCrunch IA, The Verge IA, MIT Technology Review.
   Estas captan cosas que las oficiales tardan en confirmar, pero que ya
   están circulando."

4. "Hacker News: vía la API gratuita de Algolia. Lo usamos para detectar
   lanzamientos comentados, esos que la comunidad técnica está discutiendo
   hoy. Solo aceptamos posts con al menos ochenta puntos en las últimas 72
   horas."

5. "Y un fallback de último recurso, Google News, solo si nada de lo anterior
   llegó al umbral mínimo. Es el plan C, porque tiene mucho ruido."

6. "Cada artículo pasa por una función llamada `release_score`. Le suma
   puntos por dominio oficial, palabras como release o launched o pricing,
   entidades como OpenAI o Claude. Le resta puntos por opiniones, predicciones
   de AGI, frases tipo 'el CEO dijo'. La idea es premiar lanzamientos reales
   y castigar editorial."

7. "Después viene la diversificación. No queremos un Top 3 con tres
   lanzamientos de OpenAI. La función `diversify_releases` fuerza un proveedor
   distinto por slot, si hay material."

8. "Y por último, la memoria. Cada link que ya mostramos lo guardamos en
   `history_brief.json`. Mañana, ese link no vuelve. Pero hay un truco: si
   por filtrar history nos quedamos sin nada, reintentamos sin ese filtro,
   porque mejor algo viejo que nada."

### 🖥️ Apoyos en pantalla

1. Diapositiva con los cuatro tipos de fuente como cajas conectadas a una
   caja central llamada "pool de candidatos".
2. Editor abierto en `daily_brief.py`, scroll a la constante
   `OFFICIAL_SOURCES`, marcador en pantalla resaltando los cinco RSS.
3. Editor en `EDITORIAL_RSS_SOURCES` con los tres RSS editoriales.
4. Editor en `fetch_hacker_news`, resaltar el filtro
   `points>={min_points}`. Abrir `hn.algolia.com` en el navegador para
   mostrar que la API es pública.
5. Editor en `KEYWORDS` y la rama de Google News dentro de
   `_fetch_articles_with_filter`. Comentar que es el último plan.
6. Editor en `release_score`, hacer scroll lento. Resaltar `priority_entities`,
   `penalty_terms` y la línea que cancela CEO sin release concreto.
7. Editor en `diversify_releases`. Recorrer el for que requiere proveedor
   nuevo en la primera pasada.
8. Editor en `load_history`, `save_history` y la línea del retry sin filtro
   dentro de `fetch_new_articles`.

### ✅ Checkpoint

El alumno puede:
- Explicar qué fuente aporta qué tipo de señal.
- Localizar `release_score` y entender cómo cambia el puntaje al cambiar los
  pesos.
- Correr la app con `TEST_MODE=1` y ver el log
  `brief: articulos crudos=..., pool editorial=...` para diagnosticar.

### ⚠️ Errores comunes

- Querer subir `MIN_RELEASE_SCORE` para "ser más exigentes": no es el lugar.
  Esa función es solo el primer filtro grueso. El editor LLM hace la decisión
  fina más adelante.
- Agregar un RSS roto y no detectarlo. Mostrá cómo `feedparser` no rompe
  el flujo si una URL devuelve 404 — pero también que conviene checkearlas
  cada cierto tiempo.

---

## Módulo 4 — Capa editorial con LLM

### 🎯 Objetivo

Que el alumno entienda por qué metemos un LLM como editor jefe, cómo le
hablamos y cómo confiamos en su salida sin perder control.

### ⏱️ Duración

30 min.

### 🧠 Concepto clave

> "El scoring decide qué es un release. El editor LLM decide qué vale la pena
> contar. Son dos preguntas distintas. La magia del sistema vive acá."

### 🎬 Guion

1. "Tenemos un pool de ocho candidatos diversificados. Ahora viene la
   pregunta editorial: ¿cuál de estos ocho merece publicación hoy, y cómo se
   lo contamos a alguien que no es técnico?"

2. "Para eso pasamos esos ocho a gpt-5-mini con un prompt muy claro. Le
   decimos: actúas como editor jefe de un canal en español para LATAM, tu
   audiencia son rectores, gerentes, emprendedores no técnicos. Esa
   delimitación es lo que vuelve los titulares humanos en vez de jerga de
   changelog."

3. "El editor responde JSON estructurado. Por cada candidato, nos devuelve un
   `editorial_score` de cero a cien, un `headline_es` que ya está en español
   natural, un `hook` que explica por qué importa, y un `image_concept` que
   describe en inglés cómo debería verse la portada."

4. "Importante: el editor también puede flaguear un `skip_reason` cuando
   piensa que algo no vale la pena. Pero le sacamos el poder de veto. Si lo
   flaguea, lo deja al fondo del ranking, pero no lo descartamos. Esa
   decisión salvó al sistema de quedarse sin Top 3 los días flojos."

5. "Le pasamos también una memoria editorial: los titulares de los últimos
   siete días, para que no repita el mismo ángulo dos veces seguidas. Si
   ayer salió OpenAI y antier también, hoy prefiere Anthropic o Google si
   tienen algo sólido."

6. "Toda esta llamada está envuelta en try except. Si gpt-5-mini falla,
   devuelve JSON inválido o tarda demasiado, caemos a fallbacks
   deterministas y la app sigue. Nunca dejes que un LLM rompa tu pipeline."

7. "Y por último, el ranking final. Ordenamos por `editorial_score`
   descendente, con `release_score` como desempate. El Top 3 sale de acá."

### 🖥️ Apoyos en pantalla

1. Diapositiva con dos columnas: "scoring técnico" vs "scoring editorial",
   con bullets de qué resuelve cada uno.
2. Editor en la función `editorial_enrich`, scroll desde el principio.
3. Editor en `_editorial_prompt`, resaltar la sección de roles y reglas duras.
4. Editor en la sección del prompt donde se describen los campos del JSON.
   Mostrar el ejemplo de `image_concept` y la nota sobre no repetir
   descripción visual como titular.
5. Editor en el bloque del `skip_reason` dentro de `editorial_enrich`. Marcar
   el comentario que explica por qué no lo usamos como veto.
6. Editor en `recent_published_summaries` y la inyección de `memory_block`
   dentro del prompt.
7. Editor en el `try / except` envolviendo `client.responses.create`,
   mostrando los dos fallbacks (`return releases` directo).
8. Editor en el sort final, resaltando la tupla de claves.

### ✅ Checkpoint

El alumno puede:
- Localizar el archivo `published_log.json` después de un brief.
- Editar el prompt y cambiar el tono editorial (por ejemplo, de "no técnico"
  a "para CTOs").
- Forzar un error en la llamada al LLM (cortando internet o cambiando el
  modelo) y confirmar que el script no muere.

### ⚠️ Errores comunes

- Pedirle al LLM más campos que los que se procesan después. Cada campo del
  JSON debe tener un consumer claro en el código.
- Editar el prompt y olvidar actualizar el ejemplo de JSON al final. Si los
  campos del schema no coinciden con el ejemplo, el modelo se confunde.
- No setear `text={"format": {"type": "json_object"}}`. Sin eso, el modelo
  puede devolver prosa con el JSON adentro y parse falla.

---

## Módulo 5 — Imagen estilo magazine cover

### 🎯 Objetivo

Generar una imagen que pare el scroll en Instagram, separando claramente
qué hace la IA y qué hace Pillow.

### ⏱️ Duración

35 min.

### 🧠 Concepto clave

> "La IA dibuja, Pillow escribe. Nunca al revés. Los modelos de imagen
> hacen escenarios espectaculares pero escriben tipografía de pesadilla. La
> solución es usar cada herramienta para lo que es buena."

### 🎬 Guion

1. "Esta parte es la que más feedback bueno recibe del público. Vamos a
   armar portadas que se sienten editoriales, tipo Wired o TIME, no
   infografías corporativas."

2. "El truco es dividir en dos capas. gpt-image-1 genera solo el fondo: una
   escena cinematográfica conceptual. Por ejemplo, si la noticia es 'OpenAI
   lleva sus modelos a AWS', la IA dibuja una subestación industrial al
   atardecer con cables que brillan."

3. "Esa descripción de la escena la inventa el editor LLM en el campo
   `image_concept`, en inglés porque los modelos de imagen entienden mejor
   inglés."

4. "Sobre ese fondo, Pillow dibuja todo el texto. Y todo significa todo: el
   kicker arriba del titular, el titular gigante en tipografía Anton bold
   condensada, y la marca personal arriba a la derecha con el avatar."

5. "Anton es una fuente Google Open Source. La descargamos una sola vez,
   la dejamos en `assets/fonts/`, y la cargamos solo cuando dibujamos el
   titular. Para el kicker y la marca usamos Arial bold del sistema."

6. "Cómo se acomoda el titular: la función `_draw_magazine_block` calcula
   primero cuánto espacio ocupan las líneas a un tamaño grande, después
   resta para arriba desde la base, y pone el kicker justo encima sin pisarlo.
   Si el titular se agranda, el kicker sube. Si se achica, baja."

7. "El fondo se renderiza más oscuro en la mitad inferior con un gradiente
   suave, para que el titular blanco se lea sí o sí, no importa qué color
   haya generado la IA."

8. "Y un detalle de seguridad operativa: si la llamada a gpt-image-1 falla,
   `create_fallback_background` arma un gradiente cinematográfico con
   Pillow puro. Nunca te quedás sin imagen."

### 🖥️ Apoyos en pantalla

1. Diapositiva dividida en dos: "IA: pinta escenas, no sabe escribir" /
   "Pillow: escribe perfecto, no sabe imaginar".
2. Editor en `build_image_prompt`, resaltar dónde se inyecta `image_concept`
   y las prohibiciones explícitas (no text, no logos, no boxes).
3. Editor en `editorial_enrich` mostrando que `image_concept` viene del LLM.
4. Carpeta `assets/fonts/` abierta, archivo `Anton-Regular.ttf` listado.
5. Editor en `load_font` mostrando la branch `display=True` y los paths.
6. Editor en `_draw_magazine_block` con marcadores en el cálculo del kicker
   y del título.
7. Editor en `_draw_bottom_gradient`, mostrar la línea por línea con alpha
   creciente.
8. Editor en `create_fallback_background`, comparándolo con `compose_instagram_image`
   para que se vea el plan B.

### ✅ Checkpoint

- Al correr `RADAR_MODE=content`, el alumno recibe en Telegram una imagen
  1080×1080 con titular en Anton, kicker y marca personal.
- El alumno puede cambiar `PERSONAL_BRAND` y `APP_NAME` en el archivo y ver
  el cambio reflejado.
- El alumno puede cambiar una palabra del `image_concept` (manualmente en
  el JSON cacheado) y ver una imagen distinta al siguiente run.

### ⚠️ Errores comunes

- Subir el `start_size` del titular demasiado y que no entre. La fuente Anton
  es condensada, pero hay un límite. Si pasa, ajustar `start_size` o
  `min_size`.
- Olvidar `display=True` al llamar a `fit_wrapped_title` para el titular y
  obtener Arial en vez de Anton.
- El alumno cambia el `image_concept` pero no se renderiza porque el cache
  de `selected_release.json` todavía tiene el viejo. Solución: borrar el
  archivo y volver a correr brief.

---

## Módulo 6 — Entrega a Telegram

### 🎯 Objetivo

Conectar la generación con la entrega. Mensajes de texto, imágenes y
manejo de errores de envío.

### ⏱️ Duración

15 min.

### 🧠 Concepto clave

> "Telegram es la cara del agente. Una llamada HTTP simple, pero con
> manejo de errores que te ahorra dolores de cabeza."

### 🎬 Guion

1. "Telegram es lo más fácil de toda la app. Dos endpoints: sendMessage para
   texto y sendPhoto para imágenes. Los dos son POST a una URL armada con
   tu token."

2. "Una sutileza: Telegram tiene límite de 4096 caracteres por mensaje.
   Como el guion multi-formato más el reporte editorial puede pasarse, la
   función parte el mensaje en chunks de 4000 caracteres y los manda en
   secuencia."

3. "Para enviar la imagen, abrimos el archivo en modo binario y lo pasamos
   en el campo `files` del POST, con un caption corto."

4. "Si el envío de imagen falla por cualquier motivo, no rompemos el flujo:
   probamos mandar un mensaje de texto que diga 'no se pudo enviar la
   imagen' con el error. Operacionalmente, eso te avisa sin frenarte."

5. "Y al final de toda la corrida hay un try/except que cubre cualquier
   excepción no manejada. Si algo explota, te llega a Telegram un mensaje
   con la última parte del traceback. Antes era silencio, ahora sabés."

### 🖥️ Apoyos en pantalla

1. Editor en `send_to_telegram`, mostrando el corte de chunks.
2. Editor en `send_telegram_photo`, mostrando el upload binario.
3. Editor en el bloque dentro de `run_radar` que llama a
   `send_telegram_photo` con su `try/except` interno.
4. Editor en `notify_failure_to_telegram`, resaltar cómo se compone el
   mensaje de fallo.
5. Editor en `if __name__ == "__main__"` con el wrap try/except final.

### ✅ Checkpoint

- El alumno recibe brief y content en Telegram sin errores.
- El alumno simula un fallo (por ejemplo, corrompe el `TELEGRAM_CHAT_ID`
  temporalmente) y ve cómo el mensaje de alerta llega o cómo aparece en
  consola si Telegram mismo es el problema.

### ⚠️ Errores comunes

- Caption muy largo en `sendPhoto`: Telegram lo trunca a 1024 caracteres.
  Mantener captions cortos.
- Foto demasiado grande: Telegram acepta hasta 10 MB. Como `gpt-image-1` a
  1024×1024 da archivos chicos, no es problema aquí, pero conviene mencionar.

---

## Módulo 7 — Automatización con GitHub Actions

### 🎯 Objetivo

Que el alumno entienda cómo el cron diario, los secrets y el cache trabajan
juntos para que la app corra sola.

### ⏱️ Duración

25 min.

### 🧠 Concepto clave

> "GitHub Actions es tu servidor gratis. Dos workflows, dos crones, dos
> caches, y la app corre todos los días sin que toques nada."

### 🎬 Guion

1. "Hasta acá todo corre en tu compu. Ahora viene la parte mágica: que la
   app corra en la nube de GitHub, sin que vos hagas nada, todos los días."

2. "Vamos a tener dos workflows. `radar-brief.yml` corre cada mañana a las
   doce UTC y manda el Top 3 a Telegram. `radar-content.yml` corre diez
   minutos después y arma el contenido del número uno por defecto, o el
   número que vos hayas pedido por Telegram."

3. "Los dos workflows necesitan tus claves. En vez de subirlas al repo, las
   guardamos en Settings → Secrets and variables → Actions. Ahí ponés
   `OPENAI_API_KEY`, `TELEGRAM_BOT_TOKEN` y `TELEGRAM_CHAT_ID`. El workflow
   las inyecta como variables de entorno cuando corre."

4. "El brief escribe varios archivos: `selected_release.json` con el Top 3,
   `history_brief.json` con los links ya vistos, y `published_log.json` con
   los titulares destacados. Esos archivos no viven en el repo. Se guardan
   en el cache de GitHub Actions, con keys que incluyen la fecha y el
   `run_id` para que cada corrida sobrescriba la anterior."

5. "Cuando arranca el content workflow, restaura esos caches con
   `restore-keys` rolling: pide su propio run_id, no lo encuentra, cae al
   patrón prefijo y agarra el cache más reciente del día. Así siempre lee
   el último Top 3, incluso si corriste el brief tres veces."

6. "Y el detalle clave para que el botón de Telegram funcione: el content
   ya no usa `fail-on-cache-miss: true`. Si por algún motivo no hay cache,
   el script reconstruye el Top 3 sobre la marcha y manda contenido igual."

7. "Probarlo es directo: en GitHub Actions, click en el workflow, Run
   workflow, y elegís la rama. Si todo está bien, en menos de dos minutos te
   llega a Telegram."

### 🖥️ Apoyos en pantalla

1. Navegador en GitHub, pestaña Actions del repo, mostrando los dos
   workflows listados.
2. Editor en `.github/workflows/radar-brief.yml`, scroll de arriba a abajo
   marcando cron, env vars y steps.
3. Captura `gh-actions-secrets.png` o navegador en Settings → Secrets
   mostrando los tres secrets con sus nombres (sin revelar valores).
4. Editor con los dos archivos `.yml` abiertos lado a lado, comparando
   las claves del cache de `selected_release` y `published_log`.
5. Comentario destacado en el `.yml` de content sobre por qué se quitó
   `fail-on-cache-miss`.
6. Navegador disparando un Run workflow manual desde la UI de GitHub.
7. Telegram mostrando el mensaje recibido a los pocos segundos.

### ✅ Checkpoint

- El alumno corrió manualmente el workflow `radar-brief.yml` desde la UI
  y recibió el Top 3 en Telegram.
- El alumno corrió manualmente `radar-content.yml` con choice 1 y recibió
  contenido + imagen.
- El cron está activo y la próxima ejecución se ve programada en la UI.

### ⚠️ Errores comunes

- Olvidar agregar los secrets antes del primer run: el workflow falla con
  `ValueError: Falta OPENAI_API_KEY`. Pedíles que revisen la sección
  Secrets antes de disparar nada.
- Crear secrets en "Codespaces" o "Dependabot" en vez de "Actions". Tienen
  scopes distintos. Solo Actions sirve para los workflows.
- Cron expresado en hora local en vez de UTC. Repetir que el cron de GH
  es UTC siempre.

---

## Módulo 8 — Selección interactiva con Cloudflare Worker

### 🎯 Objetivo

Que el alumno entienda por qué necesitamos un Worker y cómo desplegarlo
para que el "1", "2", "3" en Telegram dispare contenido.

### ⏱️ Duración

25 min.

### 🧠 Concepto clave

> "Telegram no puede llamar directamente a GitHub Actions. Necesitamos un
> intermediario diminuto que reciba mensajes y dispare workflows. El
> Worker es justo eso."

### 🎬 Guion

1. "Hasta acá, vos para forzar un contenido tenés que ir a GitHub y darle
   Run workflow a mano. Queremos algo más simple: que el alumno escriba un
   número en Telegram y el sistema entienda."

2. "Telegram tiene webhooks: cuando llega un mensaje al bot, Telegram hace
   un POST a la URL que vos le digas. Necesitamos una URL pública,
   gratuita, que viva siempre. Cloudflare Workers es perfecto."

3. "El Worker es un JavaScript de unas treinta líneas. Recibe el mensaje,
   verifica que diga uno, dos o tres, contesta al usuario para confirmar y
   llama a la API de GitHub para disparar el workflow de content con ese
   choice."

4. "Necesita tres secrets en Cloudflare: el token de Telegram para
   responder, un Personal Access Token de GitHub con permiso de workflow,
   y los identificadores del repo. Esos secrets se configuran en el
   dashboard del Worker, no en el código."

5. "Una vez deployado, registrás la URL del Worker como webhook del bot
   con un curl simple. A partir de ahí, cualquier 'uno', 'dos' o 'tres'
   en el chat del bot dispara contenido."

6. "Yo recomiendo arrancar con el Worker después de que ya tenés el cron
   funcionando. Primero confiá en la automatización, después agregás
   interactividad."

### 🖥️ Apoyos en pantalla

1. Diapositiva con flujo: Telegram → Cloudflare Worker → GitHub Actions →
   Telegram (de vuelta con el contenido).
2. Dashboard de Cloudflare → Workers, mostrando el botón Create a Worker.
3. Editor con el código del Worker, comentado por bloque:
   - parseo del mensaje
   - reply de confirmación al usuario
   - llamada a `workflow_dispatch` con `choice` en el body
4. Cloudflare → Worker → Settings → Variables, mostrando los nombres de
   los cuatro secrets (sin valores).
5. Terminal con el `curl` para registrar el webhook:
   `https://api.telegram.org/bot<token>/setWebhook?url=<worker_url>`
6. Diagrama de bloques con un "1" entrando por Telegram y el contenido
   llegando minutos después.

### ✅ Checkpoint

- Worker deployado, URL pública accesible.
- Webhook registrado en Telegram (verificable con `getWebhookInfo`).
- Escribir `1` en el bot dispara un Run en GitHub Actions.
- El alumno recibe el contenido del número uno en su Telegram.

### ⚠️ Errores comunes

- Personal Access Token sin permiso `workflow`. El dispatch devuelve 404
  silencioso. Hay que crear un fine-grained token y darle ese scope.
- Confundir webhook con polling. Si el bot ya tenía polling activo, el
  webhook no recibe nada. Hay que llamar `deleteWebhook` para empezar
  limpio.
- URL del Worker con `http://` en vez de `https://`. Telegram solo acepta
  HTTPS para webhooks.

---

## Módulo 9 — Operación, memoria editorial y monitoreo

### 🎯 Objetivo

Que el alumno entienda cómo el sistema evoluciona día a día sin repetirse
y cómo se entera cuando algo se rompe.

### ⏱️ Duración

15 min.

### 🧠 Concepto clave

> "Una vez en producción, lo que importa es la operación. Memoria, fallos
> visibles, y la disciplina de no tocar lo que funciona."

### 🎬 Guion

1. "Cada vez que el sistema publica un Top 3, los titulares quedan
   registrados en `published_log.json` con fecha y proveedor. Al día
   siguiente, ese log se le pasa al editor LLM como contexto."

2. "El editor entonces sabe: 'OpenAI ya salió ayer y antier'. Y prefiere
   hoy a Anthropic si tiene algo sólido. Esto diversifica el feed sin que
   vos lo pidas explícitamente."

3. "El log se trimea a treinta días para que no crezca para siempre. El
   editor mira los últimos siete días por defecto."

4. "El otro pilar operacional es la alerta de fallo. Si cualquier corrida
   levanta una excepción que nadie atrapa, `notify_failure_to_telegram` te
   manda el tipo de error, el mensaje y las últimas seis líneas del
   traceback. Después relanza la excepción para que el job aparezca en
   rojo en GitHub Actions. No silenciamos."

5. "Y el monitoreo del día a día se hace en GitHub Actions. Cada corrida
   queda registrada, con su log completo. Si te llega una alerta, abrís
   ese run y mirás qué pasó."

6. "Mi recomendación: cuando algo falle, mirá primero los logs. Después
   reproducí local con `TEST_MODE=1`. Y solo después tocá producción."

### 🖥️ Apoyos en pantalla

1. Editor en `published_log.json` con varios días de ejemplo.
2. Editor en `recent_published_summaries` y dónde se inyecta al prompt.
3. Editor en `notify_failure_to_telegram` con el formato del mensaje de
   alerta.
4. Captura de un mensaje de error en Telegram, real o simulado.
5. GitHub Actions con un run en rojo, abierto en el step que falló.
6. Diapositiva con el ciclo: alerta → log → reproducción local → fix → push.

### ✅ Checkpoint

- El alumno ve `published_log.json` con entradas de su uso real.
- El alumno simula un fallo (cambiando temporalmente el modelo de OpenAI
  a uno inexistente) y recibe la alerta en Telegram.
- El alumno encuentra el log del fallo en GitHub Actions.

### ⚠️ Errores comunes

- Confundir `history_brief.json` con `published_log.json`. El primero es
  para anti-duplicado por link; el segundo es para contexto editorial.
- Editar el `published_log.json` a mano y romper el JSON. Si el archivo
  es inválido, el sistema lo trata como vacío y sigue. Mostralo.

---

## Módulo 10 — Cierre, costos y próximos pasos

### 🎯 Objetivo

Que el alumno cierre con claridad mental, sepa cuánto cuesta operarlo y
qué puede agregarle por su cuenta.

### ⏱️ Duración

8 min.

### 🧠 Concepto clave

> "Tu agente ya existe. Lo que hagas con él de acá en adelante define si
> es un proyecto o un sistema."

### 🎬 Guion

1. "Recapitulando: pescamos releases de fuentes diversas, los puntuamos,
   los pasamos por un editor LLM que decide y redacta, generamos una
   portada cinematográfica y entregamos todo a Telegram. Y vos podés
   pedir contenido escribiendo un número."

2. "Los costos: GitHub Actions gratis hasta dos mil minutos al mes, te
   sobra. Cloudflare Workers gratis. Telegram gratis. OpenAI te va a
   cobrar centavos al día: una llamada de gpt-5-mini para editor, otra
   para contenido, y una imagen de gpt-image-1. Calculá unos dos a tres
   dólares mensuales en uso intenso."

3. "Lo que podés agregar por tu cuenta, sin pedirme permiso: agregar
   más fuentes editoriales que vos uses; cambiar `APP_NAME` y
   `PERSONAL_BRAND` a tu marca real; meter más formatos de contenido,
   como un script de podcast o un email newsletter; postear automático a
   LinkedIn o Instagram, aunque eso requiere meterse con APIs de Meta."

4. "Lo que no te recomiendo tocar al principio: la lógica de cache. Es
   delicada y un cambio sutil rompe el flujo entre brief y content."

5. "Y un consejo final: usá el sistema. Lo que mata estos proyectos no
   es la falta de features, es no usarlos. Si lo usás dos semanas
   seguidas, vas a saber exactamente qué le falta. Y ese feedback es
   oro."

### 🖥️ Apoyos en pantalla

1. Diapositiva con los cinco bloques arquitectónicos uno al lado del
   otro, marcados con un check.
2. Diapositiva con tabla de costos: cada servicio + costo mensual
   estimado + total.
3. Diapositiva con tres bullets de "qué agregarle":
   - más fuentes
   - más formatos
   - publicación directa
4. Diapositiva con un check rojo grande sobre "tocar el cache de
   workflows" como cosa a evitar al principio.
5. Diapositiva final con tu marca y CTA del curso.

### ✅ Checkpoint

- El alumno tiene NotiAgente Hered-IA corriendo en su propia
  infraestructura, con su marca.
- El alumno sabe a quién pedirle ayuda (vos) y dónde están los logs
  cuando algo falla.

### ⚠️ Errores comunes

- Querer publicar el curso sin haberlo usado al menos dos semanas:
  insistí en que el aprendizaje real viene del uso real.

---

## Anexo A — Cheatsheet de comandos

```bash
# Setup local
git clone <url-de-tu-repo> ai-trend-agent
cd ai-trend-agent
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
# editar .env con tus claves

# Correr en modo prueba
TEST_MODE=1 RADAR_MODE=brief python daily_brief.py
TEST_MODE=1 RADAR_MODE=content python daily_brief.py

# Correr en modo real (con feeds en vivo)
RADAR_MODE=brief python daily_brief.py
RADAR_MODE=content python daily_brief.py

# Disparar workflows manualmente desde la línea de comandos
gh workflow run radar-brief.yml --ref main
gh workflow run radar-content.yml --ref main -f choice=1

# Telegram: registrar y verificar webhook
curl "https://api.telegram.org/bot<TOKEN>/setWebhook?url=<WORKER_URL>"
curl "https://api.telegram.org/bot<TOKEN>/getWebhookInfo"
curl "https://api.telegram.org/bot<TOKEN>/deleteWebhook"
```

## Anexo B — Variables de entorno

| Variable | Quién la usa | Dónde se configura |
|---|---|---|
| `OPENAI_API_KEY` | editor LLM, generador de contenido, generador de imagen | `.env` local + GitHub Secrets |
| `TELEGRAM_BOT_TOKEN` | envío de mensajes y fotos al bot | `.env` local + GitHub Secrets + Cloudflare Worker |
| `TELEGRAM_CHAT_ID` | destino al que escribe el bot | `.env` local + GitHub Secrets |
| `RADAR_MODE` | switch entre brief y content | inline en el comando, o en el env del workflow |
| `SELECT_CHOICE` | número 1/2/3 desde el Worker | input del workflow, vía Cloudflare |
| `TEST_MODE` | activa artículos falsos | inline en el comando, solo local |
| `GITHUB_TOKEN` | Worker dispara workflows | secret en Cloudflare Worker |
| `GITHUB_OWNER`, `GITHUB_REPO`, `GITHUB_REF` | identifican el repo y la rama | secret en Cloudflare Worker |

## Anexo C — Estimación de costos mensuales (uso diario)

| Servicio | Costo |
|---|---|
| GitHub Actions (dos workflows diarios) | $0 (dentro del free tier) |
| Cloudflare Workers (uno) | $0 (dentro del free tier) |
| Telegram Bot API | $0 |
| OpenAI gpt-5-mini (editor + contenido) | ~$0.50 al mes |
| OpenAI gpt-image-1 (una imagen al día, calidad high) | ~$2.10 al mes |
| **Total estimado** | **~$2.60 al mes** |

## Anexo D — Troubleshooting express

| Síntoma | Causa probable | Fix |
|---|---|---|
| "No hay lanzamientos que valga la pena publicar hoy" | pool vacío después de filtro | revisar logs `brief: articulos crudos=...` |
| Imagen con texto sin sentido | el editor confundió campos | revisar prompt y schema del JSON |
| Mensaje no llega a Telegram | chat_id mal o bot no recibió primer mensaje | abrir chat con el bot y enviarle "hola" |
| Workflow falla en `Restore selected release cache` | clave de cache mal configurada | revisar `restore-keys` en el `.yml` |
| Alumno escribe "1" y no llega contenido | Worker apunta a una rama sin código actualizado | verificar `GITHUB_REF` en Worker, mergear a main |
| Cron no dispara | timezone mal interpretado | recordar que GH Actions usa UTC, no local |

---

## Cierre

Este documento es una base. Adaptalo a tu tono, recortá los módulos que
sientas largos, agregá los detalles que descubras grabando. Lo importante es
que el alumno termine con NotiAgente Hered-IA corriendo en su propio Telegram,
con su propia marca, y entendiendo cada pieza.

Si querés podemos iterarlo: cada vez que grabes un módulo, contame qué
funcionó y qué no, y ajustamos la guía para los siguientes.
