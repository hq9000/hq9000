Let me guess: you ended up with tons of untracked files in your working directory.
Now it's a nightmare to actually see what to stage for your future commit? Correct?

This is how you solve it:

`git clean -f -d`

this little beast removes all untracked files, including directories, forcefully.

Importantly, it works in the scope of your current directory (which is not necessarily the root of your repo). Therefore, to make the untracked files removed from every corner of your repo, you run it while being in the repo's root.

If it sounds a bit too scary, run `git clean -f -d -n` (the `-n` means "dry run", makes it only print out what it _would_ remove). Example:

```shell
$ git clean -f -d -n
Would remove 2022-07-19-vega-visualization-performance-benchmark.md_upd
Would remove 2024-02-20-how-to-clean-your-git-working-directory.md
Would remove 2024-02-20-how-to-disable-permission-tracking-in-git.md
```

What about staged but not yet commited files? If you have a file in staging area, it's already considered "tracked" and therefore will not be removed. Proof:

```
$ touch example_to_hide_in_staging.txt
$ git clean -f -d -n
Would remove example_to_hide_in_staging.txt
$ git add example_to_hide_in_staging.txt 
$ git clean -f -d -
$
```


Have fun!


