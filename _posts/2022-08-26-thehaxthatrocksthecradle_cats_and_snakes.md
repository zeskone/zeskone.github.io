---
layout: post
title:  "The Hax that Rocks the Cradle Cats and Snakes"
date:   2022-08-26 17:19:23 -0500
categories: thehaxthatrocksthecradle
---

<br>
# Level 31 - The Cat's Out of the Net
Tinytina's alter-ego, Crunkbunny is now offering a way for you to get a mysterious cat's creds.

<details>
<summary>Level 31 - Hint</summary>

<br>
<span style="color:DodgerBlue">
Check out usage information for <code>netcat</code>. This is another utility where, honestly, the <code>--help</code> leaves me ... not helped. Maybe check the <code>man</code> for it or find some help online.
</span>
</details>
<br>
<details>
<summary>Level 31 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
It may be worth pointing out that people very often us <code>nc</code> as the command for <code>netcat</code>. So often in fact, that I <i>just</i> found out right now that you can use the full word <code>netcat</code> - at least in current versions of Kali and Ubuntu. Who knew? (not me, apparently).<br>
<br>
Once you know the command to use, the syntax for <code>nc</code> is pretty simple:
<code>nc ipaddress portnum</code><br>
<br>
If you were connecting to IP 1.2.3.4 at port 9876, it would be:<br>
<code> nc 1.2.3.4 9876</code><br>
Or to get a little more detail:<br>
<code> nc -nv 1.2.3.4 9876</code><br>
<br>
Try that first! - substituting the IP and port that you are connecting to.<br>
<br>
If you tried it, you might be saying "Well, now what?". This is all I got:<br>
<pre>
┌──(kali㉿kali)-[~]
└─$ nc -nv 10.0.0.19 21141
(UNKNOWN) [10.0.0.19] 21141 (?) open

</pre>
<br>
See all that nothingness after the nc command where I should be getting somethingness?!<br>
<br>
Remember that Crunkbunny said:<br>
<code>If you use netcat to send a certain favorite word of mine ("kaboom" of course) to a certain port (21141) on this machine...</code><br>
<br>
So how do you send a word using <code>netcat</code>? The simplest way would be to connect, as you did above, type in the word, and hit Enter!
</span>
</details>
<br>
# Level 32 - Penguins and Kitties and Snakes, Oh My!
 Netkitty1, the first netkitty ever (whatever that means) needs your help! This time, she's automated the netcat process, but needs you to fill in a couple gaps. Let's see how!

<details>
<summary>Level 32 - Hint</summary>

<br>
<span style="color:DodgerBlue">
You have some steps to perform here:<br>
<ul>
<li>Decode the username</li>
<li>Download the Python script</li>
<li>Edit the Python script</li>
<li>Run the Python script (might need to search for how to do this online)</li>
</ul>
</span>
</details>
<br>
<details>
<summary>Level 32 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
You have some steps to perform here:<br>
<ul>
<li>Decode the username</li>
<ul>
<li><code>hURL -b YmFzdGV0</code></li>
<li> ... or use <a href="https://cyberchef.org">CyberChef</a> or a similar online resource</li>
<li> to get the username: bastet</li>
</ul>
<li>Download the Python script</li>
<ul>
<li><code>wget targetip:65534/hack_the_cat.py</code></li>
<li><i>You may have noticed that we're just downloading the Python file in netkitty1's home directory. You could technically <code>cat</code> out the file, highlight the text, copy, paste in to a new file on your machine, save that and go from there. While that may seem most comfortable at first, I recommend you try this CLI way instead. Once you get the hang of it, you may find it can save time in situations like this!</i></li>
</ul>
<li>Edit the Python script</li>
<ul>
<li>Now that it's on your local machine, you can edit the script using any number of text editing apps.</li>
<li>I'd recommend something that does syntax highlighting (color codes the program's syntax to make it easier to edit stuff). If you want to be able to do it graphically (so you can use your mouse to edit), I'd recommend VS Code or its open-source alternative code-oss. You don't need all its features for our usage here, but it might be good to be familiar with the app nonetheless.</li>
<li>Try running <code>code-oss</code> from within Kali to see if you have it installed.<br>
If not, you can use any other text editor for now.
</li>
<li>netkitty1 marked the area where you need to edit the script. When you're done, that section should look something like this (of course, replace the target IP address to suit your environment):<br>
<image src="/images/netkitty1_codeoss.png"></image>
</li>
<li>Remember to save your changes!</li>
</ul>
<li>Run the Python script</li>
<ul>
<li>Make sure you're at the CLI in the same location as the script file and run: <code>python hack_the_cat.py</code><br>
<i>note that on some systems you might need to run it using <code>python3 hack_the_cat.py</code></i></li>
<li>You should see something like:<br>
<image src="/images/netkittyhax1.png"></image></li>
<li>It will continue until eventually, it gets to:<br>
<image src="/images/netkittyhax2.png"></image></li>
<li>Did ... did we just get <i>another</i> step?</li>
</ul>
<li>Yes, we did</li>
<ul>
<li>Use OSINT to find out bastet's home city and you should come across something like this Wikipedia article naming Bubastis as the city (remember the password is all lowercase):
<image src="/images/bastet_home.png"></image></li>
</ul>
</ul>
</span>
</details>
<br>
# Level 33 - Rock & Roll
 Bastet has asked for your aid, will you answer?

<details>
<summary>Level 33 - Hint</summary>

<br>
<span style="color:DodgerBlue">
Similar to last time - kind of:
<ul>
<li>Find the username (remember waaay back in the day when you found a specific piece of text in a text file?)</li>
<li>Download the Python script</li>
<li>Edit the Python script</li>
<li>Run the Python script</li>
</ul>
</span>
</details>
<br>
<details>
<summary>Level 33 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
Similar to last time - kind of:
<ul>
<li>Find the username (remember waaay back in the day when you found a specific piece of text in a text file?)</li>
<ul>
<li>I won't go into details here, since we've covered <code>grep</code> before:<br>
<code>grep mafdet forgersandforgeries.txt</code></li>
</ul>
<li>Download the Python script</li>
<ul>
<li><code>wget targetip:65530/hackmafdet.py</code></li>
</ul>
<li>Edit the Python script</li>
<ul>
<li>This one requires one more step, editing a Python range.</li>
<li>Python ranges can be defined with just one number, the endpoint. Python will assume you want all the numbers from 0 to that number.</li>
<li>BUT!!!! Note that if you were to, for example give 10 as the range with:<br> <code>range(10)</code><br>
...Python would count from 0 to 9. That range stop parameter is what they call "exclusive" and is the same as saying:<br>
<code>range(up to, but not including this number here)</code><br></li>
<li>In our example, then, the edit should look like:<br>
<image src="/images/hackmafdet.png"></image>
</li>
</ul>
<li>Run the Python script</li>
<ul>
<li>Same as before:<br>
<code>python hackmafdet.py</code><br>
</li>
<li>After some waiting around, you should see...<br>
<image src="/images/mafdetrocks_pwhint.png"></image></li>
</ul>
<ul>
<li>ANOTHER STEP?! These cats, I tell you ...</li>
<li>Check the MD5 hash in a hash lookup tool:<br>
<image src="/images/mafdetrocks_hashlookup.png"></image></li>
</ul>
</ul>
</span>
</details>
<br>
# Level 34 - PIN
Mafdet, the music fan, ran across an account to hack. Similar to the last few, with a bit of a twist.

<details>
<summary>Level 34 - Hint</summary>

<br>
<span style="color:DodgerBlue">
Similar to last time - kind of:
<ul>
<li>Username is given</li>
<li>Download the Python script</li>
<li>Edit the Python script</li>
<li>Run the Python script, BUT save the Python script output to a file</li>
<li>Find some magical way to search through the output</li>
</ul>
</span>
</details>
<br>
<details>
<summary>Level 34 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
Similar to last time - kind of:
<ul>
<li>Username is given: sekhmet</li>
<li>Download the Python script</li>
<ul>
<li><code>wget targetip:65521/hacksekhmet.py</code></li>
</ul>
<li>Edit the Python script.<br>
When you're done, it should look something like:<br>
<image src="/images/hacksekhmet.png"></image></li>
<br>
<li>Run the Python script, BUT save the Python script output to a file
There are multiple ways to do this, I'll cover two here:<br>
</li>
<ul>
<li><code>python hacksekhmet.py > hacksekhmetoutput.txt</code><br>
The <code>></code> redirects a command's output from <b>stdout</b> (outputting at the CLI screen) to a file of your choosing - in this case, <b>hacksekhmetoutput.txt</b>. If the file doesn't exist, this command will create it. Also note that if the file <i>does</i> exist, this will overwrite it without asking for permission!
</li>
<li><code>python hacksekhmet.py | tee hacksekhmetoutput.txt</code><br>
Piping (<b>pipe</b> is what the <code>|</code> is called) your command's output to <code>tee</code> also redirects your command's output to the file you give it. The key difference is that it <i>also</i> still outputs it to the CLI. This way you can keep an eye on the progress but still also have the output in a file for later.
</li>
<li>Either way, you should get a file that has contents that look a lot like this:<br>
<image src="/images/sekhmetbrute.png"></image></li>
</ul>
<li>Find some magical way to search through the output</li>
<ul>
<li>Remember our friend <code>grep</code>? Use that to search for <b>success</b> in the file <b>hacksekhmetoutput.txt</b>:<br>
<pre>└─$ grep success hackout.txt<br>
... no output here! ...</pre>
</li>
<li>Adjust to make sure you search case <b>insensitively</b> as Mafdet suggested:<br>
<pre>└─$ grep -i success hackout.txt<br> 
       SucCeSS - *sekhmet-9051* is right. B64 decode:</pre><br>
</li>
<li>We found it! Kind of? It seems like there might be something on the next line or something, so adjust for that again using the <code>-A</code> parameter:<br>
<pre>└─$ grep -i success hackout.txt -A1 
       SucCeSS - *sekhmet-9051* is right. B64 decode:  
       bWFmZGV0eW91cHVuaw==</pre><br>
</li>
<li>More work?! Who put this thing together?! By now, you're a pro at identifying and decoding base64 strings right?<br>
<pre>└─$ hURL -b bWFmZGV0eW91cHVuaw==

Original string       :: bWFmZGV0eW91cHVuaw==
base64 DEcoded string :: mafdetyoupunk</pre>
</li>
</ul>
</ul>
</span>
</details>