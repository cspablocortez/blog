---
title: La configuración de mis notas a un blog de Jekyll
date: 2024-05-29
layout: post
published: true
---

Llevo la mayor parte del año acumulando notas de mi día a 
día en archivos markdown gestionados por un repositorio 
git. Configuré una aplicación de Sinatra para generar un 
blog rudimentario, con la habilidad de buscar archivos y 
mostrar una versión HTML de cada documento con RedCarpet y 
WebRick. Estaba inventando el hilo negro. Jekyll ya tiene 
todas estas funciones por defecto, así que me propuse 
convertir ese conjunto de carpetas y scripts para gestionar 
la creación de contenido en un sólo proyecto Jekyll.

La estructura del repositorio antes de Jekyll:[^1]

[^1]: El sitio Jekyll está en `stage/`  

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

Mi rutina durante este tiempo consistió de los siguientes 
comandos:

```sh
$ bin/new hoy
```

Esto genera un archivo con el formato 
`mayo/29-miércoles.md`.

Para editar y escribir uso una combinación de nano y vim, 
nano para redactar y vim para editar, en especial si un 
documento necesita ediciones precisas y repetitivas. 

Antes de convertir el archivo en HTML para verlo en un 
servidor local, ejecuto `bin/spell [archivo]`:

```ruby
#!/usr/bin/env ruby

input_filename = ARGV[0] || 'input.md'

system("aspell -c -d es #{input_filename}")
```

y después con `bin/preview [archivo]` puedo ver el documento 
en un navegador. Este preview solo funciona con un archivo a 
la vez. Para ver todos los documentos que tenía 
acumulados, usaba `bin/run`, lo que activaba la aplicación 
de Sinatra que gestionaba el contenido. En ocasiones usaba 
[glow](https://github.com/charmbracelet/glow) para leer los 
documentos sin tener que iniciar un servidor.

Los Ruby scripts de `bin/` facilitaron mucho mi proceso de 
creación, así que al convertir el proyecto en un website 
para Jekyll, decidí reescribirlos, orientados al 
sistema de archivos de Jekyll, en particular el uso de las 
carpetas 
`_drafts` y `_posts` y los nombres requeridos para los 
archivos, porque Jekyll necesita los archivos en formato 
`YYYY-MM-DD.md`.

## Creación de Sitio Jekyll

Empecé por crear un proyecto de Jekyll:

```sh
jekyll new stage
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

Para el tipo de contenido que pienso albergar en este sitio, 
decidí instalar el tema 
[Persephone](https://github.com/erlzhang/jekyll-theme-persephone) 
en el `Gemfile` con `bundle install`. Dediqué la mayor parte 
de la tarde a configurar el sitio y leer su 
documentación.

## Scripts de gestión de contenido

Antes de crear los scripts en mi carpeta de notas, decidí 
escribirlos para este blog. En total son dos scripts:

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

### PATH

Para poder usar los scripts desde cualquier directorio (es 
decir, en otros blogs Jekyll) copié el script al directorio 
`~/bin`:

```sh
cp spell ~/bin
```

#### Directorio ~/bin

Después de constatar que no casuaran problemas, agregué 
ambos scripts al directorio `~/bin`. Este directorio 
contiene los archivos binarios del sistema, personalizados 
al usuario actual. También existe `/bin` y `/usr/bin`, el 
primero contiene los programas necesarios durante el proceso 
de arranque y están disponibles para todos los usuarios, y 
el último los que no son críticos.

```sh
$ mkdir ~/bin
$ echo 'export PATH="$HOME/bin:$PATH"' >> ~/.zshrc
$ source ~/.zshrc
```

Al agregar `~/bin` a la variable `PATH`, mi terminal zsh 
sabrá que allí puede encontrar los scripts.
