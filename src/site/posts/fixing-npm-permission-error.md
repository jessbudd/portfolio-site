---
title: Fixing npm EACCESS error (permission denied, mkdir)
date: 2019-09-15
meta: 
---


Nodejs and NPM have made life so easier. If you use Gulp toolkit with it I am sure you love it 😍

However, I was frequently getting errors along the lines of <code> Error: EACCES: permission denied, mkdir </code>

<code>$ npm install</code>

The first thing I tried was running it with sudo. No dice.

<code>
$ sudo npm install
</code>

I checked and updated my versions of node and npm to the latest stable versions. Still no luckk.

<code>
$ sudo npm update
$ sudo npm install
</code>

I kept getting the same errors. I did some googling and found adding some terms worked for quite a few people. So I tried:

<code>$ sudo npm install --unsafe-perm=true --allow-root</code>

Unfortunately, it didn't work for me. I went on for more googling and came across [this npm community thread](https://npm.community/t/global-installs-sudo-npm-i-g-fail-on-mac-after-6-5-upgrade-works-fine-after-6-4-1-downgrade/4082/27) that talked about changing the permissions of the folder.

<code>
sudo chown -R $(whoami) ~/.npm 
sudo chown -R $(whoami) /usr/local/lib 
sudo chown -R $(whoami) /usr/local/bin
</code>

And it worked, I'm one happy chappy and continue on with my course. I wanted to document this for future me next time!

