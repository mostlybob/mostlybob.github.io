---
layout: post
title: "Updating Octopress to use SSH for Github Pages"
date: 2014-10-17 05:45:57 -0500
comments: true
categories: [blog, Octopress, ssh]
author: Bob Campbell
---
In the afore-mentioned spirit of building the boat as it’s moving away from the dock, I’m sort of trying this one on the fly. After switching the remotes, I had expected the deploy to “just work,” since it was pushing to a Github repo. When I deployed, however, it still asked for my GH credentials. Without actually looking at the Rakefile Octopress uses, I had assumed that there was a bit of configuration in the deploy task that was telling it to use a different method. When I actually looked at it, though, no such luck:

``` ruby task, task, who has the task?
task :deploy do
  # Check if preview posts exist, which should not be published
  if File.exists?(“.preview-mode”)
    puts “## Found posts in preview mode, regenerating files ...”
    File.delete(“.preview-mode”)
    Rake::Task[:generate].execute
   end

   Rake::Task[:copydot].invoke(source_dir, public_dir)
   Rake::Task[“#{deploy_default}”].execute
 end
```

Nothing pertaining to my blog, specifically, to be seen, but there was that ```deploy_default``` task. All it said was “push” so not much there either. There was another variable in that block, though, called ```ssh_user``` with a default e-mail address in it. I replaced it with the e-mail address I used to create the SSH keys and I’m thinking that might do it, the reasoning being if it tried to push with an invalid SSH setting, GH would fall back to the HTTPS mode. I could be wrong, but I thought I’d give that a whirl.

Sure I could do a search for all this, but I’m in an experimental mood. Let’s see how it goes.

*Ok, it didn’t work - the deploy still asked for credentials, so I sense a web search in my future. For science!*
