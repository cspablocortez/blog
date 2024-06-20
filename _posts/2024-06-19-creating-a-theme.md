---
title: Guide for Creating a Jekyll Theme
date: 2024-06-19 17:24:58 -0700
layout: post
published: true
---

Yesterday we created some important files and folders for our Jekyll project. Today we will continue adding all the necessary files and building the HTML structure.

Objective:

- Define the HTML structure of our project
- Create all necessary Jekyll files
- Set up our project to accept external CSS themes 

# Step 1 - Necessary Files

In case you haven’t added all the necessary files, these two bash commands should suffice:

```bash
$ mkdir -p _layouts _includes assets/css

$ touch _layouts/default.html _layouts/post.html _includes/header.html _includes/footer.html assets/css/style.css
```

# Step 2 - Defining Layouts

A `layout` is an HTML template that defines how your content (the markdown files) should be displayed .

## Default Layout

 The file `_layouts/default.html` is the file for all markdown documents.
 
 ```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ page.title }}</title>
    <link rel="stylesheet" href="{{ "/assets/css/style.css" | relative_url }}">
</head>
<body>
    <header class="site-header">
        {% include header.html %}
    </header>

    <main class="site-content">
        {{ content }}
    </main>

    <footer class="site-footer">
        {% include footer.html %}
    </footer>
</body>
</html>
 ```

## Post Layout

The `_layouts/post.html` is the HTML template for the posts (so the markdown files that are not "pages" like Home, About, Contact, etc.)

```html
---
layout: default
---

<article class="post">
    <header class="post-header">
        <h1 class="post-title">{{ page.title }}</h1>
        <p class="post-meta">{{ page.date | date: "%B %d, %Y" }}</p>
    </header>
    <section class="post-content">
        {{ content }}
    </section>
</article>
```

# Includes

Since HTML templates can get large, we can write partial HTML components like the navigation bar or footers as separate files. These go inside the `_includes` folder.

We are going to create two, the header and the footer.

`_includes/header.html`:

```html

<nav class="navbar">
    <a href="{{ site.baseurl }}/" class="nav-link">Home</a>
    <a href="{{ site.baseurl }}/about" class="nav-link">About</a>
    <a href="{{ site.baseurl }}/blog" class="nav-link">Blog</a>
</nav>
```

`_includes/footer.html`:

```html
<div class="footer-content">
    <p>&copy; {{ site.time | date: "%Y" }} {{ site.title }}. All rights reserved.</p>
</div>
```

# Config File

As you know, the `_config.yml` file holds all of our site settings.

Here’s an example of what it could look like:

```yml
title: My Jekyll Site
description: >- # this means to ignore newlines until "baseurl:"
  A simple Jekyll theme
baseurl: "" # the subpath of your site, e.g. /blog
url: "http://yourdomain.com" # the base hostname & protocol for your site
```

# Sample Content

We will use the default sample post that Jekyll provides when we use the `jekyll new project` command and another post to test out HTML and CSS.

Add the following markdown files to your 

```
---
layout: post
title: "Sample Post"
date: 2023-01-01
---

# This is a Heading 1

## This is a Heading 2

### This is a Heading 3

#### This is a Heading 4

##### This is a Heading 5

###### This is a Heading 6

Here is some **bold text** and some *italic text*. Here is a [link](https://www.example.com).

> This is a blockquote.

- This is a list item
- Another list item

1. First ordered list item
2. Another ordered list item

Here is a `code snippet`.
```

```markdown
---
layout: post
title:  "Welcome to Jekyll!"
date:   2024-06-19 17:38:09 -0700
categories: jekyll update
published: true
---

You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

Jekyll requires blog post files to be named according to the following format:

`YEAR-MONTH-DAY-title.MARKUP`

Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

Markdown is used for comments in [Discord][discord].

<p>Markdown is used for comments in <a href="https://discord.com">Discord</a>.

[discord]: https://discord.com

[jekyll-docs]: https://jekyllrb.com/docs/home

[jekyll-gh]: https://github.com/jekyll/jekyll

[jekyll-talk]: https://talk.jekyllrb.com/

```

# Preview Changes

Remember that to run a local server and see the changes in your project you must run `bundle exec jekyll serve` at the terminal, which will launch a local server at `localhost:4000`.