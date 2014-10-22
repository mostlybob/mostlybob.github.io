---
layout: post
title: "Updating the Blog Setup to Use SSH"
date: 2014-10-16 12:32:45 -0500
comments: true
categories: [blog, github, ssh, https, git]
author: Bob Campbell
---

Generally speaking, I’ve found the workflow using Octopress to get stuff onto the blog reasonably straightforward. One bit that hangs me up, more for the inconvenience, is having to stop and enter my username & password everytime I deploy or push something to the repo on Github. It’s not a lot, but over the course of a typical session, if I have to do it, say, 6 or 7 times, it gets a little tiresome.

I’ve known for some time that Github makes it possible to set up SSH authentication so that you can sidestep this little hitch in the routine. This seemed like a nice little thing to blog about. Who knows? I never googled it with DuckDuckGo, so there may be a ton of stuff out there on this very topic, but I’m looking for stuff to write about and it beats a page of [Lorem Ipsum](http://lipsum.com/).

### Establish your keys
If you haven’t done so already, you need to set up SSH keys locally. I followed the directions [here](https://help.github.com/articles/generating-ssh-keys/), since I’m using Github. I have plans to explore deploying Jekyll/Octopress blog(s) to a more traditional shared webhosting solution, but for today, it’s Github. I’m using Linux. Mac should be much the same. Windows, out of the box, is a bit stunted in this regard. Your friendly neighborhood search engine should be able to [direct you](https://duckduckgo.com/?q=setting+up+SSH+on+windows) toward setting up SSH on Windows.

### Change your remote
Being somewhat lazy (or expeditious, choose), I set up things using the most direct route possible, meaning HTTPS for my github repo. Had I not, you’d be reading [something else](http://www.reddit.com/r/catpictures/). Here again, [Github spells it out](https://help.github.com/articles/changing-a-remote-s-url/).

### Test your changes
Rubber to road time. I followed the directions literally and took the name of the repo using HTTPS and stuck a 2 on the end of it for the SSH remote. As I suspected, git didn’t like that when I tried to push my commits. I took the 2 off and all was well. To reiterate, if you have a remote that looks like this when you do a ```git remote -v```

```
origin  https://github.com/palmolivemadge/ur-soaking-in-it.git (fetch)
origin  https://github.com/palmolivemadge/ur-soaking-in-it.git (push)
```

don’t do this:

```
$ git remote set-url origin git@github.com:palmolivemadge/ur-soaking-in-it2.git
```

Note the 2 on the end, just like what GH said in its post. Instead, do this:

```
$ git remote set-url origin git@github.com:palmolivemadge/ur-soaking-in-it.git
```

There are probably excellent reasons for GH describing things the way they did, but for us poor, literal-minded souls, they are a little misleading. It’s an easy mistake to spot and fix, but sometimes the dumbest things hang up the smartest people.

The follow-up to this will be altering the rake tasks in Octopress to use the SSH repo instead of the HTTPS. Enough pesky passwords!

Hey. Not so bad for my first substantial post, and only one day in. Onward!
