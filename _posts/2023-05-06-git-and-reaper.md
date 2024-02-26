---
title: git for music! My approach to versioning projects
---

Being both a musician and a software engineer, I always felt that these two areas are almost completely separated. My developer skill-set seemed to have little to no use for my work as a musician. Which is a pity considering how cool it would be if there was some kind of a sinergy across these two sides of my life.

Recently, though, I have found a useful possibility to utilize something I previously used solely for my development work, namely, git, the version control tool, for my music production.

Okay, and now let's get to the point and...

## meet Git for music production

Did you notice yourself creating a dozen of versions of your project? Are the names like this familiar to you? 

`my-cool-song-new-vocals-brighter-mix-4.rpp`

Did you ever feel frustrated about unmanageability of all this and how sloppy you project directory ends up looking?

This version nightmare problem for software people has a solid and well-recognized solution: version control systems. Such as ["git"](https://git-scm.com/), which is not only the most widely used one in the industry, but also completely free, open source and cross platform (that is working flawlessly on Win/Mac/Linux).

I use Reaper, and instead of creating dozens of copies of my project file (`my-cool-song.rpp`), such as `my-cool-song-new-vocals-brighter-mix-4.rpp`, I simply initialize a git repository in the project folder and put the file under version control.

By the way, a good supplementary for this reading could be this video of me going through an example. If you are not fan of watching videos, feel free to read on.

<iframe width="100%" height="100%" src="https://www.youtube.com/embed/TAnaKhtenPM" title="using git for managing musical projects" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>


<div class="video-container">
  <iframe width="100%" height="100%" src="https://www.youtube.com/embed/TAnaKhtenPM" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## My git-based music workflow

Although, when wearing a developer hat, I am normally in linux, for the music stuff, Windows is a better option. For Windows, you can install `git-bash`, and have all the git functionality at your fingertips through a command-line interface.

First, I initialize a repository in the project directory. For me, it is most convenient to use a git bash command line terminal:

```shell
Acer@DESKTOP-NRN84IB MINGW64 /c/home/music
$ cd test_git_project/

Acer@DESKTOP-NRN84IB MINGW64 /c/home/music/test_git_project
$ git init .
Initialized empty Git repository in C:/home/music/test_git_project/.git/

Acer@DESKTOP-NRN84IB MINGW64 /c/home/music/test_git_project (master)
$
```

in the example above:
- I first navigated to the directory with my project with `cd` command
- initialized a repository with `git init .`
- on the last, third line, my command prompt starts having a little `(master)` thing, which is the default "branch" in my repository that Git has created for me



I also create a `.gitignore` file and that this is this particular project file that I want to track, and not any other, such as media or peak files:

```.gitignore
*

!in_your_eyes_remix_git_managed.rpp
```

Then I am free to work with the project in my DAW as usual. When I am done working on a specific version, I make a commit and give it a descriptive name, e.g. "bass vst settings adjusted".

Then I can see all the versions of my project in `git gui` tool.

![image](https://user-images.githubusercontent.com/21345604/236634404-f0392a01-d22f-4893-9e90-356707eadc86.png)

* side note: you can use any git frontend, not only `git gui`.

Not only that, but I can also open any historical version of the project, create branches and so on. In other words, I can fully benefit from the version control system! If you are already using git, you know what I mean.

The days of versioned files mess in my project folder are finally gone! I wonder, though, if Reaper developers will be willing to incorporate that into their product one day.

### Managing other files (WAVs etc.)

Git is not super suited for managing big binary files (such as WAV samples and stems), but this is not a problem for me since I only manage the main project file.

About other files I do not care. Why? Becase I never remove them. The media files are either WAVs related to this project (and which are therefore kept in the project folder) or samples from my library. In both cases, these files are normally (at least withing the lifespan of the project under construction) never deleted.

This approach, which, I guess, I share with most producers, makes it easy to return to any historical version of the project and rely on the media files to be found.

### collaborating with GIT? Not sure...

GIT is not only about versioning, but also about collaboration, with remote repositories and so on. Frankly, I don't see it feasible for collaboration over music projects since the project files are normally opaque and we should not expect git or any other version control system to be able to merge/diff them.

And let's not forget that to be able to work on your project, the collaborator needs to have very close set up: the DAW, the plugins and all the media files.

Another note of the remote repositories: I do find it useful that I can push a project to github and this kind of a backup that will outlive my current PC. This is nice, but we can't really consider it a real backup - because of missing media.

### Tracking TODO items for your music project in GitHub

Interesting use-case I'm currently testing is to have a "todo list", think of an small per-project issue tracker with a list of things you plan to do later. Just a version-tracked text file of the format similar to this:

```
fix panning issues in chorus TODO
add one more synth layer TODO
```

Once it's in Github, you can update it from anywhere (GitHub allows you to edit files right in the browser), so, basically, you project gets its own, private, read/write website. On the go and got a cool idea? Now you know where to record it (don't forget to `pull` your update, though, once you are back to your DAW PC).

In conclusion, when we inspect this idea of "git for music" a bit closer, we can see that it does have a few viable applications. Yes, this tool is not magical, but still pretty useful!

Thanks for reading.

>_By the way, **are you a musician looking for collaboration**? Feel free to drop me a line at grechin.sergey(at)gmail.com! If you are a producer, vocalist, songwriter, we can do stuff together! Starting from cross-checks of our productions to help each other detect mixing glitches, or cross-mastering of our tracks up to releasing something together._
