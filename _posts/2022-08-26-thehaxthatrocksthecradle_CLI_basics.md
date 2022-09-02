---
layout: post
title:  "The Hax that Rocks the Cradle CLI Basics"
date:   2022-08-26 17:19:23 -0500
categories: thehaxthatrocksthecradle
---


# Level 7 - SSH and File Output
You got another set of credentials - and not for the last time!

Use that to connect to the target host via SSH.

Once you've done that, see what files are available to you and see what you can find in the file(s).

<details>
<summary>Level 7 - Hint</summary>

<br>
<span style="color:DodgerBlue">
To the Internet for help once more! I don't suggest this all the time because I'm lazy (that's a possible contributing factor though!), but because this is probably the most valuable skill you can develop - learning how to find more information!
<br>
Some search suggestions to get you moving:<br>
<ul>
<li>SSH usage</li>
<li>show files in Linux</li>
<li>display file contents in Linux</li>
</ul>
</span>
</details>
<br>
<details>
<summary>Level 7 - Full Answer</summary>
<br>
<span style="color:MediumSeaGreen">
Kind of similar to FTP, SSH to a server with:
<code>ssh x.x.x.x -l username</code><br>
or<br>
<code>ssh username@x.x.x.x</code><br>
... where x.x.x.x is the IP address of the SSH server.<br>
<br>
<blockquote>The first time you SSH to something, you'll get a warning about the authenticity of the host and fingerprint, and blah, blah, blah. Just type yes at the warning message. What could possibly go wrong with that?</blockquote><br>
Enter the password when prompted.<br>
<br>
To list files, use <code>ls</code>.<br><br>
To output the contents a file to your screen, type:<br>
<code>cat filename</code><br><br>
To disconnect from this session, type <code>exit</code>.<br>
</span>
</details>
<br>
# Level 8 - Directing Change
The file for this new user is in a directory. Figure out how to get into it!


<details>
<summary>Level 8 - Hint</summary>

<br>
<span style="color:DodgerBlue">
Check out how to <b>change directory in Linux</b> online!
</span>
</details>
<br>
<details>
<summary>Level 8 - Full Answer</summary>
<br>
<span style="color:MediumSeaGreen">
Change Directory with the <code>cd</code> command:<br>
<code>cd info</code><br>
<br>
Repeat the steps from Level 7 to get the info for the next user!
</span>
</details>
<br>
# Level 9 - Hidden .mysteries
Same deal as level 8 ... almost. You might need to do something a little differently to show **all** the contents of a directory using ls.

<details>
<summary>Level 9 - Hint</summary>

<br>
<span style="color:DodgerBlue">
<code>ls</code> is a command, and has a help file! Remember how to check that from the CLI? Note that for some commands, some of these options might not work, depending on ... a lot of things:<br>
<ul>
<li><code>commandname -h</code></li>
<li><code>commandname --help</code></li>
<li><code>man commandname</code></li>
</ul>
</span>
</details>
<br>
<details>
<summary>Level 9 - Full Answer</summary>
<br>
<span style="color:MediumSeaGreen">
Use:<br>
<code>ls -a</code><br>
... to show <b>all</b> directories and files in your current directory, even if they're "hidden".<br>
<br>
You can tell if they are hidden because they have a . in front of the directory or file name. It's like a really little kid playing hide and seek ... "If I put a dot in front of my name, you can't see me, right?!"
</span>
</details>
<br>
# Level 10 - 