---
title: Devlog Part 3 - Project Structure
date: 2024-06-05 16:30:00 -7000
layout: post
published: true
---

# Typical Jekyll Project Structure

The folder structure of a Jekyll site changes depending on if you are using a gem-based theme or not.  A basic Jekyll site usually has a file structure that looks like this:

```
.
├── _config.yml
├── _data
│   └── members.yml
├── _drafts
│   ├── begin-with-the-crazy-ideas.md
│   └── on-simplicity-in-technology.md
├── _includes
│   ├── footer.html
│   └── header.html
├── _layouts
│   ├── default.html
│   └── post.html
├── _posts
│   ├── 2007-10-29-why-every-programmer-should-play-nethack.md
│   └── 2009-04-26-barcamp-boston-4-roundup.md
├── _sass
│   ├── _base.scss
│   └── _layout.scss
├── _site
├── .jekyll-cache
│   └── Jekyll
│       └── Cache
│           └── [...]
├── .jekyll-metadata
└── index.html # can also be an 'index.md' with valid front matter
```

The [Jekyll documentation][jekyll-docs] provides an overview of what each of these folders and files does.

<table>
  <thead>
    <tr>
      <th>File / Directory</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>_config.yml</code></p>
      </td>
      <td>
        <p>
          Stores configuration data. Many of
          these options can be specified from the command line executable but
          it’s easier to specify them here so you don’t have to remember them. <a href="https://jekyllrb.com/docs/configuration/options/">Here</a> is a list of available settings.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_drafts</code></p>
      </td>
      <td>
        <p>
          Drafts are unpublished posts. The format of these files is without a
          date: <code>title.MARKUP</code>, where <code>.MARKUP</code> is usually <code>.markdown</code> or <code>.md</code>. 
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_includes</code></p>
      </td>
      <td>
        <p>
          These are the partials that can be mixed and matched by your layouts
          and posts to facilitate reuse. The liquid tag
          <code>{% raw %}{% include file.ext %}{% endraw %}</code>
          can be used to include the partial in
          <code>_includes/file.ext</code>, where <code>.ext</code> is usually <code>.html</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_layouts</code></p>
      </td>
      <td>
        <p>
          These are the templates that wrap posts. Layouts are chosen on a
          post-by-post basis in the front matter. The liquid tag
          <code>{% raw %}{{ content }}{% endraw %}</code>
          is used to inject content into the web page.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_posts</code></p>
      </td>
      <td>
        <p>
          Your dynamic content, so to speak. The naming convention of these
          files is important, and must follow the format:
          <code>YEAR-MONTH-DAY-title.MARKUP</code>.
          The permalinks can be customized for
          each post, but the date and markup language are determined solely by the file name.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_data</code></p>
      </td>
      <td>
        <p>
          Well-formatted site data should be placed here. The Jekyll engine
          will autoload all data files (using either the <code>.yml</code>,
          <code>.yaml</code>, <code>.json</code>, <code>.csv</code> or
          <code>.tsv</code> formats and extensions) in this directory,
          and they will be accessible via `site.data`. For example, if there's a file
          <code>members.yml</code> under the directory, then you can access
          contents of the file through <code>site.data.members</code>.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_sass</code></p>
      </td>
      <td>
        <p>
          These are sass partials that can be imported into your <code>main.scss</code>
          which will then be processed into a single stylesheet
          <code>main.css</code> that defines the styles to be used by your site.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_site</code></p>
      </td>
      <td>
        <p>
          This is where the generated site will be placed (by default) once
          Jekyll is done transforming it. It’s probably a good idea to add this
          to your <code>.gitignore</code> file.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>.jekyll-cache</code></p>
      </td>
      <td>
        <p>
          Keeps a copy of the generated pages and markup (e.g.: markdown) for
          faster serving. Created when using e.g.: <code>jekyll serve</code>.
          Can be disabled with
          <a href="https://jekyllrb.com/docs/configuration/options/">an option and/or flag</a>.
          This directory will not be included in the generated site. It’s
          probably a good idea to add this to your <code>.gitignore</code>
          file.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>.jekyll-metadata</code></p>
      </td>
      <td>
        <p>
          This helps Jekyll keep track of which files have not been modified
          since the site was last built, and which files will need to be
          regenerated on the next build. Only created when using
          <a href="https://jekyllrb.com/docs/configuration/incremental-regeneration/">
          incremental regeneration</a> (e.g.: with <code>jekyll serve -I</code>).
          This file will not be included in the generated site. It’s probably
          a good idea to add this to your <code>.gitignore</code> file. 
          <strong>Incremental regeneration is an experimental feature of Jekyll</strong>.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>index.html</code> or <code>index.md</code> and other HTML,
        Markdown files</p>
      </td>
      <td>
        <p>
          Provided that the file has a <a href="https://jekyllrb.com/docs/front-matter/">front
          matter</a> section, it will be transformed by Jekyll. The same will
          happen for any <code>.html</code>, <code>.markdown</code>,
          <code>.md</code>, or <code>.textile</code> file in your site’s root
          directory or directories not listed above.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Other Files/Folders</p>
      </td>
      <td>
        <p>
          Except for the special cases listed above, every other directory and 
          file—such as <code>css</code> and <code>images</code> folders,
          <code>favicon.ico</code> files, and so forth—will be copied verbatim
          to the generated site. 
        </p>
      </td>
    </tr>
  </tbody>
</table>

Every file or directory beginning with the following characters: `.`, `_ `, `#` or `~` in the `source` directory will not be included in the `destination` folder. Such paths will have to be explicitly specified via the config file in the `include` directive to make sure they're copied over:

```yaml
include:
 - _pages
 - .htaccess
 ```

# Devlog Structure

However, our file structure is much simpler, since we are using the gem-based theme [minima][minima][^1], so it looks something like this:

[^1]: The installation of a gem-based theme is defined in your `Gemfile`. To see where the theme was downloaded in your computer, run `bundle info minima` in your terminal. This will output a summary, a link to the theme's homepage, and a file path where the gem is installed, such as `/Users/pablo/.rbenv/versions/3.2.2/lib/ruby/gems/3.2.0/gems/minima-2.5.1`.


```
.
├── 404.html
├── Gemfile
├── Gemfile.lock
├── README.md
├── _config.yml
├── _posts
│   ├── 2024-06-04-welcome-to-jekyll.markdown
│   ├── 2024-06-05-congressional-day-1.md
│   └── 2024-06-05-sample-post.md
├── about.markdown
└── index.markdown

1 directory, 10 files
```


# Conclusion 

As the Jekyll documentation explains: 

> The goal of gem-based themes is to allow you to get all the benefits of a robust, continually updated theme without having all the theme’s files getting in your way and over-complicating what might be your primary focus: creating content.

After you write the settings you want, such as website name, author, site description, etc. in your `_config.yml` document, we can begin writing new posts.

# Next: [Part 4 - How to write a new devlog entry](/blog/2024/06/05/devlog-part-four.html)

--- 

#### Footnotes

[minima]: https://github.com/jekyll/minima
[jekyll-docs]: https://jekyllrb.com/docs/structure/

