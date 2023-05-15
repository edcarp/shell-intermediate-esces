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
- "Compared to using a Web browser to access and save files, these allow greater opportunities for automation."
---

Many of us use remote repositories with `git` (e.g.  GitHub). This allows us to download code or
other files written by colleagues.

What about files that do not exist in a git repository? If we wish to download online files from the shell, we can use tools such as Wget.

## Wget

Wget is a simple tool developed for the GNU Project that downloads files with the HTTP, HTTPS and FTP protocols. It is widely used by Unix-like users and is available with most Linux distributions. (However, it is not part of Git Bash for Windows.)

To download this lesson (located at https://edcarp.github.io/shell-intermediate-esces/05-file-transfer/index.html) from the Web, we can simply type:

~~~
$ wget https://edcarp.github.io/shell-intermediate-esces/05-file-transfer/index.html
~~~
{: .bash}

We will see something similar to this:

~~~
--2023-05-15 08:08:03--  https://edcarp.github.io/shell-intermediate-esces/05-file-transfer/index.html
Resolving edcarp.github.io (edcarp.github.io)... 185.199.110.153, 185.199.108.153, 185.199.109.153, ...
Connecting to edcarp.github.io (edcarp.github.io)|185.199.110.153|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15409 (15K) [text/html]
Saving to: ‘index.html’

index.html                    100%[=================================================>]  15.05K  --.-KB/s    in 0.001s

2023-05-15 08:08:03 (20.5 MB/s) - ‘index.html’ saved [15409/15409]
~~~
{: .output}

We can then view or edit `index.html` using the usual tools, for example `cat`, `nano` or `head`. We can also double-click it in our laptop GUI to open it in a Web browser.
  
## Other commands

Alternatively, we can use `curl`, which supports a much larger range of protocols including common mail based protocols like pop3 and smtp. Or we might use `lftp`.

Please refer to the man pages by typing `man wget`, `man curl`, and `man lftp` in the shell for more information.

## Applications

`wget`, `curl` and `lftp` allow a degree of automation that is not possible using a Web browser.
Possible applications include:

- Downloading large files direct to a server (rather than via your laptop)
- Mirroring a Web site
- Automatically updating local datafiles to keep up-to-date with a top copy online.
