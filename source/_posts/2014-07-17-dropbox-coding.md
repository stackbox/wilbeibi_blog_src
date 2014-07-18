---

title: Collaborative programming with Dropbox
date: 2014-07-17

tags: [miscellaneous]

description: Easy solution of real time collaborative coding 
---


Recently, I am working on a web project collaborate with my friend Kelun. He is in charge of front-end code and I am taking care of backend code. So, here is a problem: How can we programming together smoothly? Which means, at any moment of time, I can check his code while he is programming.


## Why not Github?
No, that's little bit heavy for this project. So, what's alternative choices? Dropbox! Dropbox maybe the easiest way to share folder (wait, you means `rsync`? Dropbox did a lot of algorithm improvement to ensure it's higher speed of syncing)
![Alt text](http://dl.dropbox.com/u/1656836/web3/invite-to-folder.png)



But, something weird happens. My Webstorm automatically changed layout views. That because he is also using Webstorm, and In each project, Webstorm use a `.idea/` directory to save specific settings (as the document below said).

> Project settings are stored with each specific project as a set of xml files under the .idea folder. If you specify the default project settings, these settings will be automatically used for each newly created project.



## Is there any `.gitginore` like file in Dropbox?

Sure. Of course it's not as powerful as `.gitginore`. In dropbox -> Preference -> Account -> Change Setting, unclick `.idea` folder, that's all.

Also, I strongly suggest unclick `node_modules` folder. It takes Dropbox too much time to synchronize a bunch of small pieces of files.

And if you sometimes use Emacs, to avoid annoying temporary files (but some time really save you ass), the only way I know is to add this in `.emacs` file.

     (setq make-backup-files nil)

Please feel free to correct my typos or grammar.