---
layout: post
title:  "用scoop安裝jekyll"
date:   2022-03-29 14:37:21 +0800
categories: windows
tags: [scoop, githubPages, jekyll]
---
 
 這是在windows底下，linux底下才沒那麼麻煩咧.....

 在PowerShell底下

```batch
#Ruby：
scoop install ruby

#MSYS2：
scoop install msys2
msys2

#restart powershell
#ridk
ridk install 3

#Jekyll：
gem install bundler jekyll
gem update

#start local jekyll
bundle exec jekyll serve

```
