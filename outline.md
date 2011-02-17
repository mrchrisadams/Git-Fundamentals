Hi there,

Introducing this talk.

The purpose behind this brown bag is to give an understanding of how git
works, so you can come to it with a fresh eye if you've been working
with SVN, or any other source control systems.

In this talk, 

 * we'll create a repo, 
 * make a few commits, 
 * branch and merge back in, 
 * making remotes and pushing changes

Explaining what's happening along the way.


Git is distributed, fast, built on surprisingly simple fundamentals.

!SLIDE 

Lets make our repo.

!SLIDE command

git init

!SLIDE command

.git


!SLIDE

!image

!SLIDE bullets incremental transition=fade

* every snapshot of your code made so far, stored as commits
* specific preferences for this project 
* info about any branches, latest commits and other remote repos 

!SLIDE

So long as you have the `.git` file, you can always regenerate a snapshot
of any previous point on a project.

!SLIDE command

git clone . ~/Backups/git-brown-bag.git

!SLIDE incremental

git clone ~/Backups/git-brown-bag.git brown-bag-talk
git clone git@code.headshift.com:drupal-project.git php-spagetti-code
git clone https://github.com/londonhackspace/Doorbot.git doorbot
git clone git://github.com/jquery/jquery-mobile.git jq-mobile

!SLIDE

Committing






