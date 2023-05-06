---
title: git for musicians! My approach for versioning projects
---

Being both a musician and a software engineer, I always felt that these two areas are almost completely separated. My developer skill-set seemed to have little to no use for my work as a musician. Which is a pity considering how cool it would be if there was some kind of a sinergy across these two sides of my life.

Recently, though, I have found a useful use-case of something I previously used for my development work for my music production.

## meet Git for music production

Did you notice yourself creating a dozen of versions of your project? Are the names like this familiar to you? 

`my-cool-song-new-vocals-brighter-mix-4.rpp`

Did you ever feel frustrated about unmanageability of all this and how sloppy you project directory ends up looking?

This version nightmare problem for software people has a solid and well-recognized solution: version control systems. Such as ["git"](https://git-scm.com/), which is not only the most widely used one in the industry, but also completely free, open source and cross platform (that is working flawlessly on Win/Mac/Linux).

I use Reaper, and instead of creating dozens of copies of my project file (`my-cool-song.rpp`), such as `my-cool-song-new-vocals-brighter-mix-4.rpp`, I simply initialize a git repository in the project folder and put the file under version control.

## My git-based music workflow

Although, when wearing a developer hat, I am normally in linux, for the music stuff, Windows is a better option. For Windows, you can install `git-bash`, and have all the git functionality at your fingertips through a command-line interface.

First, I initialize a repository in the project directory. For me, it is most convenient to use a git bash command line terminal.

* side note: you can use any git frontend, not only `git gui`.

I also create a `.gitignore` file and that this is this particular project file that I want to track, and not any other, such as media or peak files.

Then I am free to work with the project in my DAW as usual. When I am done working on a specific version, I make a commit and give it a descriptive name, e.g. "bass vst settings adjusted".

Then I can see all the versions of my project in `git gui` tool.

Not only that, but I can also open any historical version of the project, create branches and so on. In other words, I can fully benefit from the version control system! If you are already using git, you know what I mean.

The days of versioned files mess in my project folder are finally gone! I wonder, though, if Reaper developers will be willing to incorporate that into their product one day.

GIT is not only about versioning, but also about collaboration, with remote repositories and so on. Frankly, I don't see it feasible for collaboration over music projects since the project files are normally opaque and we should not expect git or any other version control system to be able to merge/diff them.

Well, this tool is not magical, but still pretty useful!

Thanks for reading.