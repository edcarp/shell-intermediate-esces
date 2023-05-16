---
title: "(Re)Introducing the Shell"
teaching: 5
exercises: 0
questions:
- "What is a command shell and why would I use one?"
objectives:
- "Explain how the shell relates to the keyboard, the screen, the operating system, and users' programs."
- "Explain when and why command-line interfaces should be used instead of graphical interfaces."
keypoints:
- "A shell is a program whose primary purpose is to read commands and run other programs."
-  "This lesson uses Bash, the default shell in many implementations of Unix."
-  "Programs can be run in Bash by entering commands at the command-line prompt."
- "The shell's main advantages are its high action-to-keystroke ratio, its support for
automating repetitive tasks, and its capacity to access networked machines."
- "The shell's main disadvantages are its primarily textual nature and how
cryptic its commands and operation can be."
---

### The Shell

This course assumes you have either taken our ur [introductory shell course](https://edcarp.github.io/shell-novice-esces) already, or have broadly similar background knowledge. Here is a reminder of what we mean by the shell.

The shell is a program where users can type commands.
With the shell, it's possible to invoke complicated programs like climate modeling software
or simple commands that create an empty directory with only one line of code.
The most popular Unix shell is Bash.
Bash is the default shell on most modern implementations of Unix and in most packages that provide
Unix-like tools for Windows.

The grammar of a shell allows you to combine existing tools into powerful
pipelines and handle large volumes of data automatically. Sequences of
commands can be written into a *script*, improving the reproducibility of
workflows.

In addition, the command line is often the easiest way to interact with remote machines
and supercomputers.
Familiarity with the shell is near essential to run a variety of specialized tools and resources
including high-performance computing systems.
As clusters and cloud computing systems become more popular for scientific data crunching,
being able to interact with the shell is becoming a necessary skill.
We can build on the command-line skills covered here
to tackle a wide range of scientific questions and computational challenges.


## Phillipa's Pipeline: A Typical Problem



Phillipa Frogg, an ecologist, wants to use the [Living Planet Index dataset](https://www.livingplanetindex.org/)
to help her with her research. However, she is unable to use the raw data directly; instead, she has to
edit the data so it's in a suitable format for her to make best use of. Although she could do this by hand in
a text editor, this would be laborious, time-consuming, and error-prone. With the shell, Phillipa can instead assign her computer this mundane task while she focuses
her attention on writing her latest paper.

The next few lessons will explore the ways Phillipa can achieve this.
More specifically,
they explain how she can use a command shell to run shell programs,
and use loops to automate the repetitive steps of entering file names,
so that her computer can work while she writes her paper.

As a bonus,
once she has put a processing pipeline together,
she will be able to use it again whenever she collects more data.

In order to achieve her task, Phillipa needs to know how to:
- navigate to a file/directory
- create a file/directory
- check the length of a file
- chain commands together
- retrieve a set of files from a remote location
- connect to a powerful Linux server
- iterate over files
- run a shell script containing her pipeline
- control file permissions, so colleagues can read her work but not alter it

{% include links.md %}
