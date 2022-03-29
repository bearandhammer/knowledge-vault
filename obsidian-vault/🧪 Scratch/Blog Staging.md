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

Once enable, you are free to browse, install and enable community plugins by clicking the 'Browse' button, as indicated. The following screenshot shows the flow on how to access/adjust these settings:

Browse for and install 'Obsidian Git'; post installation ensure you click the 'enable' button to turn on the plugin (all plugins, that I have tried this far, do not enable by default and wait for the user confirmation in this regard). Post installation, you should see the following if searching for the plugin again (that confirms installation is successful):

Post-installation, close the search modal to return to the Settings modal and sca through the various settings until you reach the 'Installed Plugins' section; this is where you will find an entry for Obsidian Git, that allows you to access/tweak configuration settings.

This is the configuration platter that I went with, but you can tailor this fully to your taste as desired. 🍴

Image

Let's take a super-succinct tour of these settings and the exact meaning behind each setting. The 'Vault backup interval (minutes)' is, as you'd expect, the exact time interval between each automatic commit and push operation. Every 5 minutes is seems like a good balance between frequency and performance, although I have to admit I have noticed too much degradation as automatic commits/pushes occur. 'Auto pull interview (minutes)' is set to 0 to disable this feature, but if you are interested in pulling information (as you have a shared vault) then this could be of interest.

I prefer more clean commit history, so I have chosen 'Rebase' for the 'Sync method'; but again, dealers choice here! The next four settings ('Commit message on manual backup/commit', 'Commit message on auto backup', '{{date}} placeholder format', '{{hostname}} placeholder replacement') enable to you tailor the commit messages generated but injecting a hostname and date (in the desired format) into a template string. Of course, you are free to omit anything you don't want. For example, a final commit message in my repository is as follows:

Template string: '{{hostname}} vault backup: {{date}}'
Results in: 'Lews PC vault backup: 29/03/2022 19:49:58'

The 'List filenames affected by commit in commit body' adds any adjusted files into the body for the commit, which results in the follow effect (when viewed in GitHub):



