:
 Git is a simple, but extremely powerful system. 

Notes taken from the [Git Parable](http://tom.preston-werner.com/2009/05/19/the-git-parable.html)

!SLIDE

> Until you understand the concepts upon which Git is built, you’ll feel like a stranger in a foreign land.

!SLIDE

> Snapshots, like save points in a video game, are really what you care about when you need to interact with a VCS. What if you could take snapshots of your codebase at any time and resurrect that code on demand?

!SLIDE

> You start your project in a directory named working. As you code, you try to write one feature at a time. When you complete a self-contained portion of a feature, you make sure that all your files are saved and then make a copy of the entire working directory, giving it the name snapshot-0. After you perform this copy operation, you make sure to never again change the code files in the new directory.

!SLIDE

> To make it easy to remember what changes you made in each snapshot, you add a special file named message to each snapshot directory that contains a summary of the work that you did and the date of completion. By printing the contents of each message, it becomes easy to find a specific change that you made in the past, in case you need to resurrect some old code.


!SLIDE

> Since the release, you’ve created 10 new snapshots. This new work must not be included in the 1.0.1 bug fix version you now need to create. To solve this, you copy snapshot-99 to working so that your working directory is at exactly the point where Version 1.0 was released. A few swift lines of code and the bug is fixed in the working directory.

!SLIDE

> By looking at your code history as a tree, solving the problem of ancestry becomes trivial. All you need to do is include the name of the parent snapshot in the message file you write for each snapshot. Adding just a single upstream pointer will enable you to easily and accurately trace the history of any given snapshot all the way back to the root.

!SLIDE 

> But like everything good in life, there is a price to be paid. Each time you create a new snapshot, you must remember that the new snapshot becomes the latest on its branch. Without this information, switching to a new branch would become a laborious process indeed.

!SLIDE 

> The least amount of information necessary to identify a branch is the location of the latest snapshot on that branch. If you need to know the list of snapshots that are part of the branch you can easily trace the parentage.

!SLIDE

> Storing the branch names is trivial. In a file named branches, stored outside of any specific snapshot, you simply list the name/snapshot pairs that represent the tips of branches. To switch to a named branch you need only look up the snapshot for the corresponding name from this file.

!SLIDE

> While constructing the snapshot message for the merge, you realize that this snapshot is special. 
Instead of just a single parent, this merge snapshot has two parents! The first parent is your latest on the ‘math’ branch and the second parent is Zoe’s latest on her ‘math’ branch. 

The merge snapshot doesn’t contain any changes beyond those necessary to merge the two disparate parents into a single codebase.

Once you complete the merge, Zoe fetches all the snapshots that you have that she does not, which include your development on the ‘math’ branch and your merge snapshot. Once she does this, both of your histories match exactly!


!SLIDE

> Second, snapshots will no longer be named with simple numbers. Instead, you’ll use the contents of the message file to produce a hash. This hash will be guaranteed to be unique to the snapshot since no two messages will ever have the same date, message, parent, and author. To make sure everything goes smoothly, you both agree to use the SHA1 hash algorithm that takes the contents of a file and produces a 40 character hexadecimal string. You both update your histories with the new technique and instead of clashing ‘snapshot-114’ directories, you now have distinct directories named ‘8ba3441b6b89cad23387ee875f2ae55069291f4b’ and ‘db9ecb5b5a6294a8733503ab57577db96ff2249e’.

!SLIDE

> This point is important enough to warrant repeating. A snapshot is identified by a SHA1 that uniquely identifies it (and its parent). These snapshots can be created and moved around between computers without losing their identity or where they belong in the history tree of a project. 

!SLIDE

You remember that the SHA1 hash produces a short string that is unique for a given file contents. Starting with the very first snapshot in the project history, you start a conversion process. First, you create a directory named objects outside of the code history. 

!SLIDE
Starting with the very first snapshot in the project history, you start a conversion process. 
First, you create a directory named objects outside of the code history. 
Next, you find the most deeply nested directory in the snapshot. 
Additionally, you open up a temporary file for writing. For each file in this directory you perform three steps. 

  Step 1: Calculate the SHA1 of the contents. 
  Step 2: Add an entry into the temp file that contains the word ‘blob’ (binary large object), the SHA1 from the first step, and the filename. 
  Step 3: Copy the file to the objects directory and rename it to the SHA1 from step 1. 

Once finished with all the files, find the SHA1 of the temp file contents and use that to name the temp file, also placing it in the objects directory.
 
