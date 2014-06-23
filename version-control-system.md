# Make a Local Version Control System!

By [Rose Ames](https://github.com/rose)

Build a command line tool for storing and retrieving old versions of a project.  I made the steps below more detailed based on feedback from week 1.  But they're still only suggestions - feel free to do things differently!

## Part 1 - Basic backups
1. Single backup.  Make a command line tool that recursively copies everything in the current directory to a directory called .myvcs (which should be created if it doesn't already exist).  At this point it's ok to overwrite .myvcs if it already exists.
2. Snapshots.  Instead of putting everything directly into .myvcs, put the first backup into .myvcs/1, the next in .myvcs/2, and so on.  (I'll use 'snapshot' and 'backup' interchangeably from now on)
3. Reversion.  Add an option to your tool, so that you can revert to an earlier snapshot.  For example, `myvcs checkout 3` should copy the contents of .myvcs/3 into the current directory.
4. Latest.  Make it so `myvcs latest` reverts you to the highest existing snapshot.


## Part 2 - Metadata
1. (Warmup)  Current backup.  Make a file called .myvcs/head that keeps track of which backup you're currently 'using'.  It just needs to hold a single number, which will change every time you create a backup or checkout an old one.  `myvcs current` should print that number.
2. Logging dates.  However you decide to do it, store the date of each snapshot as it's created. `myvcs log` should print a list of the backups & their creation dates.
3. Messages.  Add a way to leave a note about each backup when it's created, for example `myvcs backup -m "add readme"`.  Alter `myvcs log` to show the message as well as the date for each backup.
4. Branches.  Here's the fun part!  Using the head data from in item 5, store the parent of each backup as it's made.  Then alter `myvcs log` to only print information about the current backup's ancestors.

#### Example/Explanation on branches
*(skip this if you understand what's required here)*

Suppose I'm working on a project and take 12 snapshots.  Then I think maybe I've made a design mistake and revert back to snapshot 7 to try something different.  I make 3 new backups, and then type `myvcs log`.  What should I see?

Well,  I'm not interested in the work that was done in snapshots 8-12.  Logically, the snapshot 'before' 13 was 7.  I want to see information about snapshots 13-15, and 1-7.  This isn't difficult to do.

When I check out 7, .myvcs/head should be altered to point at 7.  When I next create a snapshot, myvcs just needs to look in head to see what the new snapshot's parent is.  It then stores 13 in head, ensuring that 14 will have 13 as a parent (unless I change my mind and check out an older snapshot before the next time I back up).

`myvcs log`  should look at the current contents of head, print out the date &  message for the latest snapshot, then print its parent's data, then the parent's parent's, and so on until a snapshot with no parent is reached.


#### Notes on Metadata:

Item 1 is pretty easy, but don't skip it; you'll need it for number 4!

With Item 2, you're going to start storing per-backup metadata.  There are a few possible ways to do this.  You could create a separate metadata file for each branch, for example .myvcs/1.info would store all of the metadata about backup 1.

Or you could have a separate file for each type of data; for example, to complete Item 6 you could create .myvcs/dates that stores the date information for all the backups.

However you do it, remember that the user should never have to touch anything in .myvcs directly!  It only exists to make the command line tool able to do its jobs.


## More ideas / helpful resources
Post any other useful links or ideas you have here!
* I got this idea from the [Git Parable](http://tom.preston-werner.com/2009/05/19/the-git-parable.html).  It's got info about lots more git features than covered above - highly recommended.
* Add named branches.
* Front end. Put a simple front end on your project so the VCS can be administered from the web. Use any web framework you have to hand — you should be able to display the metadata, read log files and messages, and run commands from the browser. Keep it simple and functional.