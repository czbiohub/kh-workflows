human_mouse_zebrafish:
	nextflow run czbiohub/nf-kmer-similarity -latest -profile aws \
		--samples s3://kmer-hashing/hematopoeisis/smartseq2/human_mouse_zebrafish/samples.csv


merkin2012_aws:
	nextflow run czbiohub/nf-kmer-similarity -latest --sra "SRP016501" \
		-r olgabot/support-csv-directory-or-sra \
		-profile aws

merkin2012_local:
	sudo /home/olga/bin/nextflow run czbiohub/nf-kmer-similarity -latest --sra "SRP016501" \
                -r olgabot/support-csv-directory-or-sra \
		-work-dir /mnt/ibm_lg/olga/nextflow-workdir/ \
                -profile local


choanoflagellates:
	nextflow run czbiohub/nf-kmer-similarity \
		-r olgabot/support-csv-directory-or-sra -latest --sra "PRJNA419411" \
		-profile aws


choanoflagellates_local:
	nextflow run czbiohub/nf-kmer-similarity \
	 	-r olgabot/support-csv-directory-or-sra \
		-latest --sra "PRJNA419411" \
		-work-dir /mnt/ibm_lg/olga/nextflow-workdir/ \
		-profile local
