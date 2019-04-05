aws:
	nextflow run czbiohub/nf-kmer-similarity \
		-r olgabot/support-csv-directory-or-sra -latest --sra "PRJNA419411" \
		-profile aws


local:
	sudo /home/olga/bin/nextflow run czbiohub/nf-kmer-similarity \
	 	-r olgabot/support-csv-directory-or-sra \
		-latest --sra "PRJNA419411" \
		-work-dir /mnt/ibm_lg/olga/nextflow-workdir/ \
		-profile local
