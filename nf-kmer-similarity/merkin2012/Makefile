D1=/mnt/ibm_lg/olga/nextflow-workdir
D2=/mnt/pureScratch/olga/nextflow

aws:
	nextflow run czbiohub/nf-kmer-similarity -latest --sra "SRP016501" \
		-r olgabot/support-csv-directory-or-sra \
		-profile aws

local:
	sudo /home/olga/bin/nextflow run czbiohub/nf-kmer-similarity -latest --sra "SRP016501" \
		--outdir s3://kmer-hashing/multispecies/merkin2012/ \
                -r olgabot/support-csv-directory-or-sra \
		-work-dir /mnt/pureScratch/olga/nextflow/ \
                -profile local

move_workdir:
	ls -1 ${D1} | xargs -I {} -P 8 -n 1 sudo rsync -avh ${D1}/{} ${D2}


