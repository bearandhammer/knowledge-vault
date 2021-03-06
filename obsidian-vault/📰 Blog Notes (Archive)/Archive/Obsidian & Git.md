
---
tags: 📰
---

# Obsidian & Git (original blog notes)

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

Post-installation, close the search modal to return to the Settings modal and sca through the various settings until you reach the 'Installed Plugins' section; this is where you will find an entry for Obsidian Git, that allows you to access/tweak configuration settings. The plugin will use any stock credentials you have configured for you designated workspace.

This is the configuration platter that I went with, but you can tailor this fully to your taste as desired. 🍴

Image

Let's take a super-succinct tour of these settings and the exact meaning behind each setting. The 'Vault backup interval (minutes)' is, as you'd expect, the exact time interval between each automatic commit and push operation. Every 5 minutes is seems like a good balance between frequency and performance, although I have to admit I have noticed too much degradation as automatic commits/pushes occur. 'Auto pull interview (minutes)' is set to 0 to disable this feature, but if you are interested in pulling information (as you have a shared vault) then this could be of interest.

I prefer more clean commit history, so I have chosen 'Rebase' for the 'Sync method'; but again, dealers choice here! The next four settings ('Commit message on manual backup/commit', 'Commit message on auto backup', '{{date}} placeholder format', '{{hostname}} placeholder replacement') enable to you tailor the commit messages generated but injecting a hostname and date (in the desired format) into a template string. Of course, you are free to omit anything you don't want. For example, a final commit message in my repository is as follows:

Template string: '{{hostname}} vault backup: {{date}}'
Results in: 'Lews PC vault backup: 29/03/2022 19:49:58'

The 'List filenames affected by commit in commit body' adds any adjusted files into the body for the commit, a personal preference of mine in this case, which results in the follow effect (when viewed in GitHub):

Image

It is possible to adjust the target branch for commit/push operations by toggling the 'Current branch' setting. This could be of benefit if working on a vault using a strategy such as Git flow (or where you want to stage changes into another branch and create Pull Requests/merge into another upstream branch, perhaps in a multi-user setup).

I have opted to pull updates on startup with the aid of the 'Pull updates on startup'. To pair nicely with this, the 'Pull changes before push' is also enabled, although my vault will only be for my own personal use (this could be useful if I change committed markdown files from another device).

Lastly, the most important setting to alter here is 'Disable push'; it is critical this is turned off in order for automatic commit/pull operations to trigger.

You are now away to the races and automatic commit/push operations should trigger as you build out your own personal knowledge base (capturing configuration changes, mardown file alterations/additions, etc). For example, as I have been compiling notes for this blog post the process has triggered numerous times. In Obsidian you will see a toastr-style notification:

Image

From a Git GUI, such as Fork, you should observe the following:

Image


---

My Current Vault

If you want to checkout my current vault dedicated to weird and wonderful knowledge snippets (100% a stub-fest, at the time of writing) then you can find that here.

https://github.com/bearandhammer/knowledge-vault

The plan, for me at least, is to build out (and then attempt to tie together) my evolving thoughts on life, work, professional practices, programming, mindfulness, health and nutrition and see what seedlings form from the process. Perhaps these 'seedling' ideas will grow into something more, who knows!

--

Extra Resources

I would recommend this superb YouTube resource (very long but well document with copious timestamps) for anyone wanting to go on an Obisidian journey.

https://www.youtube.com/watch?v=wB89lJs5A3s

As mentioned, the software itself is not open source but is highly extensible. Contributions in the form of plugins and themes are welcome and for those interested this repository is a good starting spot.

https://github.com/obsidianmd/obsidian-releases

--

Core plugins

Before looking at some community-driven plugins I wanted to take a very quick tour of some of the Core plugins bundled with Obsidian. Not all of these are enabled by default, so peruse the list and enable any that take your fancy.

I'll run over some of key, and noteworthy/interesting ones...

Obsidian comes with a stock File Explorer and Search capabilities (the standard search seems fairly powerful, below you can see a search by tag).

The Graph view really starts to expose the power of Obsidian showing a node-based diagram of the relationships between your notes.

One particular core plugin that caught my eye was the Audio recorder, allowing audio snapshots to be captured and injected directly into notes.

Audio Recording in a Note


![[Recording 20220330085052.webm]]

---

The Publish/Sync options allow access to paid services store and synchronize data; which is why I am opting for the GitHub-based approach. Pricing details can be found here, if this is on interest.

https://obsidian.md/pricing


--- 

Community Plugins

The following community plugins caught my attention, after a little bit of research (although I have yet to really get to grips with their full capabilities).

The Templater plugin allows you to craft custom templates for notes, inserting the result of raw JavaScript functions, as you see fit; which over time will become an enormous time saver.

Although simple, the Paste URL into selection has become my hot favourite. It allows you to highlight raw text and then paste URLs to create fully functioning links:

If you wish to switch up a note and turn it into a fully functional Kanban Board, the Kanban plugin does just that (I've included screens of the board view and the raw markdown, for reference).

The Calendar plugin integrates, you probably guessed it, a calendar into Obsidian. This does provide some tangible benefits, however, as it is possible to create note-based tasks that can be scheduled for review on target dates; metadata that is instantly visible on this calendar.

The Mind Map plugin shows a targeted view of the various relationships diverging off of the current note, allow a focused view of all of the links and easier navigation between them.

If you have the desire to write more complex queries against your knowledgebase data, the Dataview plugin enables querying by metadata using Dataview Query Language (SQL-like syntax) or JavaScript.

I can definitely see that the Natural Language Dates plugin has legs; in this example you'll see 'inoneweek' being automatically resolved.

Having some kind of syntax highlighting and copy code buttons is also a boon (check out the Editor Syntax Highlight and Copy button for code blocks plugins).

I've listed the GitHub repositories for all of these plugins below:

- Templater https://github.com/SilentVoid13/Templater
- Paste URL into selection
- Kanban
- Calendar
- Mind Map
- Dataview
- Editor Syntax Highlight
- Copy button for code blocks
- Natural Language Dates

## Blog Resources
### Main Resources
### Secondary Resources
[[Supplementary Blog Resources]]

```sql
SELECT 
COUNT(1) 
FROM [dbo].[MyTable] mt
WHERE mt.[IsDeleted] = 0
```

```csharp
string test = "Hello World";
Console.WriteLine(test);
```


---

All images/gifs - captions and open in new tab. > DONE
Handle all links (nicely format and open in new tab). > DONE
Read all content - clear and correct? > DONE
Grammarly pass > DONE
Tags/Categories > DONE
Claire Pass > DONE
Post!!! > DONE


Copy (for Twitter, Facebook and LinkedIn)...


New blog post: Happy Friday to you all! A fun foray of discovery; join me to find out 'What is Obsidian (and adding the magic dust of GitHub Integration)?' @obsdmd #secondbrain #knowledgevault #notes #github #selfimprovement