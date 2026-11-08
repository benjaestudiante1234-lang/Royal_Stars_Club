# Royal Star’s Club — sitio web

Sitio estático de Royal Star’s Club preparado para GitHub Pages. Incluye la página principal y tres páginas independientes: **Liga de Royal** (Vue 3), **Novedades** y **Cronograma**.

## Estructura del proyecto

```text
Royal_Stars_Club/
├── index.html                 # Página principal
├── liga.html                  # Página independiente de Liga (Vue 3)
├── novedades.html             # Listado público de noticias
├── noticia-duelo-hermanas-lorenzo.html # Crónica editorial de la primera fecha
├── cronograma.html            # Horarios y calendario de actividades
├── assets/
│   ├── css/
│   │   ├── main.css           # Estilos de la página principal
│   │   ├── liga.css           # Estilos de la página de Liga
│   │   └── portal.css         # Estilos de Novedades y Cronograma
│   ├── js/
│   │   ├── main.js            # Menú, calendario de inicio y funciones generales
│   │   ├── liga.js            # Vue 3: categorías, búsqueda y preguntas
│   │   ├── novedades.js       # Filtros, lectura, carga, importación y exportación de noticias
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
- `novedades.html`: página independiente de noticias. Desde el menú principal se abre en una pestaña nueva. Permite filtrar, buscar y leer noticias publicadas en el archivo `assets/data/novedades.json`. La crónica “Duelo de hermanas: Lorenzo vs. Lorenzo” abre su propia página editorial (`noticia-duelo-hermanas-lorenzo.html`). No muestra controles de carga en la página pública.
- `cronograma.html`: página independiente con la grilla de horarios y un calendario mensual interactivo. Desde el menú principal se abre en una pestaña nueva.

## Cómo publicar o actualizar noticias

La página pública `novedades.html` es de solo lectura: no contiene un formulario de carga ni un panel de administración visible. Para agregar o modificar una noticia, editá `assets/data/novedades.json` en el repositorio. Cada publicación usa los campos `id`, `title`, `category`, `date`, `summary`, `content`, `image` (opcional) y `url` (opcional, para abrir una página editorial propia). En `image` podés indicar una ruta relativa dentro de `assets/img/`. Después guardá los cambios y subilos a GitHub (`git add .`, `git commit -m "Actualizar novedades"`, `git push`). GitHub Pages actualizará la página pública al publicar el nuevo commit.

Esta versión HTML estática no tiene autenticación ni base de datos; la administración online desde un panel privado requiere un backend (por ejemplo, Django).

## Cómo probarlo localmente

1. Descargá o cloná el repositorio.
2. Abrí `index.html` con un navegador moderno (Chrome, Edge o Firefox).
3. Para revisar todas las páginas, abrí también `liga.html`, `novedades.html`, `noticia-duelo-hermanas-lorenzo.html` y `cronograma.html`.

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

- Los accesos a Novedades, Blog, Liga y Cronograma se abren en pestañas nuevas.
- El bloque grande de información de Liga no está en la página principal; se conserva su página independiente. La página Novedades no muestra el panel de carga de noticias.
- El cronograma mantiene los horarios como referencia y no confirma cupos o turnos.
- El calendario incluye la fecha de inicio de Liga informada para el 6 de noviembre de 2026.
- Los enlaces e imágenes usan rutas relativas para que el sitio funcione al desplegarlo en GitHub Pages.
