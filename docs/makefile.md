# Makefile
- Reference
[https://en.wikipedia.org/wiki/Makefile](https://en.wikipedia.org/wiki/Makefile)
[https://opensource.com/article/18/8/what-how-makefile](https://opensource.com/article/18/8/what-how-makefile)

Make is an Unix automation utility. It requires a 'Makefile', which contains shell command with specific structure.
A makefile consists of rules in the following form
```
target: dependencies
    system command(s)
```

- A makefile is executed with the make command, e.g. make [options] [target1 target2 ...]
- Makefiles contain five kinds of things: explicit rules, implicit rules, variable definitions, directives, and comments.

    An explicit rule says when and how to remake one or more files, called the rule's targets. It lists the other files that the targets depend on, called the prerequisites of the target, and may also give a recipe to use to create or update the targets.
    An implicit rule says when and how to remake a class of files based on their names. It describes how a target may depend on a file with a name similar to the target and gives a recipe to create or update such a target.
    A variable definition is a line that specifies a text string value for a variable that can be substituted into the text later.
    A directive is an instruction for make to do something special while reading the makefile such as reading another makefile.
    ‘#’ in a line of a makefile starts a comment. It and the rest of the line is ignored.



## Flask local server
```
export FLASK_APP:=app_main.py
export FLASK_DEBUG:=True

flask_run:
    . ../bin/activate;flask run;
```