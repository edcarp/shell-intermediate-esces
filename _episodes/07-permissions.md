---
title: "Permissions"
teaching: 10
exercises: 0
questions:
- "Understanding file/directory permissions"
objectives:
- "What are file/directory permissions?"
- "How to view permissions?"
- "How to change permissions?"
- "File/directory permissions in Windows are different"
keypoints:
- "File permissions describe who and what can read, write, modify, and access a file."
- "Use `ls -l` to view the permissions for a specific file." 
- "Use `chmod` to change permissions on a file or directory."
---

Unix controls who can read, modify, and run files using *permissions*.

We'll discuss how Windows handles permissions at the end of the section:
the concepts are similar,
but the rules are different. (The examples in this lesson do work with Git Bash for Windows. But where control of permissions is crucial under Windows, further effort may be required.)

Every user has a unique user name. They also have an integer user ID.

Users can belong to any number of *groups*. Each group has a unique name and integer group IDs.

Every file and directory on a Unix computer belongs to *one owner* and *one group*.

For each file on the system,
every user falls into one of three categories:
the owner of the file,
someone in the file's group,
and everyone else.

For each of these three categories,
the computer keeps track of
whether people in that category can *read* the file;
*write* to the file; or *run* the file as a program. (In the case of directories, the latter has a different meaning - whether people in that category can *search* the directory.)

For example, if a file had the following set of permissions:

<table class="table table-striped">
<tr><td></td><th>user</th><th>group</th><th>all</th></tr>
<tr><th>read</th><td>yes</td><td>yes</td><td>no</td></tr>
<tr><th>write</th><td>yes</td><td>no</td><td>no</td></tr>
<tr><th>execute</th><td>no</td><td>no</td><td>no</td></tr>
</table>

it would mean that:

*   the file's owner can read and write it, but not run it;
*   other people in the file's group can read it, but not modify it or run it; and
*   everybody else can do nothing with it at all.

Permissions are revealed with `ls -l`, for example in the `exercise-data` directory:

~~~
$ ls -l
~~~
{: .bash}
~~~
$ ls -l
total 5
-rw-r--r-- 1 dbarker 1049089 18 Feb 16 17:40 numbers.txt
drwxr-xr-x 1 dbarker 1049089  0 Mar 21 09:06 populations/
drwxr-xr-x 1 dbarker 1049089  0 Feb 16 17:40 writing/
~~~
{: .output}

On the right side, we have the files'  names. On the left, we see permissions.

Let's have a closer look at one of those permission strings:
`-rw-r--r--`.
The first character tells us what type of thing this is:
'-' means it's a regular file,
while 'd' means it's a directory.

The next three characters tell us what permissions the file's owner has.
Here, the owner can read and write the file: `rw-`.
The middle triplet shows us the group's permissions.
If the permission is turned off, we see a dash, so `r--` means "read, but not write or execute".
The final triplet shows us what everyone who isn't the file's owner, or in the file's group, can do.
In this case, it's 'r--' again, so everyone on the system can look at the file's contents but do nothing else.

To change permissions, we use the `chmod` command
(whose name stands for "change mode").

In research contexts, removing write permission can help reduce the chance of accidental damage to important files.

This command removes write permission on the `numbers.txt` for all users:

~~~
$ chmod -w numbers.txt
~~~
{: .bash}

~~~
-r--r--r-- 1 dbarker 1049089 18 Feb 16 17:40 numbers.txt
~~~
{: .output}

Now, all users of the system can read the file but nothing else.

To restore write permission for the user who owns the file (only), the command is:

~~~
$ chmod u+w numbers.txt
~~~
{: .bash}

The 'u' signals that we're changing the privileges
of the user (i.e., the file's owner),
and `+w` means we should add write permission.
A quick `ls -l` shows us that it worked,
because the owner's permissions are now set to read and write:

~~~
-rw-r--r-- 1 dbarker 1049089 18 Feb 16 17:40 numbers.txt
~~~
{: .bash}

## What about Windows?

Those are the basics of permissions on Unix.
As we said at the outset, though, things work differently on Windows.
There, permissions are defined by access control lists,
or ACLs.
An ACL is a list of pairs, each of which combines a "who" with a "what".
For example,
you could give a user permission to append data to a file without giving  permission to read or delete it.

This is more flexible that the Unix model,
but it's also more complex to administer and understand on small systems.

{% include links.md %}
