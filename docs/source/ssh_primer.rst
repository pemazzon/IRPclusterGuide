.. _ssh_access:

=============
An SSH primer
=============

The **S**\ecure **SH**\ell protocol is a way to connect to a remote 
machine using an encrypted connection. It is a "text only" protocol
but it can be used to "tunnel" other kind of connections too.

It is natively supported by the "main" operative systems (e.g. Windows,
Mac OSX and Linux), meaning that you can open a terminal emulator on 
each one of them and simply type::

  ssh ...something...

SSH commands (ssh, scp, ...) can do a lot of things and they have a
lot of options to accomodate very complex network configurations, but
in their simplest form they're not so complicated to understand once
you have learned to identify the various "moving parts".

We will introduce 2 different concepts that will greatly simplify
the access to the IRP cluster: `public key authentication <pubkey>`_
and the `ssh config file <sshconfig>`_.

.. _pubkey:

*************************
Public key authentication
*************************

When you are connecting to a remote machine through ssh you are
normally prompted to insert a password. This is not the only way to 
authenticate your user though. Besides: it might get boring after a 
while and it's not very `"automation friendly"` either. You can 
(if the remote machine has been configured appropriately) use the
so called `"public key infrastructure"` to identify yourself using 
a file (your **private key**), as long as your **public key**
(another file `cryptographically coupled` with the private
counterpart) has been installed on the remote machine.

The whole mechanism is exploited in 3 steps:

  #. create a ( private key, public key ) couple
  #. install the (public) key on the remote machine
  #. verify you can connect without a password

Generate a key couple
=====================

You can create different (based on the cryptographical mechanism) kind
oif keys. We will use the more "robust" Ed25519 algorithm for our examplei.
Open a terminal and type::

  ssh-keygen -t ed25519 -a 150 -f id_mykey

This command creates **two** files called ``id_mykey`` and ``id_mykey.pub`` 
in the current directory using the Ed25519 crypto algorithm.

.. warning::

   During the creation of your keys you will be prompted
   for a `passphrase`: this is a password to protect your key
   in the event it's stolen. 
   
   **DO NOT** skip this passage, please!

   **DO NOT** forget your passphrase ;-)

The two files `lives` normally inside the ``.ssh`` directory in your user's
`home folder`. For the user `paolo` this would be:

  * On Linux ``/home/paolo/.ssh``
  * On MacOS ``/Users/paolo/.ssh``
  * ON Windows ``C:\Users\paolo\.ssh``
 
If the above directory doesn't exist it's time to create it!

Once you create the directory **move** the two files inside there.

.. note::

   There are some aspects that you better not underestimate when it
   comes to the security of the above directory and especially your
   **private** key. If a user - that is not you - can have access to your
   private key, either because you didn't restrict access to the 
   ``.ssh`` directory or becuse you left a copy of your private key 
   somewhere, that user can have access to your same resources and
   basically **be you** somewhere. This is why you also provide a 
   password to protect your key in case it's stolen: your key is
   useless if it can't be unlocked with the right passphrase.

Copy the (public) key on the remote machine
===========================================

You have been provided a username (e.g. paolomazzon) and password to 
access the remote machine (e.g. 192.168.87.198). Now you want to be 
able to login with your key:

.. code:: console

   ssh-copy-id paolomazzon@192.168.87.198:

The remote system should answer with something like:

.. code:: console

   /usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
   /usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
   paolomazzon@192.168.87.198's password:

Insert your user's password (hopefully for the last time ;-) ):

.. code:: console

   Number of key(s) added: 1

   Now try logging into the machine, with:   "ssh 'paolomazzon@192.168.87.198'"
   and check to make sure that only the key(s) you wanted were added.

Verify you can connect without a password
=========================================

Notice one of the last messages you received was:

.. code:: console

   Now try logging into the machine, with:   "ssh 'paolomazzon@192.168.87.198'"

so let's try it! ::

   ssh paolomazzon@192.168.87.198

.. note::

   single quotes in the above command are not mandatory!

If everything goes well you should get access to the remote system 
without providing any password:

.. image:: images/hpc-frontend.png

.. note::

   For the curiously inclined of you: you can try the above command with
   ``ssh -v`` and convince yourself that you are actually using the 
   public key. Find below an excerpt of the message exchange between 
   your and the remote PC:

   .. code:: console

      OpenSSH_8.9p1 Ubuntu-3ubuntu0.7, OpenSSL 3.0.2 15 Mar 2022
      ...
      debug1: Connecting to 192.168.87.198 [192.168.87.198] port 22.
      debug1: Connection established.
      debug1: identity file /home/paolo/.ssh/id_ed25519 type 3
      ...
      debug1: Authenticating to 192.168.87.198:22 as 'paolomazzon'
      ...
      debug1: Will attempt key: /home/paolo/.ssh/id_ed25519 ED25519 SHA256:Ac5bL7LAIzQCVrQGGrRN2M3i36hT6jP0nlEksN9w7+0 explicit agent
      ...
      debug1: Authentications that can continue: publickey,password
      debug1: Next authentication method: publickey
      debug1: Offering public key: /home/paolo/.ssh/id_ed25519 ED25519 SHA256:Ac5bL7LAIzQCVrQGGrRN2M3i36hT6jP0nlEksN9w7+0 explicit agent
      debug1: Server accepts key: /home/paolo/.ssh/id_ed25519 ED25519 SHA256:Ac5bL7LAIzQCVrQGGrRN2M3i36hT6jP0nlEksN9w7+0 explicit agent
      Authenticated to 192.168.87.198 ([192.168.87.198]:22) using "publickey".
      ...
      ...
      Linux frontend 6.1.0-18-amd64 #1 SMP PREEMPT_DYNAMIC Debian 6.1.76-1 (2024-02-01) x86_64
      ...
      ...


.. _sshconfig:

The SSH config file
===================

TBD

