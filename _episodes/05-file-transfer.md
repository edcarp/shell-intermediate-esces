---
title: "Transferring Files"
teaching: 5
exercises: 0
questions:
- "How to use wget to transfer a file?"
objectives:
- "Learn what wget is"
- "Use wget to transfer a remote file to your local computer"
keypoints:
- "There are multiple ways to copy remote files at the command-line."
- "These may be used to simply transfer one file, or to mirror a whole Web site."
- "Compared to using a Web browser to access and save files, these allow greater opportunities for automation."
---

Many of us use remote repositories with `git` (e.g.  GitHub). This allows us to download code or
other files written by colleagues.

What about files that do not exist in a git repository? If we wish to download online files from the shell, we can use tools such as Wget.

## Wget

Wget is a simple tool developed for the GNU Project that downloads files with the HTTP, HTTPS and FTP protocols. It is widely used by Unix-like users and is available with most Linux distributions. (However, it is not part of Git Bash for Windows.)

To download this lesson (located at https://edcarp.github.io/shell-extras/03-file-transfer/index.html) from the web via HTTP we can simply type:

~~~
$ wget https://edcarp.github.io/shell-extras/03-file-transfer/index.html
~~~
{: .bash}

~~~
XXX output XXX
--2021-05-29 02:12:18—  
https://carpentries-incubator.github.io/shell-extras/03-file-transfer/index.html
Resolving carpentries-incubator.github.io (carpentries-incubator.github.io)... 185.199.111.153, 185.199.110.153, 185.199.109.153, ...
Connecting to carpentries-incubator.github.io (carpentries-incubator.github.io)|185.199.111.153|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 22467 (22K) [text/html]
Saving to: ‘index.html’
index.html        100%[===================>]  21.94K  --.-KB/s    in 0.003s  

2021-05-29 02:12:19 (6.35 MB/s) - ‘index.html’ saved [22467/22467]
~~~
{: .output}
  
## Other commands

Alternatively, we can use `curl`, which supports a much larger range of protocols including common mail based protocols like pop3 and smtp. Or we might use `lftp`.

Please refer to the man pages by typing `man wget`, `man curl`, and `man lftp` in the shell for more information.