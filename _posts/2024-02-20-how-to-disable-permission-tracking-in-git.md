Over and over google I to find this command that disable permission tracking in a git repository. Did it happen 50+ times already over the years? Or more?

Enough goggling, this is the command that makes my repo chmod-resistant:

`git config core.fileMode false`

After you've run it, you will not see the changes in permissions of files (i.e. after chmodding) as modifications recognized by Git.

