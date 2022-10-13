---
layout: post
title:  "Part 2 - The Hax that Rocks the Cradle FTP"
date:   2022-08-26 17:19:23 -0500
categories: thehaxthatrocksthecradle
---


# Level 6 - FTP? WDYM? LOL!
Acronyms. Get used to them, you're bound to be swimming in them in just about any tech related field.

Anyway, remember way back in time when we did that nmap scan of the target host?
See if you can make use of this set of credentials on one of those other ports we found open!

<details>
<summary>Level 6 - Hint</summary>

<br>
<span style="color:DodgerBlue">
FTP - File Transfer Protocol - Running on port 21, this protocol lets you transfer files and stuff. Let's turn to our friend the Internet for some help!<br>
You may want to look up something like a <b>list of FTP commands</b>.<br>
If you find one, then try to find out:<br>
<ul>
<li>How to connect to an FTP server</li>
<li>How to list files</li>
<li>Once you have some filenames available, how do you download it?</li>
</ul>
</span>
</details>
<br>
<details>
<summary>Level 6 - Full Answer</summary>
<br>
<span style="color:MediumSeaGreen">
To connect to an FTP server, the command is simply:<br>
<code>ftp x.x.x.x</code><br>
or<br>
<code>ftp username@x.x.x.x</code><br>
... where x.x.x.x is the IP address of the FTP server.<br>
<br>
Enter the password when prompted. <i>If you're new to CLI environments, note that the password won't show anything on screen when you type, so type carefully or be prepared to hit backspace a ton of times! (No, I don't know that from experience, why do you ask?)</i><br>
<br>
To list files, use <code>ls</code> or <code>dir</code>.<br><br>
To download a file, type:<br>
<code>get filename</code><br><br>
Then quit FTP with the word <code>quit</code>.<br>
Example below:<br>
<image src="/images/ftp.png"></image>
<br><br>
If you're using a CLI environment on your attacking machine and, again, you're new to it and not sure what to do next ...<br>
<code>ls</code> - to view the files in your current directory<br>
<code>cat sshcreds.txt</code> - to output the contents of the file<br>
<br>
You'll be using these commands quite a few times in the coming steps!<br>
</span>

</details>
<br>
