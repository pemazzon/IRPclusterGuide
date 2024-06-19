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
a file (your **private key**), as long as your **public key**, which
is another file that is `cryptographically coupled` with the private
counterpart, has been installed on the remote machine.

The whole mechanism is exploited in 3 steps:

  #. create a ( private key, public key ) couple
  #. install the public key on the remote machine
  #. verify you can connect without a password

Generate a key couple
=====================

You can create different (based on the cryptographical mechanism) kind
of keys. We will use the more "robust" Ed25519 algorithm for our example::

  ssh-keygen -t ed25519 -a 150 -f id_mykey

This command creates **two** files called ``id_mykey`` and ``id_mykey.pub`` 
in the current directory using the Ed25519 crypto algorithm.

.. warning::

   During the creation of your keys you will be prompted
   for a `passphrase`: this is a password to protect your key
   in the event it's stolen. 
   
   **DO NOT** skip this passage, please!

   **DO NOT** forget your passphrase ;-)

.. _sshconfig:

The SSH config file
===================
