---
title: Jekyll y Github Pages
layout: post
date:   2024-05-28 00:59:34 -0700
categories: jekyll update
---

Jekyll, al ser producto del cofundador de Github, tiene (en teoría) el 
beneficio de integración nativa con Github Pages, el sistema 
de hosting de archivos estáticos de la compañía. En lo práctico no es así y tuve
problemas con diferentes versiones de Jekyll cuando incluí `gem "github pages"` 
en mi `Gemfile`. Para solucinarlo añadí `gem "webrick"` también.

```ruby
source "https://rubygems.org"

gem "minima", "~> 2.5"
gem "webrick"

# If you have any plugins, put them here!
group :jekyll_plugins do
  gem "github-pages"
  gem "jekyll-feed", "~> 0.12"
end
```

De esta manera puedo ver los cambios de mi sitio a través 
de `localhost`  con:

```sh
$ bundle exec jekyll serve`
```

Cuando confirmo los camnbios, Github Pages procesará mis archivos desde el 
código fuente del repositorio.
