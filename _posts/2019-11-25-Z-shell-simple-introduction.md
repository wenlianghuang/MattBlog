---
layout: post
title: "20191125 Z shell in Mac Introduction"
date: 2019-11-25
tags:
    - "jekyll"
---
<h2>Overview</h2>
Zsh is a shell that can be used as an interactive login shell and as a command interpreter for shell scripting. 
In June 2019, Apple announced that the forthcomming <a href = "https://www.apple.com/tw/macos/catalina/" target="_blank"> macOS Catalina(10.15)</a> would adopt Zsh as the default shell, replacing Bash

<h2> Installation Notes</h2>
1.Install <code>zsh</code>

2.Install <code>oh-my-zsh</code>

4.Install <code>zsh-completions</code>

3.Install <code>Adjust the Set </code>

In step 2 there is a <a href="https://github.com/ohmyzsh/ohmyzsh" target="_blank"><span style="color:#ff0000">reference</span></a> here. This is a useful framework in zsh

<h2>Adjust the Set</h2>
There are 140 theme of zsh in the directory <span style="color:#ffcc00;text-decoration:underline">.oh-my-zsh/themes/</span>

In the .zshrc, we can set 'ZSH_THEME=""' that can change the theme.

There are 271 plugins of zsh in the director <span style="color:#ffcc00;text-decoration:underline">.oh-my-zsh/plugins/</span> and there are lots of alias in these plugins, you can check when you try to use these implementation.

<span style="color:#ff0000">Note:</span>In <span style="color:#3333cc">.bashrc</span>, the "bind "\e[A": history-search-backward " and "bind "\e[B": history-search-forward" however; in <span style="color:#3333cc">.zsh</span> there are "bindkey "^[[A" history-search-backward" and "bindkey "^[[B" down-line-or-history". They are different.<br>
And bindkey is build-in of zsh


