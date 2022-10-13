---
layout: post
title:  " Part 0 - The Hax that Rocks the Cradle Intro"
date:   2022-08-26 17:19:23 -0500
categories: thehaxthatrocksthecradle
---

Welcome to The Hax that Rocks the Cradle!

# What Is This Anyway?
The purpose of this intentionally vulnerable VM is to help you get used to some security related concepts while learning Linux stuff along the way.

The first few challenges are web related. Nothing in depth, but you'll need to be able to browse to the victim host and use both your browser and a tool or two to enumerate the site.

After those initial web related stages, we'll delve into the Linux CLI (command line interface) for the rest of your time here! It can be intimidating at first, leaving the comfort of a graphical environment. Hopefully by the time you're done, you will have used a lot of basic CLI commands so much that it won't be nearly so intimidating.

# Who is This For?
The target audience is anyone who is interested in learning a bit more about security and about Linux (specifically the CLI).
The guide will assume you know how to use a computer, look stuff up online, and open a terminal window, and ... that's mostly it. There will be clues inside the VM itself, and you'll be filled in on more here if you need it.

# What Do You Need?
An "attacking machine" that is preferably Linux, preferably Kali or Parrot. While not strictly required, this will make using (and possibly installing) the needed tools easier.

New to VMs? Check this out: 

If **not** using Kali or Parrot, you'll need to able to use or install these applications or others that can perform their function - of course if you use another app, the detailed walk-through will be less helpful:
- nmap
- Web directory brute forcer
- SSH client
- base64 decoder (or use one online)
- Code editor with Python syntax highlighting (or just a text editor if you want to go old school)
- SSH brute forcer
- cewl - or another tool that makes a wordlist based on site contents
- hashcat - or another password cracking tool and one that can mangle wordlists

Kind of a lot of things, right? That's why I'd recommend you just use Kali or Parrot ... one step at a time!