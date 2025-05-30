---
title: 'Add custom css to chirpy theme'
date: 2025-05-29
categories: [IT]
tags: [chirpy, code, jekyll, customize]
---
### Custom css in chirpy theme?
1. create folder `../assets/css`
2. add `jekyll-theme-chirpy.scss` from source
3. append the file like this e.g.  

```css
/* append your custom style below */

/* fix margin-left of highlight css for code block until I know better */

.highlight pre {
    margin-bottom: 0;
    margin-top: 1rem;
    margin-left: 1rem;
    font-size: .85rem;
    line-height: 1.4rem;
    word-wrap: normal;
}
```
