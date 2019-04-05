aws:
	nextflow run czbiohub/nf-kmer-similarity -latest --sra "SRP016501" \
		-r olgabot/support-csv-directory-or-sra \
		-profile aws

local:
	sudo /home/olga/bin/nextflow run czbiohub/nf-kmer-similarity -latest --sra "SRP016501" \
                -r olgabot/support-csv-directory-or-sra \
		-work-dir /mnt/ibm_lg/olga/nextflow-workdir/ \
                -profile local

