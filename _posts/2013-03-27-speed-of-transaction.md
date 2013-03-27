---
layout: post
title: speed of transaction
meta: shell+awk+bc snippet to measure speed of transaction
---

# {{ page.title }}

bc -e "`{du -s /mnt/z2911kj6/pg && sleep 10 && du -s /mnt/z2911kj6/pg}|awk 'NR==1 {a=$1;}; NR==2 {print $1-a};'`*512/1024/1024"

Any more elegant way?