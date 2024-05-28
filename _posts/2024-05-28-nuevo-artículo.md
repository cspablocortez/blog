---
title: Guía para crear nuevo artículo
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

```sh
nano _drafts/<título>.md
```

Añadir front matter con fecha y título, luego pasar el 
archivo a `_posts`.

Para ver un borrador en `localhost`:

```sh
bundle exec jekyll serve --drafts
```

Para pasarlo a `_posts` y publicar:

```sh
mv _drafts/<título>.md _posts/2024-05-28-<título>.md
```



