---
title: Devlog Part 4 - New Devlog Entries
date: 2024-06-05 23:12:50 -4000
layout: post
published: true
---

Writing and managing your posts in a Jekyll site is easy. Every entry for your devlog will be a Markdown file saved in the `_posts` folder.

To create a new post, create a new file within `_posts` using the following format: `YYYY-MM-DD-TITLE.md`. For example, our first entry will be titled "Congressional App Challenge Day 1", so we will be creating a file called `2024-06-05-congressional-day-1.md`.


In this file, we will outline today's lesson. We started by reviewing the 2023 Congressional App Challenge winners for Nevada, making notes about the app idea and its implementation, paying attention to the software stack used. To add this information in our file, the first thing we must do is add [front matter][front-matter].

# Front Matter

Front matter is a snippet of YAML placed between two triple-dashed lines at the start of a file.

We will specify a title and a layout for this entry like so:

```
---
title: Congressional App Challenge Day 1
layout: post
---
```

That's all we need! Now we can begin writing our content in Markdown.

# Markdown

> Markdown is a markup language that adds formatting elements to plaintext documents.

Think about the writing apps you use often, like Google Docs or Microsoft Word. In these types of apps, called word processors, whenever you want to format certain words to stand out&mdash;like making some words bold, some italic, or adding headings to different sections, you'd either use the buttons at the top of the menu (**B** for bold, ***I*** for italics, etc.) or use a keyboard shortcut, like Ctrl + B to make something bold. 

Markdown allows you to do all of this formatting just by typing special characters within your document. For example, to make a word **bold**, we write two asterisks around it: `**bold**`.

The reason why Markdown is useful is because it preserves your text formatting across multiple document types. It can be exported to HTML so we can upload to a website (this is what we are doing), but we can also write plain text and export from Markdown to PDF, PowerPoint, Microsoft Word, etc. 

Take a look at the [Getting Started](https://www.markdownguide.org/getting-started/) guide or the [cheat sheet](https://markdownguide.offshoot.io/cheat-sheet/) from [Markdown Guide](https://www.markdownguide.org/) to learn more. 

# Conclusion

You now have all you need to maintain a devlog as you build your Congressional App Challenge.

--- 

#### Footnotes

[minima]: https://github.com/jekyll/minima
[jekyll-docs]: https://jekyllrb.com/docs/structure/
[front-matter]: https://jekyllrb.com/docs/step-by-step/03-front-matter/


