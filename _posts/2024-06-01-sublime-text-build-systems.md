---
title: Sistemas de compilación en Sublime Text 
layout: post
published: true
---

[Artículo sobre Build Systems](https://www.sublimetext.com/docs/build_systems.html) en la documentación de Sublime Text.

# ¿Qué son?

Sublime Text incluye la opción de usar (y crear) sistemas de compilación que le
permiten al usuario ejectutar programas externos. Por ejemplo, para ver los
resultados de un script en Python sin abrir y ejecutar el programa desde una
terminal, el usuario ejecuta un sistema de compilación y los resultados
aparecen en la consola del editor.

Un sistema de compilación es un archivo JSON con la extensión `.sublime-build`. 

# Cómo crear un Build System en Sublime Text

`Tools > Build System > New Build System...`

En esto ejemplo, el archivo markdown puede convertirse en PDF o en presentación 
usando `pandoc`.

```JSON
{
    "cmd": ["bundle", "exec", "jekyll", "serve"],
    "file_regex": "^(...*?):([0-9]*):?([0-9]*)",
    "selector": "source.gfm",
    "working_dir": "$file_path/../../",
    "variants": [
        {
            "name": "Convert to PDF",
            "cmd": ["pandoc", "$file", "-o", "${file_base_name}.pdf", "--toc"]
        },
        {
            "name": "Convert to Beamer PDF",
            "cmd": ["pandoc", "$file", "-t", "beamer", "-V", "theme:metropolis", "-s", "-o", "${file_base_name}.pdf"]
        }
    ]
}

```

# Cómo editar un Build System

El archivo queda guardado en la carpeta de `Packages` del usuario. 

Para abrirlo desde Sublime Text: `Settings → Browse Packages…:`


