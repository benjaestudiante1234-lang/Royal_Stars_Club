# Royal Star’s Club — sitio web

Sitio estático de Royal Star’s Club preparado para GitHub Pages. Incluye la página principal y páginas independientes para **Liga de Royal** (Vue 3), **Blog**, **Noticias** y **Cronograma**.

## Estructura del proyecto

```text
Royal_Stars_Club/
├── index.html                 # Página principal
├── liga.html                  # Página independiente de Liga (Vue 3)
├── blog.html                  # Artículos y experiencias del club
├── novedades.html             # Listado público de noticias
├── noticia-duelo-hermanas-lorenzo.html # Crónica editorial de la primera fecha
├── cronograma.html            # Horarios y calendario de actividades
├── assets/
│   ├── css/
│   │   ├── main.css           # Estilos de la página principal
│   │   ├── gallery.css        # Estilos de la galería
│   │   ├── liga.css           # Estilos de la página de Liga
│   │   └── portal.css         # Estilos de Blog, Noticias y Cronograma
│   ├── js/
│   │   ├── main.js            # Menú, calendario de inicio y funciones generales
│   │   ├── gallery.js         # Filtros, visor de fotos y reproductores de video
│   │   ├── liga.js            # Vue 3: categorías, búsqueda y preguntas
│   │   ├── novedades.js       # Filtros, lectura y carga de Blog y Noticias
│   │   └── cronograma.js      # Calendario interactivo
│   ├── data/
│   │   └── novedades.json     # Noticias publicadas para el sitio
│   └── img/                   # Logo, favicon, fondo y sponsors
├── README.md
└── .gitignore
```

## Páginas

- `index.html`: inicio, academia, cursos, liga destacada, horarios, calendario, preguntas frecuentes y contacto.
- `liga.html`: página de Liga de Royal desarrollada con Vue 3.
- `blog.html`: página independiente para artículos y experiencias del club. Muestra únicamente publicaciones con la categoría `Blog` en `assets/data/novedades.json`.
- `novedades.html`: página independiente de noticias. Desde el menú principal se abre en una pestaña nueva. Permite filtrar, buscar y leer noticias publicadas en el archivo `assets/data/novedades.json`. La crónica “Duelo de hermanas: Lorenzo vs. Lorenzo” abre su propia página editorial (`noticia-duelo-hermanas-lorenzo.html`). No muestra controles de carga en la página pública.
- `cronograma.html`: página independiente con la grilla de horarios y un calendario mensual interactivo. Desde el menú principal se abre en una pestaña nueva.

## Cómo publicar o actualizar noticias

Las páginas públicas `blog.html` y `novedades.html` son de solo lectura: no contienen formularios de carga ni paneles de administración visibles. Para agregar o modificar una noticia o artículo, editá `assets/data/novedades.json` en el repositorio. Cada publicación usa los campos `id`, `title`, `category`, `date`, `summary`, `content`, `image` (opcional) y `url` (opcional, para abrir una página editorial propia). Usá `Blog` para que una publicación aparezca en el Blog; las demás categorías se muestran en Noticias. En `image` podés indicar una ruta relativa dentro de `assets/img/`. Después guardá los cambios y subilos a GitHub (`git add .`, `git commit -m "Actualizar novedades"`, `git push`). GitHub Pages actualizará la página pública al publicar el nuevo commit.

Esta versión HTML estática no tiene autenticación ni base de datos; la administración online desde un panel privado requiere un backend (por ejemplo, Django).

## Cómo actualizar la galería

La sección Galería se alimenta desde `assets/data/galeria.json`. Los elementos pueden ser fotografías, videos de YouTube o archivos MP4 locales. Las fotografías se guardan preferentemente en `assets/img/galeria/` y los videos MP4 en `assets/videos/`.

Ejemplo de fotografía:

```json
{
  "type": "image",
  "category": "Canchas",
  "title": "Cancha principal",
  "alt": "Cancha principal de Royal Star's Club",
  "src": "assets/img/galeria/cancha-principal.jpg"
}
```

Ejemplo de video de YouTube:

```json
{
  "type": "youtube",
  "category": "Entrenamientos",
  "title": "Trabajo técnico",
  "youtubeId": "ID_DEL_VIDEO",
  "thumbnail": "assets/img/galeria/entrenamiento.jpg"
}
```

Ejemplo de video MP4:

```json
{
  "type": "video",
  "category": "Eventos",
  "title": "Evento del club",
  "src": "assets/videos/evento.mp4",
  "poster": "assets/img/galeria/evento.jpg"
}
```

Por el momento, la interfaz muestra `Todas`, `Torneos y competencias` y `Eventos`. La estructura continúa preparada para futuras categorías, que pueden volver a mostrarse agregando su botón en `index.html`.

Torneos y competencias incluye subfiltros por fecha: `Viernes 06` y `Viernes 13`. Las fotos se encuentran organizadas en `assets/img/galeria/torneos-06/` y `assets/img/galeria/torneos-13/`. Para agregar otra fecha, creá una carpeta nueva, agregá el elemento `date` al JSON y añadí el botón correspondiente en `galleryDateFilters`.

## Cómo probarlo localmente

1. Descargá o cloná el repositorio.
2. Abrí `index.html` con un navegador moderno (Chrome, Edge o Firefox).
3. Para revisar todas las páginas, abrí también `liga.html`, `blog.html`, `novedades.html`, `noticia-duelo-hermanas-lorenzo.html` y `cronograma.html`.

No requiere Node.js, npm, Python ni Django. Se necesita conexión a Internet para cargar Bootstrap, Font Awesome, Vue 3 y Google Fonts desde sus CDN.

## Subir el proyecto a GitHub

Primero creá un repositorio vacío en GitHub. Luego abrí una terminal dentro de la carpeta `Royal_Stars_Club` y ejecutá:

```bash
git init
git add .
git commit -m "Publicar sitio Royal Star's Club"
git branch -M main
git remote add origin https://github.com/TU-USUARIO/TU-REPOSITORIO.git
git push -u origin main
```

Reemplazá `TU-USUARIO` y `TU-REPOSITORIO` por los datos de tu repositorio.

## Publicarlo con GitHub Pages

Como `index.html` está en la raíz del proyecto, activá GitHub Pages desde **Settings → Pages** del repositorio y seleccioná la rama `main` y la carpeta `/ (root)`.

## Notas

- Los accesos a Blog, Noticias, Liga y Cronograma se abren en pestañas nuevas.
- El bloque grande de información de Liga no está en la página principal; se conserva su página independiente. Las páginas de Blog y Noticias son públicas y no muestran paneles de carga.
- El cronograma mantiene los horarios como referencia y no confirma cupos o turnos.
- El calendario incluye la fecha de inicio de Liga informada para el 6 de noviembre de 2026.
- Los enlaces e imágenes usan rutas relativas para que el sitio funcione al desplegarlo en GitHub Pages.
