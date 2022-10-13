---
layout: post
title:  "Part 1 - The Hax that Rocks the Cradle Web"
date:   2022-08-26 17:19:23 -0500
categories: thehaxthatrocksthecradle
---

For this (and all the challenges to come) to work, you need to have your attacking machine up and running, as well as the "victim" virtual machine.

# Level 1 - Finding Your Target IP Address
If you just started up the VM, you don't necessarily know the IP address it's using. 
If you found out by some other sneaky way ... uh ... forget it? Let's start over!

`nmap` is a tool that does ping sweeping, port scanning, all sorts of good enumeration stuff.
Use nmap to run a "ping scan" of the network the vm is on. If you don't know how, check the nmap help file, which is conveniently displayed if you just type `nmap` and hit enter. 

>BIG HINT: For most commands, to get the help menu, you'll use something like:
>
>- `commandname -h` or
>
>- `commandname --help`

If you got it working, the results show the addresses of all the machines on the network you specified. In some cases, it will show the addresses and the name next to it! Something like:

`Nmap scan report for thehaxthatrocksthecradle (xx.xx.xx.xx)`

<br>

In some cases though, it won't. If you have that issue, there are a couple other things you can try:
- `ping thehaxthatrocksthecradle.local`
	The address you get the reply from is your victim/target VM.
- Do a `port scan` for port 21143 on your local network and see which machine has this open. This should be your target VM - unless you have another computer with that port open, which would be kind of odd - like, very odd.

<br>
Keep this IP address handy! You'll need it for a lot of the coming steps.

>Actually, now's a good time to start up some note-taking! For future steps, you'll need to keep track of the username and password you last discovered so you can pick up where you left off. It's also a good idea to track any new stuff you've learned along the way!

<br>
>Each level will have a **Full Answer** toggle (like the one below) and maybe a **Hint** one preceding it. Give it a good try before clicking the toggle! The help is there if you need it though.

<details>
<summary>Level 1 - Full Answer</summary>
<br>
<span style="color:MediumSeaGreen">
If your IP address scheme for your network is 192.168.0.xxx, your nmap ping scan would be: <br>
<code>nmap -sn 192.168.0.-</code> 
<br>(the dash tells nmap "Fill this in with all possible values")
<br>
</span>

</details>

<br>
# Level 2 - Finding an Open Web Port
Now that you've found the IP address, run a port scan on the machine, just using nmap's default "common" ports. This is actually deceptively simple to do, so maybe just use the best resource ever - the Internet, and look up something like "nmap port scan".

This nmap scan should come back with a port that nmap says is `http-alt`. In other words, a web site! Maybe? Let's check it out!


<br>
<details>
<summary>Level 2 - Full Answer</summary>
<br>
<span style="color:MediumSeaGreen">
<code>nmap your.target.ip.address</code> <br>
For example, if your target IP is 10.0.0.50, your command would be:<br>
<code>nmap 10.0.0.50</code> 
<br>
You should see something a lot like:<br>
<image src="/images/initial_nmap.png"></image>
<br>
</span>

</details>
<br>
# Level 3 - Find a Hidden Directory and File
First, navigate to the website by just entering the IP address and port in your browser in this format:

`ip.ad.dr.ess:port`

For example, for target address 10.0.0.50 and port 1234, just type:

`10.0.0.50:1234`

You should get something like:


![screen](/images/site_initial_page.png)

<br>


Most websites want you to find their content. What if one had contents that they didn't necessarily want to show to everyone, but still have it be available to others. How would you find that content?

If a site followed an easy pattern like this, it would be easy:
* github.com/page1
* github.com/page2

Well, we'd just guess using "page" followed by numbers all the way up, right?

First of all, if they're using regular words, that makes things much more complicated! We need a **list** of **words** to try. Known in shady hacking circles by the ominous term, a ... **wordlist**. You can make one (and you will, in later levels if you continue on), but there are a bunch already made for you!

Kali and Parrot will come with some in their file system already. For example, this one here:
`/usr/share/wordlists/dirbuster/directory-list-2.3-small.txt`

If not, you can download it here:

[directory-list-2.3-small.txt](https://raw.githubusercontent.com/danielmiessler/SecLists/master/Discovery/Web-Content/directory-list-2.3-small.txt)

Secondly, that's a lot of typing. No one wants to do that. How about a tool to help you do that? There are a few different options out there. We'll use `ffuf`.
To check if you have it, just type `ffuf` at a command prompt on your attacking machine.
If you get a long help menu, congrats, you have it!

If not, you have to install it. In Kali or Parrot:

`sudo apt update`

`sudo apt install ffuf`


Now use ffuf along with that wordlist above to find a directory AND an html file in that directory that has some more information for you!

<br>
<details>
<summary>Level 3 - Hint</summary>

<br>
<span style="color:DodgerBlue">
Check out ffuf's help menu (get used to doing this for all sorts of commands!)
Specifically, look for how to specify your <b>wordlist file path</b>, <b>target URL</b>, how to search <b>recursively</b>, how to scan for a specific <b>extension</b>, and maybe <b>ignore wordlist comments</b>, since our wordlist has comments at the beginning.
<br>
<br>
The directory and file we're looking for both have hacking/security related names, btw. You'll find others, but can disregard them for now.
<br>
<br>
</span>
</details>
<br>
<details>
<summary>Level 3 - Full Answer</summary>
<br>
<span style="color:MediumSeaGreen">
Let's combine all the requirements mentioned in the hint based on ffuf's help file. When dealing with new commands, I like to do this on multiple lines, to help visually understand it better, and track my progress. Then I mush it all together:<br>
<br>
<code>ffuf</code> - our command<br>
<code>-w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt</code>  - the wordlist (adjust if yours is somewhere else)<br>
<code>-u http://target.ip.add.ress:8000/FUZZ</code>  - our target URL, followed by FUZZ where we want ffuf to fill in the gaps<br>
<code>-recursion </code> - to search recursively (this can extend scan times significantly, so be careful with this when scanning using large lists)<br>
<code>-e .html </code> - since we're looking for an html file<br>
<code>-ic</code>  - ignore wordlist comments just to make results cleaner<br>
Some options I like to throw in as well:<br>
<code>-c</code>  - colorize output<br>
<code>-v</code>  - verbose output<br>
<br>
Put it all together and you get:
<code>ffuf -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt -u http://192.168.254.175:8000/FUZZ -recursion -e .html -ic -c -v</code> 
<br>
You should see:<br>
<image src="/images/ffuf1.png"></image>
<br>
... and scroll down in the results to find ... <br>
<image src="/images/ffuf2.png"></image>
<br>
</span>

</details>
<br>

# Level 4 - Finding Sneaky Information
There are ways to hide information even on a single web page. Take a close look at what's on this page and see if there might be more to it than meets the eye initially.

<details>
<summary>Level 4 - Hint</summary>

<br>
<span style="color:DodgerBlue">
Do you see how the page says:<br>
<b>This concealment will certainly <i>highlight</i> their weaknesses.</b>
<br>
<br>
</span>
</details>
<br>
<details>
<summary>Level 4 - Full Answer</summary>
<br>
<span style="color:MediumSeaGreen">
Highlight everything on the page!<br>
You can do this by clicking/dragging, or pressing CTRL+a to Select All<br>
This was just a matter of text being the same color as the background. Simple, but this trick is used sometimes to hide text on pages. Why? Sometimes for SEO (Search Engine Optimization), sometimes by shady characters wanting to hide links on pages they gained illicit access to.
</span>
</details>
<br>

# Level 5 - Finding More Sneaky Information
This page also has more to it than meets the eye. It's stored a little differently though.

<details>
<summary>Level 5 - Hint</summary>

<br>
<span style="color:DodgerBlue">
The HTML used for web pages may have more information in the source file than you see when you get to it on a browser. There are different reasons for this - for one, it's kind of messy looking to the casual web user. Two, maybe the developers want to be able to leave <b>HTML comments</b> in the page to kind of leave notes to themselves or each other? Hmm...<br>
<br>
</span>
</details>
<br>
<details>
<summary>Level 5 - Full Answer</summary>
<br>
<span style="color:MediumSeaGreen">
The method for viewing HTML source code might differ for your browser.<br>
<ul>
Right click > View Page Source<br>
Right click > Developer Tools > View Page Source<br>
CTRL+u<br>
</ul>
Something along those lines should work for you.
Check the source of the page and you should see something like:<br>
<code>
&lt;!--<br>
FTP<br>
user:lordnikon<br>
pass:gotanewputer<br>
--&gt;
</code>
</span>
</details>
<br>
So what is this new piece of info we just found? Read on to find out!