### Adds Notification Center Support for SSH-Agent.

From HackerNews Comment: https://news.ycombinator.com/item?id=7693143

The source code can be compiled by cloning https://github.com/devinteske/apple and then:

``` cd OpenSSH-186/openssh ./configure --with-pam --with-audit=bsm make ```

You can see from my commits at the following URL what I had to change to add support for Notification Center.

https://github.com/devinteske/apple/tree/master/OpenSSH-186/openssh

Namely I changed the following:
  * openssh/Makefile.in
  * openssh/ssh-agent.c
  * openssh/ssh-agent-notify.m [new]
  * openssh/ssh-agent-notify.h [new]
  
As for the OpenSSH version, Apple forks OpenSSH and then adds things like Keychain and launchd(8) support. So if you want a later version while retaining those features, you'll have to get Apple's customizations applied to a later non-Apple version or wait until Apple does it themselves. Migrating my changes into a non-Apple version simply to say you have the latest version of OpenSSH would mean that you lose keychain and launchd(8) integration. -- Devin
