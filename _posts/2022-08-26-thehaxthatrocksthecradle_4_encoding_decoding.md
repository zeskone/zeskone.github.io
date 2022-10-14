---
layout: post
title:  "Part 4 - The Hax that Rocks the Cradle Encoding and Decoding"
date:   2022-08-26 17:19:23 -0500
categories: thehaxthatrocksthecradle
---

We're going to shift focus now and look at some encoding and decoding of data, with a couple hash-related things thrown in.

First, maybe some quick explanations are in order if you haven't run across these terms before. These are intended to be super quick and simple explanations. Entire books can be written about each of these topics!

# Encoding and Decoding
Encoding data transforms it into another form. The reasons for doing so can vary, but the important part for you to know right now is that if you know how data is encoded, it is easily decoded. No further information is needed.
Typically, if you take a small piece of data (like one word, for example) and encode it, the result is also very small. Likewise, if you take a super long piece of data (like a book), the result will be similarly long.

# Hashing
Hashing also transforms data, but a key difference is that it cannot be reversed ... well, not directly anyway. Even if you know the algorithm used, you can't really take a hash and figure out what the data was originally. What you CAN do hash a piece of data, see if it matches your hash, and if it doesn't, try another piece of data and so on. Sound like a lot of effort? It can be, but for computers, it can go very quickly, depending on the algorithm used.
How about hash length? It's always consistent! A hash created using the MD5 algorithm will be 32 characters. 
Hash a single letter? 32 characters. 
Hash a 10 GB file? 32 characters.

# Encryption and Decryption
Like encoding, encryption also transforms data into another form.
Like encoding, the length of the output also depends on the length of the input.
So what's the difference? One major difference for users is that even if you know the algorithm used, you still need a *key* (think of it like a password - because in many cases, it is one!) to decrypt the data.

# Level 23 - What Does it Mean When People Say "It's All ones and zeroes?"
Let's help Gimli out with this decoding task, the poor guy. He does the best he can.

<details>
<summary>Level 23 - Hint</summary>

<br>
<span style="color:DodgerBlue">
Remember that Gimli mentioned a few things:
bai'nairee to ah'skee (sound it out and look it up if they seem familiar!)
Cyberchef
</span>
</details>
<br>
<details>
<summary>Level 23 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
This one would be tricky if you haven't heard these terms before - I blame the dwarf's accent (which apparently shows up in writing, oddly enough):<br>
bai'nairee = binary<br>
ah'skee = ASCII = American Standard Code for Information Interchange<br>
<br>
ASCII uses numbers to represent characters - pretty much all the characters you see on the face of a standard keyboard have an ASCII number assigned to them.<br>
<br>
CyberChef - An online search for "CyberChef" should lead you to: <a href="https://cyberchef.org">https://cyberchef.org</a><br>
<br>
The interface can be a bit confusing at first, but (among other things) CyberChef lets you convert data from one type to another quickly and easily if you know how the data is encoded.<br>
In our case, we need to convert information <b>from binary</b> to readable text, so either type "binary" in the search field at the top left, or navigate to Data Format > From Binary on the left:<br>
<img src="/images/cyberchef_frombinary.png"><br>
<br>
Drag the box containing the words "From Binary" to the "Recipe" box in the center column.<br>
<img src="/images/cyberchef_addrecipe.png"><br>
<br>
Paste the binary data into the "Input" box at the top right and check the "Output" box:<br>
<img src="/images/cyberchef_converted.png"><br>
<br>
<br>
Too easy? Want to know how did CyberChef do this? Like tedious things? Read on!!!<br>
8 binary bits (8 numbers) = one byte = one character<br>
So, all we need to do is break up the binary string into bytes, each made up of 8 ones/zeros. So:<br>
<code>011110100110000101101110011001010011101001101110011011110111010001100001011100000111001101111001011000110110100001101111</code><br>
becomes:<br>

	<table>
		<thead>
			<tr>
				<th>byte</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>01111010</td>
			</tr>
			<tr>
				<td>01100001</td>
			</tr>
			<tr>
				<td>01101110</td>
			</tr>
			<tr>
				<td>01100101</td>
			</tr>
			<tr>
				<td>00111010</td>
			</tr>
			<tr>
				<td>01101110</td>
			</tr>
			<tr>
				<td>01101111</td>
			</tr>
			<tr>
				<td>01110100</td>
			</tr>
			<tr>
				<td>01100001</td>
			</tr>
			<tr>
				<td>01110000</td>
			</tr>
			<tr>
				<td>01110011</td>
			</tr>
			<tr>
				<td>01111001</td>
			</tr>
			<tr>
				<td>01100011</td>
			</tr>
			<tr>
				<td>01101000</td>
			</tr>
			<tr>
				<td>01101111</td>
			</tr>
		</tbody>
	</table>

<br>
Now for each byte, calculate out the binary to decimal conversion:<br>
	<table>
		<thead>
			<tr>
				<th>byte</th>
				<th>decimal value</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>01111010</td>
				<td>122</td>
			</tr>
			<tr>
				<td>01100001</td>
				<td>97</td>
			</tr>
			<tr>
				<td>01101110</td>
				<td>110</td>
			</tr>
			<tr>
				<td>01100101</td>
				<td>101</td>
			</tr>
			<tr>
				<td>00111010</td>
				<td>58</td>
			</tr>
			<tr>
				<td>01101110</td>
				<td>110</td>
			</tr>
			<tr>
				<td>01101111</td>
				<td>111</td>
			</tr>
			<tr>
				<td>01110100</td>
				<td>116</td>
			</tr>
			<tr>
				<td>01100001</td>
				<td>97</td>
			</tr>
			<tr>
				<td>01110000</td>
				<td>112</td>
			</tr>
			<tr>
				<td>01110011</td>
				<td>115</td>
			</tr>
			<tr>
				<td>01111001</td>
				<td>121</td>
			</tr>
			<tr>
				<td>01100011</td>
				<td>99</td>
			</tr>
			<tr>
				<td>01101000</td>
				<td>104</td>
			</tr>
			<tr>
				<td>01101111</td>
				<td>111</td>
			</tr>
		</tbody>
	</table>
<br>
Remember how I mentioned that each character on a standard keyboard has an ASCII number assigned to it? Now we get to look that up! One easy way to do so from a Linux system (and you're just getting so good at Linux that you might as well do it that way), is to type <code>man ascii</code> since the <code>ascii</code> manual has that chart in it:
<img src="/images/man_ascii.png"><br>
<br>
Now, all you need to do is look up each decimal number and find the corresponding character! So fun!<br>
	<table>
		<thead>
			<tr>
				<th>byte</th>
				<th>decimal value</th>
				<th>ASCII value</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>01111010</td>
				<td>122</td>
				<td>z</td>
			</tr>
			<tr>
				<td>01100001</td>
				<td>97</td>
				<td>a</td>
			</tr>
			<tr>
				<td>01101110</td>
				<td>110</td>
				<td>n</td>
			</tr>
			<tr>
				<td>01100101</td>
				<td>101</td>
				<td>e</td>
			</tr>
			<tr>
				<td>00111010</td>
				<td>58</td>
				<td>:</td>
			</tr>
			<tr>
				<td>01101110</td>
				<td>110</td>
				<td>n</td>
			</tr>
			<tr>
				<td>01101111</td>
				<td>111</td>
				<td>o</td>
			</tr>
			<tr>
				<td>01110100</td>
				<td>116</td>
				<td>t</td>
			</tr>
			<tr>
				<td>01100001</td>
				<td>97</td>
				<td>a</td>
			</tr>
			<tr>
				<td>01110000</td>
				<td>112</td>
				<td>p</td>
			</tr>
			<tr>
				<td>01110011</td>
				<td>115</td>
				<td>s</td>
			</tr>
			<tr>
				<td>01111001</td>
				<td>121</td>
				<td>y</td>
			</tr>
			<tr>
				<td>01100011</td>
				<td>99</td>
				<td>c</td>
			</tr>
			<tr>
				<td>01101000</td>
				<td>104</td>
				<td>h</td>
			</tr>
			<tr>
				<td>01101111</td>
				<td>111</td>
				<td>o</td>
			</tr>
		</tbody>
	</table>

</span>
</details>
<br>
# Level 24 - Casting a Hex on a Target
Zane has a new challenge for us!

<details>
<summary>Level 24 - Hint</summary>

<br>
<span style="color:DodgerBlue">
Look up "base 16" online, hopefully you should find something referring to hexadecimal. Follow that lead!<br>
</span>
</details>
<br>
<details>
<summary>Level 24 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
If you look up hexadecimal, or checked out the Full Answer for Level 23 above, you may have seen that hexadecimal (or hex for short) values can also be looked up on the ASCII table for characters!<br>
<br>
Your choices are to either:<br>
<ul>
<li>Look up the hex values in the ASCII table (<code>man ascii</code>, remember?) one by one and match them up to the letters</li>
<li>Use CyberChef to convert the string you're given from hex to readable letters.</li>
</ul>
<br>
Listen, I'm not one to judge how you spend your time, so I'll leave the decision up to you! Still, it's worth converting at least a few character manually to see how this conversion works!
</span>
</details>
<br>
# Level 25 - Get Used to Seeing This==
Fl4k has a new type of encoding scheme for us to interact with. This one is very commonly used, so pay attention to how it's decoded, and how to recognize data encoded like this!!

<details>
<summary>Level 25 - Hint</summary>

<br>
<span style="color:DodgerBlue">
Your hint from Fl4k was "base(16*4)". Your math teacher would be disappointed if you couldn't multiply that out to: "base64". I could see the look on their face now ...<br>
<br>
</span>
</details>
<br>
<details>
<summary>Level 25 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
Remember the CyberChef! Just check for the "From Base64" recipe and use that!<br>
<br>
Fl4k did mention another way though, installing hURL!<br>
First, check if you have it installed by typing <code>hURL</code> - pay attention to the goofy capitalization!<br>
If you get something like this:<br>
<pre>
└─$ hurl    
Command 'hURL' not found, but can be installed with:
sudo apt install hurl
Do you want to install it? (N/y)
</pre>
You need to install using the command they suggest using. Pay attention to the capitalization again. Yes, I know it's different from the command capitalization. Just go with it!<br>
If you don't have admin ("sudo" or "root" in Linux) rights on the Kali system you're using, you can't install it. In that case, just use CyberChef and then read on to get an idea for how the CLI tool hURL would work.<br>
<br>
To install hURL, run:<br>
<code>sudo apt update && sudo apt install hurl</code><br>
<br>
Now running <code>hURL</code> should bring up the <code>hURL</code> help menu:<br>
<pre>
└─$ hurl
.::[ hURL - hexadecimal & URL (en/de)coder ]::.
v2.1 @COPYLEFT  ->  fnord0 &lt;at&gt; riseup &lt;dot&gt; net

  USAGE: /usr/bin/hURL [ -flag|--flag ] [ -f &lt;file1&gt;,&lt;file2&gt; ] [ string ]

  COMMAND LINE ARGUMENTS
   -M|--menu    => Menu-driven GUI               ;  /usr/bin/hURL -M
   -U|--URL     => URL encode                    ;  /usr/bin/hURL -U "hello world"
   -u|--url     => uRL decode                    ;  /usr/bin/hURL -u "hello%20world"
...
...
</pre>
<br>
Look for the "base64 decode" option in the help menu and the example they give:<br>
<code>   -b|--base64  => base64 decode                 ;  /usr/bin/hURL -b "aGVsbG8gd29ybGQ="</code><br>
<br>
Copy that syntax, but replace their base64 string with the one you got from Fl4k and you should get something like:
<pre>
└─$ hURL -b "YW1hcmE6aXRjaGluZ2ZvcmFmaWdodA=="

Original string       :: YW1hcmE6aXRjaGluZ2ZvcmFmaWdodA==
base64 DEcoded string :: amara:itchingforafight
</pre>
<br>
</span>
</details>
<br>
# Level 26 - You Are Really Gonna Love This
Amara needs help decoding a set of credentials. This encoding scheme is also common. Chances are, you've seen it in use already.

<details>
<summary>Level 26 - Hint</summary>

<br>
<span style="color:DodgerBlue">
Amara's hint, "You are Elle" - sounded out, would be ... URL!<br>
See where some research about URL encoding/decoding can get you! Remember the tools you've already used so far and check their documentation.<br>
<br>
</span>
</details>
<br>
<details>
<summary>Level 26 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
URL decoding is actually a bit easier than some other types of decoding! A lot of characters will typically remain unchanged in a URL decoded string (things like numbers, letters, etc.). When it comes to punctuation though? All bets are off!
Here are some examples:
	<table>
		<thead>
			<tr>
				<th>Normal Character</th>
				<th>Encoded Character</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>space</td>
				<td>%20</td>
			</tr>
			<tr>
				<td>%</td>
				<td>%25</td>
			</tr>			<tr>
				<td>&</td>
				<td>%26</td>
			</tr>			<tr>
				<td>+</td>
				<td>%2B</td>
			</tr>			<tr>
				<td>/</td>
				<td>%2F</td>
			</tr>			<tr>
				<td>=</td>
				<td>%3D</td>
			</tr>			<tr>
				<td>?</td>
				<td>%3F</td>
			</tr>			<tr>
				<td>@</td>
				<td>%40</td>
			</tr>
        </tbody>
    </table>
<br>
URLs may use encoding like this so that, for example, stuff like slashes in a URL don't get interpreted by your browser as a directory indicator.<br>
<br>
Armed with knowledge, I'm sure you were like "Oh, well, clearly, I can just use CyberChef or hURL to decode this!":<br>
<br>
<b>CyberChef:</b><br>
Just follow the previous CyberChef instructions in Level 23, but use the <b>URL decode</b> recipe.<br>
<br>
<b>hURL</b><br>
<pre>
└─$ hURL -u moze%3Athe%20%23%20of%20grenades%20I%20carry%20is%20%3E%2020

Original    :: moze%3Athe%20%23%20of%20grenades%20I%20carry%20is%20%3E%2020
URL DEcoded :: moze:the # of grenades I carry is > 20
</pre>
<br>
<b>Manually</b>
Oh? Those methods were too easy and you want to do it manually?<br>
<ul>
<li>Check out <code>man ascii</code> again.</li>
<li>Those number codes for URL encoding (%xx) are just the 2 character hex value for the character with a % in front of it.</li>
<li>You can use the ASCII chart to find the characters that are represented by each URL encoded section in that string!</li>
</ul>
</span>
</details>
<br>
# Level 27 - The Flip-Side: Encoding
Moze got a username, but needs you to encode something in order to get the password!

<details>
<summary>Level 27 - Hint</summary>

<br>
<span style="color:DodgerBlue">
Check out the options in the tools you've used so far!<br>
</span>
</details>
<br>
<details>
<summary>Level 27 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
<b>CyberChef:</b><br>
Use the <b>To Base64</b> recipe!<br>
<br>
<b>hURL</b><br>
<pre>
└─$ hurl -B stillworkingonmysocialskills                                

Original       :: stillworkingonmysocialskills
base64 ENcoded :: c3RpbGx3b3JraW5nb25teXNvY2lhbHNraWxscw==
</pre>
<br>
</span>
</details>
<br>
# Level 28 - Breakfast Potatoes
Tannis needs your help to get claptrap's password. Get ready to make hash browns! Or maybe just a hash.

<details>
<summary>Level 28 - Hint</summary>

<br>
<span style="color:DodgerBlue">
Check out the options in the tools you've used so far! (I know, it's a copy/paste of the last hint, but I can't help it if it's still relevant!)<br>
</span>
</details>
<br>
<details>
<summary>Level 28 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
<b>CyberChef:</b><br>
Use the <b>MD5</b> recipe!<br>
Note that there isn't a From MD5 option for this like there is for stuff like Base64. Why is that, anyway? Hmm ...<br>
<br>
<b>hURL</b><br>
<pre>
└─$ hurl -m VR-0N1CA

Original   :: VR-0N1CA
MD5 digest :: 29046555bd2ca0ac79506a8f41127503
</pre>
<br>
</span>
</details>
<br>
# Level 29 - Un-Potatoing
Claptrap - the nerve of this robot. Still, since you've decided to be a hacker-for-hire for everyone, you might as well see if you can ... un-hashify something for him.

<details>
<summary>Level 29 - Hint</summary>

<br>
<span style="color:DodgerBlue">
Check out the options in the tools you've used so far! **snicker, snicker**<br>
<br>
Ok, once you've done that and found that it didn't really work, maybe try looking up online what claptrap mentioned in his note.
</span>
</details>
<br>
<details>
<summary>Level 29 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
The tools you've been using so far won't work here. Why is that? You can't reverse the hash the way you can reverse encoding.<br>
<br>
What you CAN do is look up hashes! How? Here's how ...<br>
Let's say someone said you had to figure out which single lower-case letter hashes out to:
<code>b2f5ff47436671b6e533d8dc3614845d</code>.<br>
<br>
Ok, you can't reverse the hash like you can a base64 string. You can, however, hash all the letters in the alphabet:<br>
<pre>
a - 0cc175b9c0f1b6a831c399e269772661
b - 92eb5ffee6ae2fec3ad71c777531578f
c - 4a8a08f09d37b73795649038408b5f33
d - 8277e0910d750195b448797616e091ad
e - e1671797c52e15f763380b45e841ec32
f - 8fa14cdd754f91cc6554c9e71929cce7
g - b2f5ff47436671b6e533d8dc3614845d
</pre>
<br>
Hey! We got a match at <b>g</b>! We successfully did an MD5 hash lookup.<br>
<br>
For this challenge though, tinytina's password is the hash for a whole word! How do we do that?<br>
It's simple, just take an English dictionary, or perhaps a password list. List out all the words individually and make a table that contains the words and their hashes. Then compare the thousands of hashes one by one to the hash you were given! Oooh, fun!<br>
Or ...<br>
See if someone has already done the work of creating the hash table for you, and provides a convenient website where you look up the hash! Yeah, let's do that.<br>
<br>
There are several sites you can use for this. They seem to spring up, die out, or become paid/ad-filled services all the time, so you may need to use a different one depending on when you are reading this.<br>
<br>
As of today, one option is: <a href="https://www.cmd5.org">https://www.cmd5.org</a>.
The interface is pretty minimal, just paste in your hash, click the "decrypt" button, and kablam (literally, in this case):<br>
<img src="/images/cmd5.png"><br>
</span>
</details>
<br>
# Level 30 - Layers
Tinytina needs help unraveling a mystery here, great ready for some multi-step action again!

<details>
<summary>Level 30 - Hint</summary>

<br>
<span style="color:DodgerBlue">
For the username, just use some OSINT.<br>
<br>
For the password, just remember the tools we've used so far, and be ready to use them a few times.
</span>
</details>
<br>
<details>
<summary>Level 30 - Full Answer</summary>

<br>
<span style="color:MediumSeaGreen">
For the username, use the hints Tinytina gave you and just do an online search:<br>
<img src="/images/crunkbunny.png"><br>
<br>
Remember that it should be all lowercase and one word when you use it as the username!<br>
<br>
For the password:<br>
First, let's tackle the base64 layers.<br>
<b>CyberChef:</b><br>
Use the <b>From Base64</b> recipe like before, but 3 times!<br>
<img src="/images/cyberchef_multi.png"><br>
<br>
<b>hURL</b><br>
Just run hURL on the string you were given. Run it again on the result, and one more time on that result:<br>
<img src="/images/hurl_multi.png"><br>
<br>
At this point, whether you used hURL or CyberChef, you're left with an MD5 hash, which you can recognize by its 32 character length and only using character used to count in hexadecimal (0-9 and a-f):<br>
<code>8800b005829650f3ee6f8744b5b2466e</code><br>
<br>
Do an online lookup for this hash like before and you should get:<br>
<code>badaboom</code><br>

</span>
</details>
<br>