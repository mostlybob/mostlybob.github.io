---
layout: post
title: "Running Docker with Antergos"
date: 2014-04-11 12:33:32 -0500
comments: true
categories: [docker, arch, Antergos]
---
At the risk of turning this into a super-slow mo live blogging event, I did want to put up my observations working with <a href="http://www.docker.io">Docker</a>.

After a little fiddling around, I got ```docker``` running. The basic directions are <a href="https://bbs.archlinux.org/viewtopic.php?id=174183">here</a>, the only addition I would add is that for me, it required a system restart before the change took hold. Prior to the restart, following those directions resulted in an error message:

```
Cannot connect to the Docker daemon
```

After the restart, all was well.
