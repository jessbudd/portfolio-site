---
title: How to Set Up Git Aliases for Faster Development
date: 2019-08-13
meta: Testing meta description
---

~/.bash_profile

 

In your home user folder

 

<pre>
<span class="green">alias</span> gs='git status '

<span class="green">alias</span> ga='git add '

<span class="green">alias</span> gc='git commit -m '

<span class="green">alias</span> gp='git push'

<span class="green">alias</span> gb='git branch '

<span class="green">alias</span> go='git checkout '

<span class="green">alias</span> gpl='git pull'

<span class="green">alias</span> gl='git log'

<span class="green">alias</span> got='git '

<span class="green">alias</span> get='git '
</pre>

The go abbreviation for git checkout is very useful, allowing me to type:

go <branch>
to checkout a particular branch.

Also, I often mistype git as get or got so I created aliases for them too.

 

Another trick is to make an alias for folders you navigate to often, for example this website which is made with a static site generator.

 

 

Make your /bash_forile file if you don’t yet have one

cd ~/ ls -A

If .bash_profile exists, you can open it with open .bash_profile (or code .bash_profile if you happen to be using VS Code as a text editor, which I highly recommend).

If it doesn’t exist, run touch .bash_profile to create it, then open it.