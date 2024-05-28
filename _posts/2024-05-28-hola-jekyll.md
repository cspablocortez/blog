---
title: Hola Jekyll
layout: post
date:   2024-05-28 00:59:34 -0700
categories: jekyll update
---

No hay mucho cambio en la rutina que más o menos 
ya había concertado para este proceso de escribir notas: 
sigo abriendo mi Terminal a un determinado directorio, 
luego:

```sh
$ nano _posts/YEAR-MONTH-DAY-title.MARKUP
```

Se abre nano y empiezo a editar el documento de texto desde 
una terminal con una paleta de colores agradable, 
configurado como a mí me gusta, como escribo todos los días. 
La rutina sigue siendo la misma, la materia prima sigue 
siendo la misma, y ya sea por pandoc o Jekyll, el texto 
plano se convierte en un sitio web o en un archivo PDF o en 
un libro electrónico. La distribución universal del texto a 
una escala descomunal y sin precedentes. La ironía de usar 
editores de textos de décadas pasadas como vim, nano o emacs 
me gusta, le insufla vida a los dispositivos de generaciones 
anteriores. Con tener acceso a una Terminal, la 
participación en la batalla campal por la atención de los 
usuarios del internet se vuelve posible. Democratiza el 
acceso a la información. *Welcome to the future, baby.* 

Jekyll muestra los cambios más rápido que con 
todo el proceso que me había armado a través de Ruby, 
Sinatra y RedCarpet para convertir mis archivos de markdown 
a HTML y después iniciar un servidor local (incapaz de 
mostrar cambios al instante como aquí).

## Instalación y un nuevo proyecto

La guía de inicio de la 
[documentación](https://jekyllrb.com/docs/) explica cómo 
crear un blog.

En `localhost:4000` se puede ver el sitio con una primera 
publicación que le da la bienvenida al usuario. 

El contenido del sitio proviene de los archivos markdown dentro de la 
carpeta `_posts/`, con el nombre siguiendo el formato 
mencionado anteriormente.

Jekyll instala el tema 
[minima](https://github.com/jekyll/minima) por defecto a través de una Ruby gem,
es decir, el proyecto no tendrá las carpetas de `assets`, `_data`, `_layouts`, 
`_includes` y `_sass`. Por una parte, esto hace de la creación de contenido el 
principal objetivo, no hay tantos archivos con que 
distraerse. Me imagino que podré ir creando cada carpeta que considere necesaria
y que Jekyll podrá unir los cambios sin problema. 

## Configuraciones

El archivo que contiene los valores provisionales de Jekyll 
es `_config.yml`. Allí se cambian los metadatos del sitio.