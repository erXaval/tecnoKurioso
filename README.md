# TecnoKurioso

Blog sobre noticias, innovación y nuevos usos de la inteligencia artificial en el mundo de las telecomunicaciones.

**Web publicada:** <https://erxaval.github.io/tecnoKurioso/>

Proyecto de la Actividad 1 (Laboratorio: creación de un blog) de la asignatura *Desarrollo de Aplicaciones en Red*.

## Tecnologías

- **[Jekyll](https://jekyllrb.com/) 4.4**: generador de sitios estáticos.
- **Tema minima 2.5**, personalizado con plantillas (`_layouts`, `_includes`) y estilos (`assets/main.scss`) propios.
- **GitHub Pages + GitHub Actions**: cada `push` a `main` compila el sitio y lo publica (`.github/workflows/jekyll.yml`).
- Plugins: `jekyll-feed` (RSS) y `jekyll-seo-tag` (metaetiquetas para buscadores y redes).

## Ejecutarlo en local

Requisitos: Ruby (con Devkit en Windows), Bundler y Git.

```bash
bundle install
bundle exec jekyll serve
```

Abre <http://localhost:4000/tecnoKurioso/>. Si cambias `_config.yml`, reinicia el servidor.

## Estructura

```
├── _config.yml           Configuración del sitio (título, URL, menú, permalinks)
├── _data/secciones.yml   Secciones del blog: nombre, descripción y color
├── _includes/            Piezas reutilizables: cabecera, pie, tarjeta de entrada,
│                         etiqueta de sección, tiempo de lectura
├── _layouts/             Plantillas: portada (home), entrada (post), sección
├── _posts/               Entradas del blog (AAAA-MM-DD-titulo.md)
├── assets/main.scss      Estilos propios sobre minima
├── assets/img/           Logo, favicon e ilustraciones de las entradas (SVG propios)
├── noticias.md           Página de sección (una por sección)
├── ia-telecom.md
├── explicado.md
├── archivo.md            Todas las entradas agrupadas por año
├── about.md              Sobre el blog
└── 404.html              Página de error
```

## Publicar una entrada nueva

1. Crea `_posts/AAAA-MM-DD-titulo-sin-tildes.md`.
2. Añade el front matter:

   ```yaml
   ---
   title: "Título de la entrada"
   categories: noticias        # noticias | ia-telecom | explicado
   tags: [5g, ia]
   description: "Resumen de una frase para buscadores"
   image: /assets/img/posts/imagen.svg
   ---
   ```

3. Escribe una entradilla, la marca `<!--more-->` y el resto del artículo en Markdown.
4. Comprueba en local, haz commit y push. La entrada aparece sola en la portada, en su sección y en el archivo.

Para enlaces internos usa `{% link %}`, `{% post_url %}` o el filtro `relative_url`, porque el sitio vive en `/tecnoKurioso/`.

## Licencias

- Código: [MIT](LICENSE).
- Textos e imágenes: [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.es).
