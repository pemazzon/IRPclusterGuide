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

List of available softwares
---------------------------

  * bbmap/39.06
  * bcftools/1.20
  * bedtools/2.31.1
  * bowtie2/2.5.4
  * bwa/0.7.18
  * fastp
  * fastqc
  * gatk/4.5.0.0
  * mamba/1.4.2
  * mamba/R-4.2.3
  * mamba/R-4.3.1
  * nextflow
  * R/4.2.3
  * R/4.3.1
  * samtools/1.20
  * spack/0.21.2
  * STAR/2.7.11b
  * subread/2.0.6
  * trimmomatic
  * umi_tools/latest
  * vcftools/0.1.16
