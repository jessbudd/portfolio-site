---
title: How to Set Up Git Aliases for Faster Development
date: 2019-08-13
meta: Testing meta description
---

It was at least a year ago that I first saw someone in a tutorial using an alias for their git commands. I thought at the time it was something I should set up, but not being incredibly comfortable in the command line, I didn't look into it much further.

For those that haven't heard of aliases before, they are like shortcodes to a command in the terminal. 

For example instead of typing `git push` whenever I want to push my repo, I can assign a shortcode for that command and simply type `gp` to do the same thing.

Magic!

This week I've been using git on the command line extensively, so I thought it was about time that I set them up. I found a lot of stack-overflow posts on how to create an alias on mac and the most simple to understand gave me a format to follow. 

So I typed the following into the command line window I had open for my project.



 

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

I immediately tested my aliases with a `gs`.

It worked! Huzzah! 

I went along my merry away. 

Until the next day, when I got my dev environment all set up again and tried to use my new aliases. They didn't work.

    -bash: gs: command not found

Sad face.

It turns out I only created temporary aliases that existed in that window only. To create global aliases that persisted in all future windows, I needed to add them to my `.bash_profile` file.

~/.bash_profile

 

In your home user folder

The go abbreviation for git checkout is very useful, allowing me to type:

go <branch>
to checkout a particular branch.

Also, I often mistype git as get or got so I created aliases for them too.

 

Another trick is to make an alias for folders you navigate to often, for example this website which is made with a static site generator.

 

 

Make your /bash_forile file if you don’t yet have one

cd ~/ ls -A

If .bash_profile exists, you can open it with open .bash_profile (or code .bash_profile if you happen to be using VS Code as a text editor, which I highly recommend).

If it doesn’t exist, run touch .bash_profile to create it, then open it.