---
title: How I Set Up Bash Aliases for Git
# subtitle: And speed up your development
date: 2019-08-13
meta: Testing meta description
---

It was at least a year ago that I first saw someone in a tutorial using an alias for their git commands. I thought at the time it was something I should set up, but not being incredibly comfortable in the command line, I didn't look into it much further.

## What's an alias?

For those that may not have heard of aliases before, they're like shortcut commands in your terminal. You type the shortcut in place of typing the whole command.

For example instead of typing `git push` whenever I want to push my repo, I can assign a shortcode for that command and simply type `gp` (or whatever shortcut I set) to do the same thing.

Magic!

## Setting up an alias

This week, thinking it was about time I set up these aliases, I went off to google. I found a bunch of posts on how to create git aliases like [this one](https://stackoverflow.com/questions/2553786/how-do-i-alias-commands-in-git) and [this one](https://githowto.com/aliases), but got a little overwhelmed by the different options and as with most tutorials they assumed a fair bit of up front knowledge. 

Following the most simple format example, I typed my most common git actions into the command line window I already had open for my current project.
 

<pre>
<span class="green">alias</span> gs='git status '

<span class="green">alias</span> ga='git add '

<span class="green">alias</span> gc='git commit -m '

<span class="green">alias</span> gp='git push'

<span class="green">alias</span> gb='git branch '

<span class="green">alias</span> go='git checkout '

<span class="green">alias</span> gm='git merge '

<span class="green">alias</span> gpl='git pull'

<span class="green">alias</span> gl='git log'

</pre>

I then tentatively tested my shiny new aliases with a `gs`. 

And it worked! Huzzah! 

I went along my merry away. 

Until the next day, when I got my dev environment up again and tried to use my new aliases. They didn't work.

    -bash: gs: command not found

_Sad face_.


## Setting up an alias _globally_

It turns out I had only created temporary aliases that existed in that sinlge CLI window only. To create global aliases that would persist in all future windows I needed to add them to my `.bash_profile`.

On a mac, the `.bash_profile` file will be located in your home username folder. This was a hidden file, so I needed to show all hidden files by pressing `CMD + Shft + . ` to find it.

So in my `.bash_profile` I typed the exact same code as I'd typed the day before and saved the file. I closed down all my terminal windows and tested the alias in a fresh window and they worked.  

 
## Other methods

Over the next couple days (thanks to twitterverse) I found there are possibly better ways to do this. For example Atlassian has a good article that describes [how to set up your aliases through the gitconfig file](https://www.atlassian.com/git/tutorials/git-alias). Another fender mentioned putting the git aliases in a seperate alias file and then referencing that in your .bashrc file.

I'm sure there are good reasons to choose one method over the other, but for now I'm happy with the way I've done mine.