---
title: Shell Variables
teaching: 15
exercises: 0
questions:
- "How are variables set and accessed in the Unix shell?"
objectives:
- "Understand how variables are implemented in the shell"
- "Explain how the shell uses the `PATH` variable to search for executables"
- "Read the value of an existing variable"
- "Create new variables and change their values"
keypoints:
- "The `PATH` variable defines the shell's search path"
- "Variables are assigned using \"`=`\" and recalled using the variable's name prefixed by \"`$`\""
---

The shell is just a program, and like other programs, it has variables.
Those variables control its execution,
so by changing their values
you can change how the shell and other programs behave.

Let's start by running the command `set` and looking at some of the variables in a typical shell session:

~~~
$ set | less
~~~
{: .bash}

What you see is highly system-dependent. As an example, the start of the output might look something like this:

~~~
ACLOCAL_PATH=/mingw64/share/aclocal:/usr/share/aclocal
ALLUSERSPROFILE='C:\ProgramData'
APPDATA='C:\Users\nelle\AppData\Roaming'
BASH=/usr/bin/bash
BASHOPTS=cmdhist:complete_fullquote:expand_aliases:extquote:force_fignore:hostcomplete:interactive_comments:login_shell:progcomp:promptvars:sourcepath
BASH_ALIASES=()
BASH_ARGC=()
BASH_ARGV=()
BASH_CMDS=()
BASH_LINENO=()
BASH_SOURCE=()
BASH_VERSINFO=([0]="4" [1]="4" [2]="23" [3]="1" [4]="release" [5]="x86_64-pc-msys")
BASH_VERSION='4.4.23(1)-release'
COLUMNS=80
COMMONPROGRAMFILES='C:\Program Files\Common Files'
COMPLETION_PATH='C:/Program Files/Git/mingw64/share/git/completion'
COMPUTERNAME=MY-COMPUTER
COMP_WORDBREAKS=$' \t\n"\'@><=;|&(:'
COMSPEC='C:\WINDOWS\system32\cmd.exe'
CONFIG_SITE=/etc/config.site
CommonProgramW6432='C:\Program Files\Common Files'

~~~
{: .output}

Every variable has a name.
By convention, variables that are always present are given upper-case names. All shell variables' values are strings.

Some variables (like `PATH`) store lists of values. To see the value stored in your `PATH` variable, do:

~~~
$ echo $PATH
~~~
{: .bash}

In this case, the convention is to use a colon ':' as a separator.
If a program wants the individual elements of such a list,
it's the program's responsibility to split the variable's string value into pieces.

## The `PATH` Variable

Let's have a closer look at that `PATH` variable.
Its value defines the shell's search path,
i.e., the list of directories that the shell looks in for runnable programs
when you type in a program name without specifying what directory it is in.

The rule it uses is simple:
the shell checks each directory in the `PATH` variable in turn,
looking for a program with the requested name in that directory.
As soon as it finds a match, it stops searching and runs the program.

To show how this works,
here are the components of the above `PATH` listed one per line:

~~~
/c/Users/nelle/bin
/mingw64/bin
/usr/local/bin
/usr/bin
/bin
/mingw64/bin
/usr/bin
/c/Users/nelle/bin
/c/Program Files (x86)/Common Files/Oracle/Java/javapath
/c/Program Files (x86)/Common Files/Intel/Shared Libraries/redist/intel64/compiler
/c/WINDOWS/system32
/c/WINDOWS
/c/WINDOWS/System32/Wbem
/c/WINDOWS/System32/WindowsPowerShell/v1.0
/c/WINDOWS/System32/OpenSSH
/cmd
/c/Users/nelle/AppData/Local/anaconda3
/c/Users/nelle/AppData/Local/anaconda3/Library/mingw-w64/bin
/c/Users/nelle/AppData/Local/anaconda3/Library/usr/bin
/c/Users/nelle/AppData/Local/anaconda3/Library/bin
/c/Users/nelle/AppData/Local/anaconda3/Scripts
/c/Users/nelle/AppData/Local/Microsoft/WindowsApps
/c/Users/nelle/AppData/Local/Programs/Microsoft VS Code/bin
/usr/bin/vendor_perl
/usr/bin/core_perl
~~~
{: .output}

Let's say there are two programs called `analyze`,
in two different directories:
`/bin/analyze` and 
`/c/Users/nelle/bin/analyze`.
Since the shell searches the directories in the order they're listed in `PATH`,
it finds `/bin/analyze` first and runs that.

## Showing the Value of a Variable

Let's show the value of the variable `HOME`:

~~~
$ echo HOME
~~~
{: .bash}

~~~
HOME
~~~
{: .output}

That just prints "HOME", which isn't what we wanted.
Let's try this instead:

~~~
$ echo $HOME
~~~
{: .bash}

~~~
/c/Users/nelle
~~~
{: .output}

The dollar sign tells the shell that we want the *value* of the variable
rather than its name.

This works just like wildcards:
the shell does the replacement *before* running the program we've asked for.
Thanks to this expansion, what we actually run is `echo /c/Users/nelle`,
which displays the right thing.

## Creating and Changing Variables

Creating a variable is easy&mdash;we just assign a value to a name using "=", without any spaces either side:

~~~
$ SECRET_IDENTITY=Daniel
$ echo $SECRET_IDENTITY
~~~
{: .bash}

~~~
Daniel
~~~
{: .output}

To change the value, just assign a new one:

~~~
$ SECRET_IDENTITY=Chris
$ echo $SECRET_IDENTITY
~~~
{: .bash}

~~~
Chris
~~~
{: .output}

If we want to set some variables automatically every time we run a shell,
the can go in files called `.bashrc` and/or `.bash_profile` in our home directory.
(The '.' character at the front prevents `ls` from listing this file
unless we specifically ask it to using `-a`.)

For example, this provides a mechanism to add custom software to the search path so it can be run like
any other command.

{% include links.md %}
