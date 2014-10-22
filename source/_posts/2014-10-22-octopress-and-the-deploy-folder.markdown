---
layout: post
title: "Octopress and the  _deploy folder"
date: 2014-10-22 05:51:59 -0500
categories: [blog, github, ssh]
publish: true
author: Bob Campbell
---

Another short one. In the process of chasing around the issue with getting the SSH to work with Octopress, I inadvertantly deleted the ```_deploy``` folder. When I saw the rake task complaining about the folder being missing, I recreated it and (thought) things were well. Then I noticed that my blog was no longer updating. Everything was safe and backed up, so I thought, just blow it away and start over. 

What I found during the set up is that the ```_deploy``` folder enjoys a special status within the source branch of being pointed at master. This makes sense, given its role, but I didn’t know you could do this with git. Ah, the process of discovery. I’ll have to tuck that little characteristic away for future reference.

At any rate, I seem to be back on track, although one upshot is that I lost my commit history by deleting the old GH repo. I still have the old repo local, at least until I decide to get rid of it.
