## Link Shortener
*Copied from a Hacker School Friday Jobs Prep assignment created by Tom Ballinger and Alan O'Donnell*

Build a website that allows you to submit a link, then gives you a new, hopefully shorter url to use for that link.

* Build a webpage you can visit in a web browser.
* Make a form on this webpage
* Make submitting the form return a new link that can later be used to get back to that site

More things to do:
* Display data on how much that link gets used
* Make that data private to whoever made the original shortened link
* Make shortened links not guessable
* Deploy your site somewhere besides localhost
* Graphically display the click data
* Load test your server - can you take 100 posts per second? 1000 shortened link GETs per second? How many redirections or shortens can your site do per second? What was the bottleneck?
* Make a bookmarklet that gives the user the shortened version of a link without leaving a page.
* Style your page a bit
* Update your link click stats in realtime (no refresh required)
* Break down link click stats by browser
* Build an api for people to use to access their click data

## Phonebook Command Line Tool
*Also copied from a Hacker School Friday Jobs Prep assignment created by Tom Ballinger and Alan O'Donnell*

Build a command line tool that manages phone books, via the interface below.

Things that should work:

    $ phonebook create hsphonebook.pb
    created phonebook hsphonebook.pb in the current directory
    $ phonebook lookup Sarah -b hsphonebook.pb # error message on no such phonebook
    Sarah Ahmed 432 123 4321
    Sarah Apple 509 123 4567
    Sarah Orange 123 456 7890
    $ phonebook add 'John Michael' '123 456 4323' -b hsphonebook.pb # error message on duplicate name
    $ phonebook change 'John Michael' '234 521 2332' -b hsphonebook.pb # error message on not exist
    $ phonebook remove 'John Michael' -b hsphonebook.pb # error message on not exist
    $ phonebook reverse-lookup '312 432 5432'

You should also write tests. (<--- this is important, it's half of the assignment!)

Optional extra tasks when you're done:
* make lookup the default command
* allow search by partial name - not just beginning of name
* allow `-b phonebook.rb` to occur anywhere in command
* case insensitive search
* make names work without using quotes
* add a config file where you can specify a default phone book to use. Add commands to edit this file without having to edit it manually
* implement a sql database backend if you didn't already
* implement a http backend (`phonebook lookup Tom -b 'http://mywebsite/phonebook'` etc.)
* Add tab completion

## Web Framework

*Thanks to [Rose Ames](https://github.com/rose) for submitting and writing up the details for this project!*

Make a server that listens for HTTP requests & calls different functions for different urls.  The steps below are just suggestions; feel free to do it your way!

Part 1 - make a webserver
* Using your language's http library, make a server that listens on a certain port (say 1924) and returns a string of text.  Check that your browser displays that text when you go to localhost:1924.
* Instead of fixed text, have your program look for a file called index.html in its current directory.  Return its contents, or a 404 error if the file doesn't exist.
* Read the url the browser sends and serve the appropriate file - for example, localhost:1924/foo.html should look for foo.html in the current directory.
* Now handle things like localhost:1924/foo/bar/baz.html by searching through directories.  (Bonus:  What's the security flaw here?)

Part 2 - turn your server into a framework
* Without destroying any of the previous functionality, define a special url that returns the result of a function.  For example, define a function called helloworld, and make it so going to localhost:1924/hello.html calls that function instead of looking for a file.
* Keep a list or hash table of these special urls, and the function associated with each.  Check each incoming url to see if it's in the table before looking for a file.
* Parse the url, so that part of it determines what function gets called, and another part defines the argument(s) to the function - for example, localhost:1924/user/blarg could return information about the user named Blarg.
* Turn your framework into a module or library, so someone can import it into their program.  Tell them how to write a function and associate it with a url.

More ideas
* Add (optional) additional feature ideas here!
* Handle POST requests from forms
* HTTP Header Parsing
* Make the port a command-line option
* Add support for a template system such as jinja (python), jade (javascript), or erb (ruby)
* Use a database to store data across server restarts
* Make your web server Rack/WSGI/Ring-compliant
* Write tests!
