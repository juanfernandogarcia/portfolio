# Portfolio Químico Digital — instrucciones del proyecto

Portafolio de Juan Fernando García Navas. Fuente editable en la raíz
(`*.dc.html`), sitio publicado en `site/` (GitHub Pages). Diseño: sistema
Modernist, amarillo `#ffd100` sobre tinta `#201e1d`, sin esquinas
redondeadas, reglas de 2px. Tres idiomas: EN / FR / ES.

---

## SKILL: NUEVO PROYECTO / MODIFICAR PROYECTO

Cuando el usuario escriba **NUEVO PROYECTO** o **MODIFICAR PROYECTO** y
adjunte contexto, texto, PDF, fotos o archivos, sigue este procedimiento
sin pedir confirmación de la estructura (ya está decidida).

### 1. Analizar el material

Lee todo lo aportado y extrae:

- Título, institución, año, duración.
- Una o dos frases de resumen (`lede`).
- Dos cifras clave (`kpiN1`/`kpi1`, `kpiN2`/`kpi2`) — magnitudes reales del
  proyecto: eficiencia, presupuesto, caudal, número de ensayos.
- Herramientas y software (`tool1..4`).
- Habilidades (`sk1..sk10`).
- El resultado en una frase (`closeT`).
- Lo que le dejó el proyecto, en cuatro bloques de tres puntos:
  técnico/académico, gestión y costos, liderazgo y comunicación,
  adaptación y resolución de problemas (`d1a..d4c`).

Texto que dé el usuario: **va literal**, solo formateado. Texto que
escribas tú: claro, concreto, sin adjetivos de relleno. Si falta un dato
duro, pregúntalo; no lo inventes.

### 2. Crear el archivo

`Project 05 New Project.dc.html` es la plantilla en blanco con TODO ya
cableado (galerías, video, swipe, compartir, tres idiomas). Para un
proyecto nuevo:

1. `copy_files` de `Project 05 New Project.dc.html` a
   `Project 0N <Nombre>.dc.html`.
2. Cambia `const SLUG = "p05"` por un slug único corto (`p06`, `pmet`…).
3. Renombra los ids de todos los `image-slot`: `p05-hero` → `<slug>-hero`,
   `p05-a1..a8` → `<slug>-a1..a8`, `p05-g1..g8` → `<slug>-g1..g8`.
4. Rellena los tres diccionarios de `const T` (en, fr, es). Traduce; no
   dejes inglés en las claves de fr/es.
5. Ajusta `NEIGH` (proyecto anterior/siguiente) en el nuevo archivo y en
   los vecinos, y añade la tarjeta en `Portfolio.dc.html`.

Para MODIFICAR: edita solo lo que pida. Nunca toques layout, colores ni
tipografía si el encargo es de contenido.

### 3. Estructura de la página (no cambiarla)

1. Barra superior: volver, contacto, compartir, selector de idioma
2. Hero (`<slug>-hero`)
3. Cabecera amarilla: kicker, título, `lede`, tres chips de metadatos
4. Dos KPIs + índice de las 7 secciones
5. Herramientas y habilidades
6. `01 Context` → `07 Skills developed`, con las dos galerías
   intercaladas (A tras la sección 02, B tras la 03)
7. Cierre (`closeK`/`closeT`), siguiente proyecto, contacto, pie

### 4. Galerías — obligatorio

Toda galería que añadas lleva, **por defecto y desde el primer momento**,
la barra de edición completa dentro de un contenedor con
`data-editor-only=""`:

`＋ Foto`, `＋ Video`, `✕ Quitar`, `◀ Izquierda`, `Derecha ▶`

Ocho huecos de foto (`<slug>-a1..a8`) y cuatro de video
(`<slug>-a-v1..v4`) por galería. Los botones de reubicar mueven fotos,
videos y también el recuadro vacío de video, para poder fijar la posición
del video antes de tener el archivo. Esa barra solo desaparece en la
exportación, que la elimina automáticamente por su marca
`data-editor-only`. Nunca la quites a mano ni la omitas al crear una
galería.

Comportamiento ya implementado, no rehacerlo: swipe estilo Instagram
(un gesto = una foto, se decide al soltar, resistencia en los extremos),
gesto horizontal de trackpad, video ajustado con `object-fit:contain`
sobre negro y controles nativos, autoplay al llegar y pausa al salir
conservando el punto.

### 5. Exportar a `site/`

Regenera **las seis páginas juntas** (una parcial pierde fotos). Pasos
por página, con `run_script`:

1. Eliminar todo elemento con `data-editor-only=""` (recorrido con
   contador de anidamiento, no regex).
2. Quitar el atributo `data-editor-hint=""`.
3. `editor = true; // stripped to false by the site build` → `editor = false;`
4. Reescribir enlaces: `Portfolio.dc.html` → `index.html`,
   `Project%20NN%20....dc.html` → `project-NN.html`.
5. Volcar cada imagen de `.image-slots.state.json` a
   `site/media/<slug>/<id>.<ext>` (subcarpeta por proyecto) y poner
   `src="media/<slug>/<id>.<ext>"` en su `image-slot`. Las imágenes del
   propio `Portfolio.dc.html` (retrato, tarjetas de proyecto) siguen en
   `site/media/` sin subcarpeta.
6. Hornear el orden de galería como `DEFAULT_ORDER` dentro de
   `storedOrder()` — el orden vive en localStorage del navegador y sin
   esto el sitio publicado no lo tiene. Lee el orden real con
   `eval_js_user_view` sobre `localStorage['jfg-gal-order']`.
7. Solo en `index.html`: añadir el preload del retrato.

Después, `present_fs_item_for_download` de la carpeta `site`.

### 6. Videos

No se suben desde el navegador: son archivos en `site/media/<slug>/` (una
subcarpeta por proyecto) con nombre exacto `<slug>-a-v1.mp4` …
`<slug>-b-v4.mp4`. MP4 H.264 + AAC, menos de 50 MB.
`site/media/LEEME-VIDEOS.txt` documenta las rutas y nombres de todas las
páginas; actualízalo al crear un proyecto.

---

## Reglas generales

- Responde en español.
- **Nunca uses el símbolo «—» (guion largo) en ningún texto del portafolio.** Usa
  comas, dos puntos, paréntesis o punto y seguido.
- Cambios pequeños: cambia solo eso.
- Tras editar cualquier `.dc.html`, regenera `site/` y ofrece la descarga.
- Fotos: solo el usuario las coloca, arrastrándolas a los huecos.
- No puedo generar imágenes; los recuadros vacíos son para sus fotos.
