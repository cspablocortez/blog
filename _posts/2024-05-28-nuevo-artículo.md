---
title: Guía para crear un nuevo artículo
layout: post
date: 2024-05-28 14:49:19 -7000
categories: jekyll tutorial
---

Para crear un nuevo artículo se necesita lo siguiente:

## Front Matter

```yaml
---
title: 
layout: post
date:   
categories: 
---
```

## Borradores

Para crear un borrador usando nano:

```sh
nano _drafts/<título>.md
```

Para ver un borrador en `localhost`:

```sh
bundle exec jekyll serve --drafts
```

## Publicación

Para pasarlo a `_posts` y publicar:

```sh
mv _drafts/<título>.md _posts/YYYY-MM-DD-<título>.md
```

## Layouts

Por defecto los artículos usan el layout `post` del tema 
minima. Para editar estos archivos primero podemos ver la 
instalación local:

```sh
code $(bundle info --path minima)
```

Cada archivo que se quiera modificar debe crearse como copia
en el repositorio local para evitar cambiar la configuración 
y el código de la Ruby gem.

