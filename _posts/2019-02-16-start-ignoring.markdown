---
layout:     post
title:      "Stop tracking and start ignoring"
subtitle:   "A tip to delete files from a repository and stop tracking them while keeping them locally"
date:       2019-02-17 07:00:00
author:     "Vijay Koushik"
keywords:   "git, untrack, files, ignore, folders, remove files, remove folders,  remove cached"
header-img: "img/2019_02_16/post_header.jpg"
og_type: 	"article"
comments:   true
pageId:     "2019-02-16-start-ignoring"
tags:       ["git", "untrack files", "remove files", "remove folders","remove cached"]
---

<p>Hello world,</p>
<p>I’ve been playing around with GitHub & Git over the past few months and most of the time I accidentally commit and push files that are totally unrelated to the project. Usually they are the environment files like <em>node_modules</em> & <em>build</em> directories and <em>package.json</em> when using node.js as I use Gulp to minify css & JS and files like  <em>_site</em> folder and <em>Gemfile.lock</em> when I use Jekyll for my blog. </p>
<p>The reason for this problem? I forget to add the <em>.gitignore</em> file to my repository. The <em>.gitignore</em> file contains all the ignore rules (usually names of files and folders to be ignored) for the project. But there is a catch. The <em>.gitignore</em> file will tell Git to ignore the existence of only those files that haven’t been pushed. Since I have already pushed the files, adding them to the ignore rule won't work. Git will keep tracking the changes to those files and nag me to commit those changes. </p>
<p>I could delete these files and push the deletions to the repo but, they’re going to be recreated every time I build the project. So, that doesn’t work. A quick search on the internet gave me the exact solution I needed. There is a way to remove these files from the repo and keep them locally. By executing the following command in a CLI like <strong>git bash</strong> or <strong>cmd</strong> I deleted the files from the repo without removing them from my local file system.<br/> 
 <pre>
    <code>
    git rm --cached &lt;file name&gt;<br/>
    E.g. git rm --cached package.json<br/>
    </code>
 </pre><br/>
 <img src="{{ site.baseurl }}/img/2019_02_16/rm_cached_file.jpg" alt="Break down of remove a file only from repository command in git" width="800" height="534">
 <span class="caption text-muted">A break down of the command to remove a file only from the repository</span><br/>
 <pre>
    <code>
    git rm –r --cached &lt;directory name&gt;<br/>
    E.g. git rm –r --cached _sites
    </code>
 </pre><br/>
 <img src="{{ site.baseurl }}/img/2019_02_16/rm_cached_folder.jpg" alt="Break down of remove a folder and it's contents only from repository command in git" width="800" height="534">
 <span class="caption text-muted">A break down of the command to remove a folder and it's contents only from the repository</span><br/>
The <code>--cached</code> flag removes the files from the repository and leaves the local copies undisturbed. And the <code>–r</code> flag recursively removes the files inside the directory specified.</p>
<p>Now that I removed the files from the repo, Git thinks that the local copies of the deleted files are something new I added to the repo. So adding these file names to the <em>.gitignore</em> file will tell git to ignore these files and they won’t be pushed again. </p>
<p>Since this accident happens to me frequently, I decided to post this here so I wouldn't forget to add the ignore rules to the repo. Even if I do forget, I know where to look for the solution.</p>
<p>To make things more simple I found a site <a href="https://gitignore.io">gitignore.io</a> that generates <em>.gitignore</em> file based on the Operating systems, IDEs and programming languages that I provide in an all in one text box.
    <img src="{{ site.baseurl }}/img/2019_02_16/gitignoredoti_shot.jpg" alt="Screenshot of the site gitignore.io" width="800" height="600">
<span class="caption text-muted">A screenshot of gitignore.io's homepage</span>
</p>