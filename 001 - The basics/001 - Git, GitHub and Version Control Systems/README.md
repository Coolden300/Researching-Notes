# Git and GitHub, Version Control Systems

This project is currently located on a GitHub hosted repository. For some this may be a familiar name, but for some not. For any developer it is crucial to know what are these, as they make teamwork and personal project extremely easy to share between team members and even personal devices. So here I will explain what are GitHub and Git and what is difference between them.

##

#### Version Control System(s) (VSC)
Git[*](https://en.wikipedia.org/wiki/Git)[*](https://git-scm.com/) and GitHub[*](https://en.wikipedia.org/wiki/GitHub)[*](https://github.com/) are both Version Control Systems (VCS)[*](https://en.wikipedia.org/wiki/Version_control). What is a VCS you may ask? VSC is a tool that helps to manage versions of your project(s). We can take a videogame mechanic as a simple example: Before beating a boss in a video game you save your current progress. Then after beating the boss, you save your progress again after success, or load that one previous save to restore progress and try again with different method. That's how VCSs work. They help you to create versions of your projects and manage them. If you'd have and issue in your current version of the project, you can revert changes to previous version where everything is stable, or you upload a new version to save when everything is functioning after new code update.

Besides of controlling versions VCSs also register who have made certain changes in a project so that if somebody has any claims to certain changes they can see who they're gonna adress them to.

There is 2 types of VCSs: **centralized** and **distributed** 
![](VSC_types.png)
(you can also read more about version control in general [here](https://en.wikipedia.org/wiki/Distributed_version_control))

##

**Centralized** VCSs use a remote server to store all project data, while users commit certain file updates load copies of files to work on them locally, commiting them later on. To copy file on your computer can be also called to *check out* or *to update*, since you can already a copy of certain file, you just want to update it if file has been changed by somebody else.

There's also **2 checkout types**:
- **Full checkout**, when user downloads entire project from repository. Makes it easier for user to work offline but can take up a lot of memory space.
- **Partial checkout**, which is, if you my have guessed yet, when user downloads only certain files of project that user has to work with. Vice versa: takes up less space but makes it hard to work offline.

Centralized VCSs are used for massive projects, that would be be impossible or extremely hard to have locally. Large enterprices, government bodies and gaming studios use this type of VCS.

Though with such advantage of being able to store large amounts of data, centralized VCSs have a big and important issue - <span style="color:red">single point of failure</span>. If a server goes down, files get corrupted or data is being lost, nobody will have access to the project anymore. So while using centralized VCS it is important to maintain servers well and have backups of project somewhere else, for example on another server.

Now **distributed** VCSs use a remote server to keep repository as well, except all users download a *copy* of this repository locally