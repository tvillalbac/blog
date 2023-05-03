---
date: 2019-04-22 12:26
layout: post
title: Random Password Generator
subtitle: Bash one-liner
description: Quick script to generate random passwords.
image: https://bgx4k3p.github.io/blog/assets/img/code-large.jpg
category: linux
tags: linux ubuntu bash
author: bgx4k3p
paginate: true
---

## Use Bash function (for learning purposes)

```bash
#!/bin/bash

# Function to generate a 32 character random password
randomPass() {

 #Set local variable for password
 local randompass=$(cat /dev/urandom | env LC_CTYPE=C tr -dc 'a-zA-Z0-9!@#$%^&*()_+?><~\`;' | fold -w 32 | head -n 1)

 echo $randompass
}

randomPass
```

## Quick one-liner

```bash
cat /dev/urandom | env LC_CTYPE=C tr -dc 'a-zA-Z0-9!@#$%^&*()_+?><~\`;' | fold -w 32 | head -n 1
```
