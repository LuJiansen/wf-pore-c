
These are instructions to install and run the workflow on command line.
You can also access the workflow via the
[EPI2ME Desktop application](https://labs.epi2me.io/downloads/).

The workflow uses [Nextflow](https://www.nextflow.io/) to manage
compute and software resources,
therefore Nextflow will need to be
installed before attempting to run the workflow.

The workflow can currently be run using either
[Docker](https://www.docker.com/products/docker-desktop
or [Singularity](https://docs.sylabs.io/guides/3.0/user-guide/index.html)
to provide isolation of the required software.
Both methods are automated out-of-the-box provided
either Docker or Singularity is installed.
This is controlled by the
[`-profile`](https://www.nextflow.io/docs/latest/config.html#config-profiles)
parameter as exemplified below.

It is not required to clone or download the git repository
in order to run the workflow.
More information on running EPI2ME workflows can
be found on our [website](https://labs.epi2me.io/wfindex).

The following command can be used to obtain the workflow.
This will pull the repository in to the assets folder of
Nextflow and provide a list of all parameters
available for the workflow as well as an example command:

```
nextflow run epi2me-labs/wf-pore-c --help
```
To update a workflow to the latest version on the command line use
the following command:
```
nextflow pull epi2me-labs/wf-pore-c
```
A demo dataset is provided for testing of the workflow.
It can be downloaded and unpacked using the following commands:
```
wget https://ont-exd-int-s3-euwst1-epi2me-labs.s3.amazonaws.com/wf-pore-c/wf-pore-c-demo.tar.gz
tar -xzvf wf-pore-c-demo.tar.gz
```
The workflow can then be run with the downloaded demo data using:
```
nextflow run epi2me-labs/wf-pore-c \
	--bam 'wf-pore-c-demo/porec_test.concatemers.bam' \
	--chunk_size 100 \
	--cutter 'NlaIII' \
	--hi_c \
	--mcool \
	--paired_end \
	--paired_end_maximum_distance 200 \
	--paired_end_minimum_distance 100 \
	--phased_vcf 'wf-pore-c-demo/porec_test.phased_variants.vcf.gz' \
	--ref 'wf-pore-c-demo/porec_test.fasta' \
	--vcf 'wf-pore-c-demo/porec_test.phased_variants.vcf.gz' \
	-profile standard
```
For further information about running a workflow on
the command line see https://labs.epi2me.io/wfquickstart/
