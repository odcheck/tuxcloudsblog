---
title: 'Set gopath in oh-my-zsh'
date: 2025-05-28
categories: [IT]
tags: [zsh, go, path, custom]
---
Since I am not using bash but oh my zsh, I was confused in the first place, what would be the right way to set an additional path.  
The answer is the `custom` folder and a simple `.zsh` file.
```bash
  cd $ZSH_CUSTOM  
  vim additional_paths.zsh  
```
... and within that file it would be in my case:
```bash
  cat ~/.oh-my-zsh/custom/additional_paths.zsh
```
```bash
  # Add go to path
  export PATH=$PATH:/usr/local/go/bin
```
