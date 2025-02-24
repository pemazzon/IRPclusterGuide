=================
SOFTWARE PACKAGES
=================

******************************************************
General software / software to install other softwares
******************************************************

Software are installed mostly by recompiling their source code or directly
by their binary distribution. In both cases they are available to the 
final user through an `environment module <https://modules.readthedocs.io/en/latest/>`_.

  * To see the currently available modules on the cluster type::

        module avail

    Highlighted names/versions are preloaded for you, otherwise to use
    a certain software version (e.g. to use R version 4.3.1) please use::

        module load R/4.3.1

    or the equivalent (more handy?) command::

        ml R/4.3.1

    Issuing a `module load -something-` without specifying a version automatically loads
    the latest version for you, e.g. to load the latest R version you can simply use::

        ml R

.. _mamba:

  * Software can be also installed as `mamba environments <https://mamba.readthedocs.io/en/latest/>`_.
    This kind of softwares are also available as modules to load but are not autoloaded by default.

  * The `SPACK framework <https://spack.io/>`_ is also available.

  * Finally, all the softwares installed under ``/opt/bin`` are automatically available to use.

*************************************
List of available softwares (version)
*************************************

  * annovar (20200607)  `<https://annovar.openbioinformatics.org/en/latest/>`_
  * bbmap (39.06)  `<https://jgi.doe.gov/data-and-tools/software-tools/bbtools/>`_
  * bcftools (1.20)  `<https://www.htslib.org/download/>`_
  * bedtools (2.31.1)  `<https://github.com/arq5x/bedtools2>`_
  * blast (2.16.0)  `<https://blast.ncbi.nlm.nih.gov/Blast.cgi>`_
  * bowtie2 (2.5.4)  `<https://github.com/BenLangmead/bowtie2>`_
  * bwa (0.7.18)  `<https://github.com/lh3/bwa>`_
  * fastp  `<https://github.com/OpenGene/fastp>`_
  * fastqc  `<https://www.bioinformatics.babraham.ac.uk/projects/fastqc/>`_
  * gatk (4.5.0.0)  `<https://gatk.broadinstitute.org/hc/en-us>`_
  * R  `<https://www.r-project.org/>`_  This is installed as a :ref:`mamba environment <mamba>`. Available versions are:

     * 4.3.1
     * 4.2.3

  * nextflow  `<https://nextflow.io/>`_
  * picard (3.3.0)  `<https://broadinstitute.github.io/picard/>`_
  * samtools (1.20)  `<https://www.htslib.org/>`_
  * STAR (2.7.11b)  `<https://github.com/alexdobin/STAR>`_
  * subread (2.0.6)  `<https://subread.sourceforge.net/>`_
  * trimmomatic  `<https://github.com/usadellab/Trimmomatic>`_
  * umi_tools (latest)  `<https://github.com/CGATOxford/UMI-tools>`_   This is installed as a :ref:`mamba environment <mamba>`.
  * vcftools (0.1.16)  `<https://vcftools.sourceforge.net/>`_
