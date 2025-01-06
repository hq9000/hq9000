Today I encountered a behavior of `mkdir` which I found a bit surprising.

As you know, `-p` makes `mkdir` ignore if directory already exists:

```
-p, --parents
    no error if existing, make parent directories as needed
```

it works fine for symbolic link too as shown here:


```shell
$ mkdir target
$ ln -s target link
$ mkdir -p link
$ echo $?
0
$ ls -la
total 12
drwxr-xr-x  3 sergey sergey 4096 Jan  6 18:35 .
drwxr-x--- 15 sergey sergey 4096 Jan  6 18:34 ..
lrwxrwxrwx  1 sergey sergey    6 Jan  6 18:35 link -> target
drwxr-xr-x  2 sergey sergey 4096 Jan  6 18:35 target
$
```

however, and that is what surprised me at first, if a link happens to be a _broken_ link, the `-p` stops working:

```shell
$ rmdir target
$ mkdir -p link
mkdir: cannot create directory ‘link’: File exists
```

After some thinking, I realize that there can be no way to ignore existing directory as the only object we have is a link pointing nowhere, is it a directory? Or a file? So the fact that it fails should not have been so surprising. On the other hand, the error message could have been a bit more informative.