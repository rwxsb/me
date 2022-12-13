# Week 03 - Boost Notes

## How to connect to our VM via Secure Shell?

Whenever two things connect on the internet there are is a client and a server, daemon is asked to connect (kinda like in old movies where they switch cables for phone connections) so there is a **stateful** network socket connection between two sides because connection is maintained.

We are going to install Secure Shell Server which will serve the purpose of responding to incoming connection requests of clients

When any hacker breaks into any system one of the first things that they install is a reverse shell (which will accept the connections from their computer - backdoor)

SSHD - is one of the better backdoors to install

telnet - is in plain text ?!!?!?!?

## NAT (Network Address Translation) and Bridged 
NAT allows multiple devices to connect to internet via one public IP address, Router helps with this process, mostly via information on `TCP` header.

>Q: What happens when the addresses are Translated down 2 levels. for example,when a VM inside a laptop is also facing a NAT? \
>A: NO, the router won't be seeing the VM unless there is a tunnel. \
>So we need to switch our VM network to Bridged

Bridged tells VM to predent like it is in the same NAT level rather than inside it. So it will get its IP address from our router.

- `ip a` - show all ip addresses

> When you switch to Bridged on VM settings be sure to use correct device.

- `which` vs `type` - type will tell you what is the thing you are executing whether it is a link or overwrite

## What is a loopback device?
The loopback device is a special, virtual network interface that your computer uses to communicate with itself. It is used mainly for diagnostics and troubleshooting, and to connect to servers running on the local machine.

## Who is there?

- `who` running command shows who is logged in and how?

>```bash
>//device login
>poissond tty1         2022-09-13 06:03
>//ssh login IP states is IPv4 of host
>poissond pts/0        2022-09-13 06:05 (192.168.0.234)
>//tmux sessions
>poissond pts/1        2022-09-10 11:13 (tmux(1115).%0)
>poissond pts/2        2022-09-10 11:13 (tmux(1115).%1)
>poissond pts/3        2022-09-10 11:13 (tmux(1115).%2)
>```

Why do I have  3 sessions for tmux when I have two sessions running?

- `Ctrl + B; D` Detaches the session rather than killing it inside tmux running `kill-session` ends the session.
- I actually have 3 sessions but I didn't notice my named session there with two terminal connections
- `last` shows login logs 

## Remote Access 
### Maintaining your own Server (Remote Acces s Questions)

Opening what we have done so far to Internet it is risky, It will be hacked instantly by bot nets even if it is missing a tiny bit of security patch that was released seconds ago.

_Now `good faith` actors are not going to face charges_ - *Department of Justice*

> Is it high time to be a hacker? It is always worth to be a hacker


>Q:What is a Honey Pot? \
>As rob says it sounds like a way to hack the hackers?
> It is a total bait, a fake of your system. That attracts honeys and detects them
>[Honey Pot](https://en.wikipedia.org/wiki/Honeypot_(computing))\
> I would call it a fly trap :D

Enough chit chat with Hacking and Security If you don't want to open your own machine to internet you may buy service
- DigitalOcean
- Azure
- AWS
- Google Cloud
- Bunch of Other Cloud Providers

But be sure that the cloud provider you have is secure.

## Less Windows Will make you look cooler
You may start things headless, We are not talking about decapitating them. It is rather a way of saying to start them as Background Proccesses.

`VBoxManage` - Virtual Box CLI tool that allows you to work on Virtual Box on terminal

> Be sure you add Virtual Box tools to your git bash `$PATH` \
> Remember PATH is the ways to run programs.

- `VBoxManage startvm $vmname --type headless`
> Side Note:\
> VBoxManage has a long help text using pipe and a grep helped a lot\
>`VBoxManage -h | grep $whatever`

- [Learn to Survive Vi](https://rwx.gg/tools/editors/vi/how/survive/)