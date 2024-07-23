.. _SLURM:

===================
The SLURM scheduler
===================

You're probably reading this page from your notebook or desktop PC,
a.k.a. your "personal computer". When you use a personal computer you
interact with it in a so called "interactive way". You type some
command or click somewhere and the computer is ready to respond to 
your inputs in real time. This is normal since you are the only user
(e.g. the only simultaneous user) of your PC. This is not, however, 
the typical interaction you have when you use a computing cluster: 
that would be a "luxury" if you consider that computing clusters are
normally shared by many users and some of them are worth billions (with "b"...).

In general when you use a shared computing resource some "engage rules"
must be laid down to regulate the requests for computing needs coming
from all the users.

The interaction with the computer is therefore changed to a less interactive
way:

  #. resource requests are collected;
  #. the site-defined policy are applied;
  #. the "next in line" is chosen and run;
  #. results (or errors) are delivered to the user;
  #. the loop starts again.

The program that collects the various requests and runs the loop is 
called "Resource Manager". The one running on the IRP cluster, in
particular, is called "Simple Linux Utility for Resource Management" or
simply SLURM.


