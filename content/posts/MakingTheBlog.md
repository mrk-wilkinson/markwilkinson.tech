+++
title = "Making The Blog"
draft = false
date = 2024-01-04
tags = ["devops", "meta"]
+++

## TLDR;
* Zola: Static site generator using MD and Tera
* hermit_zola: Simple theme
* Github: Hosting and deployment

## Zola
Zola is a static site generator (converts MD to html) that runs in entirely in one binary. All it took to set up was
```bash
$> git init
$> zola init
```

## Hermit_zola
I followed the instructions <a href="https://www.getzola.org/themes/hermit/">here</a> and it looked great. I did have to add a section to my *config.toml* for the tags
```toml
taxonomies = [
           {name = "tags", rss = true}
]

```
## Deploying through github pages
I used github pages to host it since I didn't require any dynmaic components or full hosting. To configure automatic deployment I used github actions to serve the /public/ directory, which is the location zola stores "compiled" websites.

## My plan for this blog
I plan to upload some walkthroughs for tryhackme and hackthebox on here, aswell as some more original content related to information security (malware analysis on random samples I find, etc).  However, the odds this stays entirely infosec related are almost zero.
