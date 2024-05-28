---
title: Guía para crear un blog de Jekyll en Github Pages
layout: post
date:   2024-05-28 00:59:34 -0700
categories: jekyll tutorial
---

Crear un nuevo proyecto Jekyll:

```sh 
jekyll new myblog && cd myblog
```
Para ver el blog en `localhost`:

```sh
bundle exec jekyll serve
```

**Nota**: en la [documentación de Jekyll]() se explica que 
el paso 
anterior puede fallar en caso de usar Ruby >= 3.0.0. Esto 
puede causar problemas cuando se publica el sitio en Github 
Pages.

# Github Pages

También ver: [documentación de 
Github](https://docs.github.com/es/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyl)

Crear un nuevo repositorio local en `myblog/` y añadir 
los cambios:

```sh
git init
git add .
git commit -m "init commit"
```

Crear un repositorio en Github con el mismo nombre y 
después:

```sh
git remote add origin https://github.com/<user>/myblog.git
git branch -M main
git push -u origin main
```

Ahora los cambios se confirmarán a la rama `main` que apunta 
(tracks) a `origin/main`, la rama en Github.

Abrir el repositorio en Github: 
`https://github.com/<user>/myblog`

Settings > Build and deployment > Source: Github Actions

Dar click a `Configure Jekyll` y confirmar cambios. 

Esto creará `.github/workflows/jekyll.yml` en el 
repositorio.

# Github Actions

Para que Github pueda procesar los cambios del sitio con 
Jekyll a través de Github Actions, debemos editar algunos 
valores del `Gemfile`.

Abrir `Gemfile` y quitar la gem de `Jekyll` y activar la 
de `github-pages` y `webrick`.

Así se ve el de este sitio:

```ruby
source "https://rubygems.org"

gem "minima", "~> 2.5"
gem "webrick"

group :jekyll_plugins do
  gem "github-pages"
  gem "jekyll-feed", "~> 0.12"
end
```

Añadir Linux:

```sh
bundle lock --add-platform x86_64-linux
```

Bajar cambios anteriores de `origin/main`:

```sh
git pull
```

Confirmar cambios al repositorio remoto:

```sh
git cmt && git push
```

Ahora cualquier cambio que se haga en `_posts/` aparecerá en 
`https://<usuario>.github.io/<repositorio>` en cuestión de 
minutos.

