# KODO — Sitio web

Sitio estático del estudio KODO. HTML/CSS/JS puros, sin build, sin dependencias.

## Estructura

```
.
├── index.html              ← todo el sitio (single-page)
├── assets/
│   ├── kodo-logo.png       ← logo (favicon + nav + footer)
│   └── proyectos/          ← imágenes de proyectos
│       ├── casa-piloto-01-render.jpg ... 05
│       ├── casa-costanera-01-render.jpg ... 05 (archivo anterior)
│       └── casa-costanera/ ← ficha editorial, planta y registro previo
├── .nojekyll               ← desactiva Jekyll en GitHub Pages
├── .gitignore
└── README.md
```

## Cómo subirlo a GitHub Pages (paso a paso)

**Importante:** los archivos del zip ya están en la raíz. Subí el CONTENIDO del zip al repo, no la carpeta `kodo-website` entera.

1. Crear un repo nuevo en GitHub. Ej: `kodo-web` (cualquier nombre que te guste).
2. En el repo, **Add file → Upload files**.
3. Descomprimí el zip en tu compu y arrastrá TODOS los archivos y carpetas (`index.html`, `assets/`, `.nojekyll`, etc.) a la zona de upload de GitHub. **No subas la carpeta entera; subí su contenido.**
4. Hacé commit ("Initial commit").
5. **Settings → Pages → Source:** elegí *Deploy from a branch* → branch `main` → folder `/ (root)`. Guardá.
6. Esperá 1–2 minutos. Tu sitio queda en `https://TU-USUARIO.github.io/NOMBRE-DEL-REPO/`.

### Si ya tenés un repo y te aparece la página rota

Si ya creaste el repo (ej. `KODOO`) y al entrar al link ves texto raro tipo `.DS_Store Thumbs.db *.log node_modules/`, es porque GitHub está sirviendo el `.gitignore` en lugar del sitio. Eso pasa cuando no hay un `index.html` en la raíz del repo. Solución:

1. Borrá todos los archivos del repo (Code → cada archivo → trash icon → commit).
2. Volvé a subir el contenido del zip nuevo, asegurándote de que `index.html` quede en la raíz (no dentro de una subcarpeta).
3. Esperá 1–2 minutos y refrescá la página con `Ctrl+F5`.

## Editar contactos / redes

Toda la info de contacto está centralizada en el objeto `KODO` al inicio del `<script>` en `index.html`. Editás un valor ahí y se actualiza en todo el sitio (nav, footer, CTAs, formulario, WhatsApp flotante).

```js
const KODO = {
  email: 'contacto.kodo@gmail.com',
  whatsappNumber: '59894526583',     // sin '+' ni espacios
  instagramUrl: 'https://www.instagram.com/kodo_uy/',
  // ...
};
```

## Agregar imágenes a un proyecto

1. Subí las imágenes a `assets/proyectos/` con nombres descriptivos: `casa-piloto-06-detalle.jpg`.
2. En `index.html`, dentro de la `<div class="proyecto-gallery">` del proyecto correspondiente, copiá un bloque `<div class="gallery-item">` existente y cambiale:
   - el `src` de la imagen
   - el `alt`
   - el `data-caption` del `.img-wrap` (lo que se ve en el lightbox)
   - el texto de `.gallery-caption` (el subtítulo bajo la imagen)
3. Si una imagen no carga, el contenedor muestra un placeholder limpio (no se rompe).

**Recomendación:** subí imágenes JPG de máximo 1920px de ancho y ~85% de calidad. Las que están en este zip ya están optimizadas (~200–500KB cada una).

## Lightbox / zoom

Al hacer click en cualquier imagen de proyecto se abre un visor con flechas para navegar. Funciona con teclado (← → Esc).

## Dominio propio

Settings → Pages → Custom domain. Apuntás tu DNS al usuario de GitHub y listo.
