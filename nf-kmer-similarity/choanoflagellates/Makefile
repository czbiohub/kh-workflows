D1=work
D2=/mnt/pureScratch/olga/nextflow


aws:
	nextflow run czbiohub/nf-kmer-similarity \
		-r olgabot/support-csv-directory-or-sra -latest --sra "PRJNA419411" \
		-profile aws


local:
	sudo /home/olga/bin/nextflow run czbiohub/nf-kmer-similarity \
		--outdir s3://kmer-hashing/choanoflagellates/richter2018/ \
	 	-r olgabot/support-csv-directory-or-sra \
		-latest --sra "PRJNA419411" \
		-work-dir /mnt/pureScratch/olga/nextflow/ \
		-profile local

move_workdir:
	ls -1 ${D1} | xargs -I {} -P 8 -n 1 sudo rsync -avh ${D1}/{} ${D2}
