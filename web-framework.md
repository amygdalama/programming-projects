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
* Handle POST requests from forms
* HTTP Header Parsing
* Make the port a command-line option
* Add support for a template system such as jinja (python), jade (javascript), or erb (ruby)
* Use a database to store data across server restarts
* Make your web server Rack/WSGI/Ring-compliant
* Write tests!