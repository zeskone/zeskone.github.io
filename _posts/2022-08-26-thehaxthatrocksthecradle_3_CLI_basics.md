---
layout: post
title:  "Part 3 - The Hax that Rocks the Cradle CLI Basics"
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
# Level 10 - From the Depths
Here you'll learn to dig a bit deeper.

<details>
<summary>Level 10 - Hint</summary>

<br>
<span style="color:DodgerBlue">
After reading acidburn's message, see what might help in the <code>ls</code> ... welll, help.
</span>
</details>
<br>
<details>
<summary>Level 10 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
Use:<br>
<code>ls -R</code><br>
... to <b>recursively</b> show the contents of the directory. Meaning it'll look in your current directory, and inside any directories in your directory, and any directories inside that ... like a matryoshka doll (those Russian nesting dolls).<br>
<br>
</span>
</details>
<br>

# Level 11 - The Matryoshka Squad
Here you'll learn to dig a bit deeper ... and wider? Maybe the shovel you've been using needs to be swapped out for another tool.

<details>
<summary>Level 11 - Hint</summary>

<br>
<span style="color:DodgerBlue">
After reading crashoverride's message, take a look at the <code>find</code> help.
<br>
Disclaimer - I personally find the CLI help for <code>find</code> to be ... not so helpful. If you don't find the help you need in <code>find</code>'s help, maybe you'll find that the help you find online will help you use <code>find</code> in a way that helps. Something like that.<br>
<br>
Suggested search: <b>linux find examples</b><br>
<br>
You can also check the manual for <code>find</code> - it's really long, but much more clear to me than the <code>--help</code> information. While we're at it - I might as well mention that you can also find the manual for most commands online really easily too! I like doing that because you can easily use CTRL+f to search on the page for a specific word if you'd like. How do you find the manuals? I typically just use the same words I'd use at the CLI! In this case, just do a search for "man find". This one in particular may come up with unrelated results, but you should also find the manual info too!
</span>
</details>
<br>
<details>
<summary>Level 11 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
Use:<br>
<code>find . -name thep*</code><br>
Let's break that down:
<ul>
<li><code>.</code> - the humble period is Linux's shorthand for "this directory". This tells find to look here. Find works recursively by default, so you don't have to tell it to do that like you would with <code>ls</code></li>
<li><code>-name</code> - this tells find that the attribute of the file we're searching by is the name. Of course it's the file name! What else would you search by?! You may be sorry you asked in a bit :)</li>
<li><code>thep*</code> - "thep" is the only piece of the filename that user crashoverride gave us. You have to put the wildcard * after that since you don't know if or how many characters follow that part of the file name.</li>
</ul>
<br>
</span>
</details>
<br>
# Level 12 - Don't Be So Sensitive
theplague needs some help with this new command!

<details>
<summary>Level 12 - Hint</summary>

<br>
<span style="color:DodgerBlue">
Again, check the <code>find</code> help or online examples.
<br>
<code>find</code> is case sensitive by default - tell it to be the opposite.
</span>
</details>
<br>
<details>
<summary>Level 12 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
Use:<br>
<code>find . -iname razor*</code><br>
Let's break that down:
<ul>
<li><code>.</code> - the humble period is Linux's shorthand for "this directory". This tells find to look here. Find works recursively by default, so you don't have to tell it to do that like you would with <code>ls</code></li>
<li><code>-iname</code> - like last time, this tells find that the attribute of the file we're searching by is the name, but the <b>i</b> in <code>iname</code> means to search in a <b>case insensitive</b> manner.</li>
<li><code>razor*</code> - "razor" is the only piece of the filename that user theplague gave us. You have to put the wildcard * after that since you don't know if or how many characters follow that part of the file name.</li>
</ul>
<br>
</span>
</details>
<br>
# Level 13 - The Nothingness You Seek
Now razor needs some help with `find`.

<details>
<summary>Level 13 - Hint</summary>

<br>
<span style="color:DodgerBlue">
After checking razor's helpful file* check the <code>find</code> help or online examples.
<br>
* - don't see a file from razor? Remember all the <code>ls</code> options?<br>
<br>
Remember when I said <code>find</code> can search for attributes other than file names, and you were like "Yeah, whatever, when am I ever going to do that?!"
<br>
Now. Now is when you do that!
</span>
</details>
<br>
<details>
<summary>Level 13 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
Use:<br>
<code>find . -empty</code><br>
Let's break that down:
<ul>
<li><code>.</code> - the humble period is Linux's shorthand for "this directory". This tells find to look here. Find works recursively by default, so you don't have to tell it to do that like you would with <code>ls</code></li>
<li><code>-empty</code> - this tells the command to look for an empty file.</li>
</ul>
<br>
</span>
</details>
<br>
# Level 14 - What's Puters, Precious?
razor's buddy blade needs some help with `find` after a run-in with a mysterious creature.

<details>
<summary>Level 14 - Hint</summary>

<br>
<span style="color:DodgerBlue">
After checking blade's tale of what happened, check the <code>find</code> manual or online examples for how to find files belonging to a user.
<br>

</span>
</details>
<br>
<details>
<summary>Level 14 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
Use:<br>
<code>find . -user gollum</code><br>
Let's break that down:
<ul>
<li><code>.</code> - the humble period is Linux's shorthand for "this directory". This tells find to look here. Find works recursively by default, so you don't have to tell it to do that like you would with <code>ls</code></li>
<li><code>-user gollum</code> - this tells the command that we're looking for a file owned by a particular user - in this case, it's "gollum".</li>
</ul>
<br>
Now that you have that super long file path, <code>cat</code> it out to see the contents.
Remember (or maybe you're learning this for the first time!) that to copy and paste from the Linux CLI, the keyboard shortcuts are:<br>
<code>CTRL+SHIFT+c</code> - copy<br>
<code>CTRL+SHIFT+v</code> - paste<br>
</span>
</details>
<br>
# Level 15 - Intelligence, Open Sourced
Reconnaissance can be done on targets just by querying publicly available sources. This is referred to as Open Source Intelligence (OSINT).

<details>
<summary>Level 15 - Hint</summary>

<br>
<span style="color:DodgerBlue">
You're looking for a book of course, not a movie! <br>
OSINT sometimes depends on you using just the right search terms, but hopefully this one shouldn't be too tricky with the info given by gollum. Give multiple search engines a try, never know what might pull up that specific bit of info you're looking for.
<br>
If you get that piece of info about the story, find a way to show a file's last modified date/time.

</span>
</details>
<br>
<details>
<summary>Level 15 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
Using the search term: "first story with Bilbo and Gollum" in a Google search gets you a lot of answers related to the 1937 book, "The Hobbit".
Using that search term in Bing (as of September 2022 anyway) gets you a nice clear-cut answer:
<image src="/images/hobbit.png"></image><br>
<br>
So now you just have to find the file made in 1937! Wow, this computer must be old, huh?
For that, we revisit our old friend <code>ls</code>. The <code>-l</code> option outputs the directory's contents in what they call "list" format, which includes some more info besides just the file names, for example, the last time the file was modified!<br>
<br>
<pre>
gollum@thehaxthatrocksthecradle:~/.treasures$ ls -l
total 280
... [snipped output] ...
-rw-rw-r-- 1 gollum gollum 23 Jul 29  1937 a1d0c6e83f027327d8461063f4ac58a6
</pre>
Now, it's just a matter of copying that file name, and pasting it into a cat command to output its contents!<br>
</span>
</details>
<br>
# Level 16 - One Line to Rule Them All
Check out what Bilbo has to say - see what you can find out about unique lines in Linux.

<details>
<summary>Level 16 - Hint</summary>

<br>
<span style="color:DodgerBlue">
Check out the <code>uniq</code> command, see if it might give you what you need.

</span>
</details>
<br>
<details>
<summary>Level 16 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
Running the <code>uniq</code> command with no options isn't quite enough.<br>
By default, it will just de-duplicate the lines in the file. That still leaves us with a lot (12,595) lines, and doesn't tell us which one was unique to begin with!<br>
<br>
Using the <code>-u</code> option shows us <bold>only</bold> the unique line, and ignores the rest:
<pre>
bilbo@thehaxthatrocksthecradle:~$ uniq -u creds 
99b2a15856249b868abbfc92dea6cee6
</pre>
<br>
Note that this won't work in a file with randomized lines, you'd have to sort the lines first. <code>uniq</code> compares one line with the lines around it. In this case, the duplicates are all one after the other, so <code>uniq</code> works by itself.<br>
</span>
</details>
<br>
# Level 17 - Searching for Specific Words
We've been looking for files so far, but how about stuff inside the files?

<details>
<summary>Level 17 - Hint</summary>

<br>
<span style="color:DodgerBlue">
Check out the <code>grep</code> command, see if it might give you what you need. 
</span>
</details>
<br>
<details>
<summary>Level 17 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
The <code>grep</code> command will find whatever "pattern" you feed it in whatever file you specify. The syntax for the most simple usage of the command is:<br>
<code>grep searchterm filename</code><br>
<br>
Since the term we're searching for is "Bombadil", and the file is "fellowship.txt", our command is:
<code>grep Bombadil fellowship.txt</code><br>
<br>
Sample output:<br>
<pre>
frodo@thehaxthatrocksthecradle:~$ grep Bombadil fellowship.txt 
Tom Bom, jolly Tom, Tom Bombadillo!
Old Tom Bombadil water-lilies bringing
here then? Do you know who I am? I'm Tom Bombadil. Tell me what's
</pre>
So now we see that Mr. Bombadil's first name is Tom!
</span>
</details>
<br>
# Level 18 - Multi-stage Madness
This one has a few steps to it, break the problem up into chunks to help you keep track of what you need to do!

<details>
<summary>Level 18 - Hint</summary>

<br>
<span style="color:DodgerBlue">
The steps you'll need to complete this level are:
<ul>
<li>Convert the binary number to decimal - by whatever means necessary!</li>
<li>Use a command to <code>wget</code> the file from the web server.</li>
<li>Find a way to locate a specific line of text in the file, like he <code>sed</code></li>
</ul>
</span>
</details>
<br>
<details>
<summary>Level 18 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
The steps fully detailed out are:
<ul>
<li>Convert the binary number to decimal - by whatever means necessary!</li>
<ul>
<li>The simplest way to do this might be to look up a binary to decimal converter online</li>
<li>You can also just figure out the binary yourself if you're into that sort of thing</li>
<li>In any case, you should arrive at the number 278</li>
</ul>
<li>Use a command to <code>wget</code> the file from the web server.</li>
<ul>
<li>In my case, with the target IP address being 10.0.0.19, my command is:<br>
<pre>
wget 10.0.0.19:8000/66f363a6b5353b2cdc28f0b75a94410c/twotowers.txt
--2022-09-12 19:18:15--  http://10.0.0.19:8000/66f363a6b5353b2cdc28f0b75a94410c/twotowers.txt
Connecting to 10.0.0.19:8000... connected.
HTTP request sent, awaiting response... 200 OK
Length: 194068 (190K) [text/plain]
Saving to: ‘twotowers.txt’

twotowers.txt            100%[=================================>] 189.52K  --.-KB/s    in 0.001s  

2022-09-12 19:18:15 (352 MB/s) - ‘twotowers.txt’ saved [194068/194068]
</pre>
</li>
<li>As you see above, this saved the file to a file called twotowers.txt on the local hard drive.</li>
</ul>
<li>Find a way to locate a specific line of text in the file, like he <code>sed</code></li>
<ul>
<li><code>sed</code> can do a lot of things. It can find a specific line in a file, for example.<br>
<pre>
sed -n '278p' twotowers.txt
'Night lies over Isengard,' said Treebeard.
</pre>
</li>
</ul>
</ul>
Now (finally) you have the name of the speaker and the place he talked about!<br>
</span>
</details>
<br>
# Level 19 - More Multi-stage Situations!
Get used to it! Some levels from here on in will involve multiple steps - some more than others.

<details>
<summary>Level 19 - Hint</summary>

<br>
<span style="color:DodgerBlue">
The steps you'll need to complete this level are:
<ul>
<li>OSINT for Samwise's wife's nickname</li>
<li>Download the file again if needed</li>
<li>We already used a command to find a specific word or term in a file. How about something near that term, you know, in case you want some context for the line you found?</li>
</ul>
</span>
</details>
<br>
<details>
<summary>Level 19 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
The steps fully detailed out are:
<ul>
<li>OSINT for Samwise's wife's nickname - search for something like "samwise gamgee's wife's name" - should yield "rosie"</li>
<li>Download the file again if needed</li>
<li>We already used a command to find a specific word or term in a file. How about something near that term, you know, in case you want some context for the line you found?</li>
<ul>
<li><code>grep</code> can be used to search for lines before <code>-B</code>, after <code>-A</code>, or both <code>-C</code> (for context). Follow up the command option with the number of lines you want to expand your search by.</li>
<li>In our case:<br>
<pre>grep "Chapter 7" twotowers.txt -A3
                          _Chapter 7_  
           Helm's Deep  
  
    The sun was already westering ... [snipped]
</pre></li>
<li>Keep in mind that a blank line (like the one after "Helm's Deep") still counts as a line as far as <code>grep</code> is concerned.</li>
</ul>
</ul>
<br>
</span>
</details>
<br>
# Level 20 - Switching It Up a Bit
Check Rosie's notes out and again, break this up into chunks to take one step at a time.

<details>
<summary>Level 20 - Hint</summary>

<br>
<span style="color:DodgerBlue">
The steps you'll need to complete this level are:
<ul>
<li>Find the user's name using OSINT</li>
<li>Find the user's password using OSINT</li>
<li>Find a way to switch users in Linux</li>
<li>If needed, figure out how to check out a user's command history in the Linux CLI. You may find a hint there.</li>
</ul>
</span>
</details>
<br>
<details>
<summary>Level 20 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
The steps fully detailed out are:
<ul>
<li>Find the user's name using OSINT</li>
<ul>
<li>Search for something like the term given in the file, "lady of the wood of Lothlorien"</li>
<li>You should get "Galadriel"</li>
</ul>
<li>Find the user's password using OSINT</li>
<ul>
<li>S`earch for something like "Galadriel's husband"</li>
<li>You should get "Celeborn"</li>
</ul>
<li>Find a way to switch users in Linux</li>
<ul>
<li><code>su</code> is the command to switch users in Linux. In this case, the command would be<br></li>
<li><code>su galadriel</code></li>
</ul>
<li>If needed, figure out how to check out a user's command history in the Linux CLI. You may find a hint there.</li>
<ul>
<li><code>history</code> is the command to check the history of the user you're currently logged in as.</li>
</ul>
</ul>
</span>
</details>
<br>
# Level 21 - Picture This ...
Check Galadriel's notes out and again, break this up into chunks to take one step at a time.

<details>
<summary>Level 21 - Hint</summary>

<br>
<span style="color:DodgerBlue">
The steps you'll need to complete this level are:
<ul>
<li>Download the picture of the elf - if you happen to be in an environment where you can't view images on your attacking machine, download it <a href="/images/someelf.jpg">here</a>.</li>
<li>Do a reverse image search to find out the elf's name</li>
<li>Show the running processes in Linux</li>
</ul>
</span>
</details>
<br>
<details>
<summary>Level 21 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
The steps fully detailed out are:
<ul>
<li>Download the picture of the elf - if you happen to be in an environment where you can't view images on your attacking machine, check it out <a href="/images/someelf.jpg">here</a>.</li>
<ul>
<li>From the CLI, use wget again: <code>http://targetip:8000/images/someelf.jpg</code></li>
</ul>
<li>Do a reverse image search to find out the elf's name</li>
<ul>
<li>Using Google, the most direct way is to go to https://images.google.com:<br>
<image src="/images/google_imagesearch_start.png"></image><br></li>
<br>
<li>Upload the image you downloaded and you should get something like:<br>
<image src="/images/google_imagesearch_result.png"></image><br></li>
<br>
<li>Using Bing, just go to the Bing homepage at https://www.bing.com:<br>
<image src="/images/bing_imagesearch_start.png"></image><br></li>
<br>
<li>Upload the image you downloaded. While the error message on the right seems to indicate we hit a dead-end, notice that the top of the screen does show the character's name, and even the actress who played the character:<br>
<image src="/images/bing_imagesearch_result.png"></image><br></li>
</ul>
<li>Show the running processes in Linux</li>
<ul>
<li>The <code>ps</code> command shows running processes. But ... by itself, it's not all that useful for our purpose here. Check the manual (<code>man ps</code>) to see some more options:
<pre>
       To see every process on the system using standard syntax:
          **ps -e**
          **ps -ef**
          **ps -eF**
          **ps -ely**

       To see every process on the system using BSD syntax:
          **ps ax**
          **ps axu**
</pre>
</li>
<li>Running <code>ps -ef</code> or <code>ps auxw</code> will yield something like:
<pre>
galadriel@thehaxthatrocksthecradle:~$ ps auxw
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
... snipped a whole BUNCH of stuff we didn't need ...
... and finally WAAAYYY at the bottom, you see ...
tauriel     2525  0.0  0.0   2888  1048 ?        Ss   20:25   0:00 /bin/sh -c python3 /home/tauriel/alwayswatching.py
tauriel     2527  0.0  0.2  18744  7984 ?        S    20:25   0:00 python3 /home/tauriel/alwayswatching.pyc
</pre>
</li>
<li>The <code>ps</code> command shows processes by other users and their names with the right options enabled as shown here.</li>
<li>Since Galadriel said the password is the file name without the .py, it should be <code>alwayswatching</code>.</li>
</ul>
</ul>
</span>
</details>
<br>
# Level 22 - Trapping a Clumsy Target
Tauriel is hunting someone and you'll have to help her set some traps for that target! Get ready to search online for some new commands to perform quite a few steps this time around!

<details>
<summary>Level 22 - Hint</summary>

<br>
<span style="color:DodgerBlue">
The steps you'll need to complete this level are:
<ul>
<li>Show owners for directories in /</li>
<li>Find out how to make a directory in Linux and make one</li>
<li>Make a hidden directory</li>
<li>Make an empty file</li>
<li>Make a hidden empty file</li>
<li>Check the URL given</li>
</ul>
</span>
</details>
<br>
<details>
<summary>Level 22 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
The steps fully detailed out are:
<ul>
<li>Show owners for directories in /</li>
<ul>
<li>Use <code>ls</code> and the <code>-l</code> option along with specifically telling the command to look in <code>/</code> instead of your current directory (its default behavior).</li>
<li><pre>
haxy@thehaxthatrocksthecradle:~$ ls -la /
total 945468
...[snipped content]...
drwxr-xr-x   2 tauriel tauriel      4096 Aug  3 20:39 mod
</pre></li>
</ul>
<li>Find out how to make a directory in Linux</li>
<ul>
<li><pre>mkdir free_dinner</pre></li>
<li>If you get no messages in return, it means your command worked - one of those quiet victories, I suppose.</li>
<li>Now you have to wait (no command needed for that, just uhh, take your hands off the keyboard for a minute?) , check the contents directory of the directory you made, and then output the contents of the new file in that directory. Since you're a pro at those things already, I'll leave the steps out.</li>
</ul>
<li>Make a hidden directory in Linux</li>
<ul>
<li>Same command as last time, but you just have to know that a hidden directory or file has a <code>.</code> in front of the file name.</li>
<li><code>mkdir .forest_tea</code></li>
<li>Wait, check directory contents, check file</li>
</ul>
<li>Make an empty file</li>
<ul>
<li><code>touch</code> is used to update the Last Modified Date of a file. If the file doesn't exist though, it makes an empty file with the name you supplied!</li>
<li><code>touch oven</code></li>
<li>Wait, check file contents</li>
</ul>
<li>Make a hidden empty file</li>
<ul>
<li><code>touch</code> is our go-to command again, just use a <code>.</code> to make the file hidden!</li>
<li><code>touch .dwarf_net</code></li>
</ul>
<li>Check the URL given</li>
<ul>
<li>Again, use <code>wget</code>:</li>
<li><code>wget targeturl</code></li>
<li>If you can't view the image on your attacking machine in your environment, replace the http://targetip:8000/images/ in the URL with https://zeskone.github.io/images/ and view it on a device that has web access.</li>
</ul>
</ul>
</span>
</details>
<br>