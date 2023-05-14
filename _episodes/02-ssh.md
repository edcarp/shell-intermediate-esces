---
title: "Working Remotely"
teaching: 15
exercises: 0
questions:
- "How do I use '`ssh`' and '`scp`' ?"
objectives:
- "Learn what SSH is"
- "Learn how to work remotely using `ssh` and `scp`"
keypoints:
- "SSH is a secure means to access a remote Linux computer"
- "The 'ssh' and 'scp' utilities are secure alternatives to logging into, and copying files to/from remote machine"
- "'ssh' and 'scp' are essential for using remote Linux servers and
---
What if we want to run some commands on another machine,
such as the server in the basement that manages our database of experimental results?
To do this,
we have to first log in to that machine.
We call this a remote login.

Once our local client is connected to the remote server,
everything we type into the client is passed on, by the server, to the shell 
running on the remote computer.
That remote shell runs those commands on our behalf,
just as a local shell would,
then sends back output, via the server, to our client, for our computer to display.

The SSH protocol
uses several sophisticated, and heavily tested, encryption protocols
to ensure that outsiders can't see what's in the messages
going back and forth between different computers.

The remote login server which accepts connections from client programs
is known as the SSH daemon, `sshd`.

The client program we use to login remotely is
the secure shell
or `ssh`.

The `ssh` login client has a companion program called `scp`, think  (`s`)ecure `cp`, 
which allows us to copy files to or from a remote computer using the same kind of encrypted connection.

## A remote login using `ssh`

Depending on security settings on the remote server, we may have to be on the local network; or remotely
we may have to use the institution's VPN.

Then, to make a remote login, we issue the command `ssh username@computer` 
which tries to make a connection to the SSH daemon running on the remote computer we have specified.

After we log in,
we can use the remote shell to use the remote computer's files and directories.

Typing `exit` or Control-D
terminates the remote shell, and the local client program, and returns us to our previous shell.

In the example below,
the remote machine's command prompt is `moon>`
instead of just `$`.
To make it clearer which machine is doing what,
we'll indent the commands sent to the remote machine
and their output.

~~~
$ pwd
~~~
{: .bash}

~~~
/c/Users/dbarker/Desktop
~~~
{: .output}

~~~
$ ssh nelle@moon.euphoric.edu
Password: ********
~~~
{: .bash}

Assuming this connection works (this specific example will not!), any commands we issue,
for example `hostname`, `pwd`, `ls` or some scientific analysis software, will run on the
remote server. This will continue until we exit the remote shell, for example:

~~~
    moon> exit
~~~
{: .bash}

`pwd` confirms we are now running commands on the local computer again (not the remote server):

~~~
$ pwd
~~~
{: .bash}

~~~
/c/Users/dbarker/Desktop
~~~
{: .output}

## Copying files to, and from a remote machine using `scp`

To copy a file,
we specify the source and destination paths,
either of which may include computer names.
If we leave out a computer name,
`scp` assumes we mean the machine we're running on.
For example,
this command copies our latest results to the backup server in the basement,
printing out its progress as it does so:

~~~
$ scp results.dat nelle@backupserver:backups/results-2023-16-05.dat
Password: ********
~~~
{: .bash}

~~~
results.dat              100%  9  1.0 MB/s 00:00
~~~
{: .output}

Note the colon `:`, seperating the hostname of the server and the pathname of 
the file we are copying to.

Copying a whole directory betwen remote machines uses the same syntax as the `cp` command:
we just use the `-r` option to signal that we want copying to be recursively.
For example,
this command copies all of our results from the `backup` directory on the `backupserver` server to our laptop:

~~~
$ scp -r nelle@backupserver:backups ./backups
Password: ********
~~~
{: .bash}

{% include links.md %}
