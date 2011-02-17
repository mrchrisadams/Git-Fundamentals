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

![git-repo](git-repo.png)

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

Committing.

!SLIDE 

Important concepts:

* hashing
* walking the tree
* staging and the index

!SLIDE

Hashes are really handy.

!SLIDE center

Data
  
!SLIDE

(very clever crypto voodoo) 

!SLIDE 

l0beec7b5ea3f0fdbc95d0dd47f3c5bc275da8a33

!SLIDE 

### Ambiguous 

## "give me file index.html"

### Unambiguous

## "give me file 5b5beb89ba449a9271b3c34d44b529d2a2633235"

!SLIDE bullets

* if contents changes, checksum changes
* super quick way for checking if a file has changed

!SLIDE 

## "give me blob 5b5beb89ba449a9271b3c34d44b529d2a2633235"

![blob](blob.png)

!SLIDE 

## Wait. How do we know what a file is called if we're just tracking
contents?

!SLIDE 

## Hashes work for lists too. 
## This is how we link file contents (blobs) to
file names.

![tree](tree.png)

!SLIDE center

# An example commit

!SLIDE incremental transition=slide

![objects-finder](objects-finder.png)

!SLIDE incremental transition=slide

![objects-example](objects-example.png)

!SLIDE incremental transition=slide

![objects-overlayed](objects-overlayed.png)

Each commit describes the whole project tree.
The contents of each file is verified by hash at each step.
Every file of every version up to now is already on your computer,
inside .git

!SLIDE

A second look at the commit.

![commit](commit.png)

!SLIDE

Hashes instead of numbers, allow for easier branching.





