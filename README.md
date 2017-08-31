# sadness
meditations on stupidity

## sudo

At work, we have a game called "teapotting" wherein if someone walks away from an unlocked computer, you send an email to the teapots@ alias which announces that you need the rock of shame.  In this game, key loggers (hard or soft) are forbidden.

Some of our teapotting games are getting out of control.  One of our users accidentally leaked his password by typing it into hipchat.  Someone else immediately ssh’d into his system and grabbed his ssh keys when they saw that.  Since he was using passphrase-less keys (doh) -or- useing his login for the keys, this worked out.   They had gone from access to persistence.

![needs](https://raw.githubusercontent.com/rsr-at-mindtwin/sadness/master/attacker%20hierarchy%20of%20needs.png)

They used the stolen password to send a mail to the teapots@ alias by using remote desktop using the password (oops).  He didn’t figure out how they did it, but given the password leak ended up changing his password just in case … but didn’t fix the ssh keys by revoking/deleting them.  

Meanwhile, the guilty parties tried various means to use their ssh access to send an email.  But because AppleScript doesn’t work from the command line, being garbage and mostly unsupported at this point, attempts to do that mostly just hanged and otherwise fucked up.  So they were stuck: without the password, they can't remote desktop, without remote desktop, they can't send a mail.  They’ve been trying to get access to his password again but are stuck.

Getting the password is easy if you lay a trap and are patient.  So I wrote this script for them in about ten minutes and after being deployed for about 3 weeks, it worked.  No need for fancy ptys or anything else.

Now, this is a dirty trick and I feel guilty about it.  I'm probably going to let the guy know but I only want to do that if he doesn't leak about what he knows (and how).  If only people could be trusted.
