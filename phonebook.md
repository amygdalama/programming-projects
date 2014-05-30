## Phonebook Command Line Tool
*Also copied from a Hacker School Friday Jobs Prep assignment created by Tom Ballinger and Alan O'Donnell*

Build a command line tool that manages phone books, via the interface below.

### Things that should work:

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

## More ideas
* make lookup the default command
* allow search by partial name - not just beginning of name
* allow `-b phonebook.rb` to occur anywhere in command
* case insensitive search
* make names work without using quotes
* add a config file where you can specify a default phone book to use. Add commands to edit this file without having to edit it manually
* implement a sql database backend if you didn't already
* implement a http backend (`phonebook lookup Tom -b 'http://mywebsite/phonebook'` etc.)
* Add tab completion