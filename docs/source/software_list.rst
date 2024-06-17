SOFTWARE PACKAGES
=================

General software / software to install other softwares
------------------------------------------------------

Software are installed mostly by recompiling their source code or directly
by their binary distribution. In both cases they are available to the 
final user through an `environment module <https://modules.readthedocs.io/en/latest/>`_.
They can be also installed as `mamba environments <https://mamba.readthedocs.io/en/latest/>`_

To see the currently available modules on the cluster type::

  module avail

Highlighted names/versions are preloaded for you, otherwise to use
a certain software version (e.g. to use R version 4.3.1) please use::

  module load R/4.3.1

or the equivalent (more handy?) command::

  ml R/4.3.1

Issuing a `module load` without specifying a version automatically loads
the latest version for you.

Finally, all the software installed under ``/opt/bin`` are automatically available to use.
