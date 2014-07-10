# Note taking app

Let's write a note taking app! Notes need to be saved to a git repo, so as to learn to integrate our code with existing services, which is a big part of delivering applications in "the real world". If you don't like git, you could try using Dropbox or email as an alternative.

## Level 1 - local files only

* create a command-line tool that allows you to input a title for the note and some text as its contents. Save the contents in a file on disk and use the name that the user input as the name of the file.
* add a command that lists all the notes you have saved. from the list, you should be able to select one of the notes to display its contents, edit or delete it.
* add tags to a note and save them as metadata. There's no limit on how many tags a note can have.
* allow filtering by tag.

## Level 2 - git

* download and install a git library for your language. Libs for python , ruby .
* modify your command line tool so that it initializes a git repo on a new empty dir and creates the corresponding github repo before allowing you to save notes. it should print an error message when you try a command on a directory that is not a note repository.
* add a new file to the repo after creating a new note; commit after every edit; run git rm after deleting a file. After any of those, push to Github.
* add a search command: input a string and list the name of all notes that match. You can use the git grep command for this.

## Final Boss - more ideas

* instead of typing your notes directly on the terminal, try launching an editor and getting the contents from it. git does this for writing commit messages.
* integrate with more git commands. My favorite: revert a note to a version that contains a given string; that is, you need to search for a string in all of the versions of a note, not just the current one. You can use the git pickaxe for this, which you can access via git log -S
* input your notes in markdown and export them to html
* integrate with more services! you could add a due date as metadata and add an event to your Google calendar, for example.

## Useful Links

* [The git pickaxe](http://gitfu.wordpress.com/2008/06/03/the-pickaxe-finding-changes-was-never-easier/)
* Markdown for [ruby](https://github.com/vmg/redcarpet) , [python](https://pypi.python.org/pypi/Markdown).