---
title: 'Disable line numbers in code blocks jekyll rouge highliter'
date: 2025-05-29
categories: [IT]
tags: [chirpy, code, jekyll, customize]
---
### How to get rid of line numbers in code blocks?
Edit `_config.yml` so that at reads like this:  
```
kramdown:
  syntax_highlighter: rouge
    block:
      line_numbers: false
```
