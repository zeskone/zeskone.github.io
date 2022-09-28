---
layout: post
title:  "The Hax that Rocks the Cradle Brute Force"
date:   2022-08-26 17:19:23 -0500
categories: thehaxthatrocksthecradle
---

<br>
# Level 35 - This One's Not About Brute Force!
Ok, so the rest of these levels will involve brute forcing, but this one doesn't. \\(o_O)/
<br>Sekhmet, in all her anger about Mafdet, also found some other account info!

<details>
<summary>Level 32 - Hint</summary>

<br>
<span style="color:DodgerBlue">
Find out how to make a file executable in Linux.
</span>
</details>
<br>
<details>
<summary>Level 32 - Full Answer</summary>

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