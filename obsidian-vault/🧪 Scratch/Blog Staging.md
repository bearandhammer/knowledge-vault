---
tags: 🧪
---

# Blog Staging

Get whatever flavour of installation underway that you require. Once complete, you'll be presented with the following once your start the application:

Image

At this point I generated a new GitHub repository (with just a README.md and no .gitignore, for now) and once cloned, in the root folder of the repository, created a vault using the relevant Obsidian option. This will result in something pretty close to this, whereby my repository name is 'knowledge-vault' and my vault name is 'obsidian-vault':

Image

Voila! That's a fully functional Obsidian vault ready to rock and roll. Let's focus next on getting an extension to manage automatically committing and pushing to our remote repository on a schedule.

---

The community pluging of choice for easily enabling automatic push/commits to a remote repository is Obsidian Git. For anyone curious about how this plugin is implemented you can find the source on GitHub here: https://github.com/denolehov/obsidian-git.

First things first, the ability to use community plugins is locked off behind a specific configuration option. You'll find this option under Settings -> Community Plugins -> Safe Mode. This does come with the caveat that community plugins do have the ability to access resources on the target device; so a degree of caution is required.

Once enable
