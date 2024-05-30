---
title: De Sinatra a Jekyll 
date: 2024-05-29
layout: post
published: true
---

Llevo la mayor parte del año acumulando notas de mi día a 
día en archivos markdown gestionados por un repositorio git. 
Configuré una aplicación de Sinatra para generar un blog 
rudimentario con la habilidad de buscar archivos y mostrar 
una versión HTML de cada documento con RedCarpet y Webrick. 
Estaba inventando el hilo negro. Jekyll ya tiene todas estas 
funciones por defecto, así que me propuse consolidar todo 
ese conjunto de carpetas y scripts en un sólo proyecto 
Jekyll.

La estructura del repositorio antes de Jekyll:

```sh
$ tree ~/Documents/Notas2024/ -I stage/
```



```
.
├── 404.md
├── Gemfile
├── Gemfile.lock
├── README.md
├── app.rb
├── bin
│   ├── new
│   ├── preview
│   ├── run
│   └── spell
├── enero
│   ├── 2024\ Notas.txt
│   ├── Galette\ des\ rois.txt
│   ├── Gatos.txt
│   ├── Jueves\ 25\ enero.txt
│   ├── La\ chica\ del\ cumpleaños.txt
│   ├── Lunes\ 22\ ene.txt
│   ├── Martes\ 23\ enero.txt
│   └── Sunday\ January\ 21.txt
├── febrero
│   ├── Breaking\ in\ Brooklyn.txt
│   ├── Carnegie\ Council.txt
│   ├── Domingo\ 4\ febrero.txt
│   ├── Jueves\ 8\ febrero.txt
│   ├── Jueves\ febrero\ 1.txt
│   ├── Lunes\ 12\ febrero.txt
│   ├── Lunes\ 19\ febrero.txt
│   ├── Martes\ 13\ febrero.txt
│   ├── Martes\ 6\ febrero.txt
│   ├── Miércoles\ 14\ febrero.txt
│   ├── Miércoles\ 28\ febrero.txt
│   ├── Miércoles\ 7\ febrero.txt
│   ├── Sábado\ 10\ febrero.txt
│   ├── Sábado\ 17\ febrero.txt
│   ├── Sábado\ 24\ febrero.txt
│   ├── Sábado\ 3\ febrero.pages
│   ├── Sábado\ 3\ febrero.txt
│   ├── Viernes\ 16\ febrero.txt
│   ├── Viernes\ 2\ febrero.txt
│   └── Viernes\ 9\ febrero.txt
├── index.html
├── index.md
├── marzo
│   ├── 03-domingo.md
│   ├── 04-lunes.md
│   ├── Jueves\ 14\ marzo.txt
│   ├── Lunes\ 11\ marzo.txt
│   ├── Martes\ 12\ marzo.txt
│   ├── Martes\ 12\ resumen\ .txt
│   ├── Martes\ 5\ marzo.txt
│   ├── Miércoles\ 13\ marzo.txt
│   ├── Miércoles\ 6\ marzo.txt
│   ├── Sábado\ 2\ marzo\ FINAL.txt
│   ├── Viernes\ 1\ marzo.txt
│   ├── Viernes\ 22\ marzo.txt
│   ├── Viernes\ 8.txt
│   └── marzo.md
├── misc
│   ├── Bisiesto.md
│   ├── Clara.md
│   ├── Clara.md.bak
│   ├── El\ traductor.md
│   ├── Extensión\ .txt
│   ├── Metamorfosis.md
│   ├── Seattle.txt
│   ├── Silencio.md
│   ├── TEST\ FILE.txt
│   ├── Vida_Anne_Moore.md
│   ├── Vida_Anne_Moore.md.bak
│   ├── preview.rb
│   └── spellcheck.rb
├── pdfs
│   ├── Bolaño.pdf
│   ├── Clara.pdf
│   ├── Silencio.pdf
│   ├── Vida_Anne_Moore.pdf
│   └── index.md
├── public
│   ├── css
│   │   ├── epub-style.css
│   │   ├── normalize.css
│   │   ├── skeleton.css
│   │   └── style.css
│   └── images
│       └── Bisiesto.png
├── rails.md
├── recordatorios.md
└── views
    ├── _form.erb
    ├── _navbar.erb
    ├── _results.erb
    ├── index.erb
    ├── layout.erb
    ├── month.erb
    ├── page.erb
    ├── search.erb
    └── year.erb

14 directories, 106 files

```

Mi rutina durante este tiempo consistió en el uso de los 
siguientes comandos:

```sh
$ bin/new hoy
```

Esto genera un archivo con el formato 
`mayo/29-miércoles.md`.

Para editar y escribir uso una combinación de nano y vim, 
nano para redactar y vim para editar, en especial si un 
documento necesita ediciones precisas o repetitivas. 

Antes de convertir el archivo en HTML para verlo en un 
servidor local ejecuto `$ bin/spell [archivo]`:

```ruby
#!/usr/bin/env ruby

input_filename = ARGV[0] || 'input.md'

system("aspell -c -d es #{input_filename}")
```

Con `bin/preview [archivo]` el documento queda confirmado en 
el repositorio con un mensaje de autoguardado y se abre en 
el navegador, pero solo funciona con un archivo a la vez. 
Para ver todos los documentos, usaba `bin/run` para iniciar 
la aplicación de Sinatra. En ocasiones usaba 
[glow](https://github.com/charmbracelet/glow) para leer los 
documentos sin tener que iniciar un servidor, ya que todo el 
proceso anterior me resultaba engorroso para cambios 
pequeños o para leer un determinado documento. La idea ahora 
es enfocarse en el contenido y dejar su procesamiento y 
distribución a Jekyll.

## Creación de Sitio Jekyll

La guía de inicio de la [documentación](https://jekyllrb.com/docs/) explica cómo 
crear un blog. También escribí una [guía para publicar un 
projecto de Jekyll en Github Pages]({{ site.baseurl }}{% post_url 2024-05-28-github-pages %}).


```sh
$ jekyll new stage
```

Los primeros archivos que pasé a `_posts` fueron los del mes 
de mayo, así que renombré los archivos markdown dentro de la 
carpeta `mayo/` anteponiendo la cadena `"2024-05-"` (e.g., 
de `mayo/29-miércoles.md` a `mayo/2024-05-29-miércoles.md` 
con el siguiente comando:

```sh
$ for file in *.md do mv "$file" "2024-05-$file"; done
```

Luego moví la carpeta a `_posts` y pude ver todos los 
archivos con `bundle exec jekyll serve`.

Como tuve que repetir este proceso y también debía incluir 
el [Front Matter](https://jekyllrb.com/docs/front-matter/) 
en los documentos existentes, fue más 
conveniente hacer un Bash script `prepend.sh` dentro de la 
carpeta de abril.

```bash
#!/bin/bash

for file in *.md; do
    echo "---" > temp
    echo "layout: post" >> temp
    echo "---" >> temp
    echo "" >> temp
    cat "$file" >> temp
    mv temp "$file"

    mv "$file" "2024-04-$file"
done
```

Para  ejecutar el script: `$ chmod +x prepend.sh` y 
después `$ ./prepend.sh`.


## Cambio de tema

Para el tipo de contenido que pienso alojar en este sitio, 
decidí instalar el tema 
[Persephone](https://github.com/erlzhang/jekyll-theme-persephone) 
en el `Gemfile` con `bundle install`. 

## Scripts de gestión de contenido

### Nuevo Post

`./new_post`: 

```ruby
#!/usr/bin/env ruby

print "Título: "
title = gets.chomp
slug = title.downcase.strip.gsub(' ', '-').gsub(/[^\w-]/, '')

date = Time.now.strftime("%Y-%m-%d")

filename = "_posts/#{date}-#{slug}.md"

content = <<~HEREDOC
  ---
  title: #{title}
  date: #{date}
  layout: post
  published: false
  ---

  
HEREDOC

File.write(filename, content)

puts "Post created: #{filename}"
```

### Chequeo de ortografía

`./spell [archivo]`:

```ruby
#!/usr/bin/env ruby

filename = ARGV[0]
system("aspell -c -d es #{filename}")
```

### Previsualización de archivos

`pvw` es un alias en mi `~/.zshrc`:

```bash
alias pvw='bundle exec jekyll serve'
```

y después: `source ~/.zshrc`.

### Nota sobre PATH

Para poder usar los scripts desde cualquier directorio se 
necesita copiar (o mover) el script al directorio `~/bin`:

```sh
cp spell ~/bin
```

#### Directorio ~/bin

Este directorio contiene los archivos binarios del sistema, 
personalizados al usuario actual. También existe `/bin` y 
`/usr/bin`, el primero contiene los programas necesarios 
durante el proceso de arranque y están disponibles para 
todos los usuarios, y el último los que no son críticos.

```sh
$ mkdir ~/bin
$ echo 'export PATH="$HOME/bin:$PATH"' >> ~/.zshrc
$ source ~/.zshrc
```

Al agregar `~/bin` a la variable `PATH`, mi terminal zsh 
sabrá que allí puede encontrar los scripts.
