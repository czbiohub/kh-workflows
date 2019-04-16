D1=/mnt/ibm_lg/olga/nextflow-workdir
D2=/mnt/pureScratch/olga/nextflow

aws:
	nextflow run czbiohub/nf-kmer-similarity -latest --sra "SRP016501" \
		-profile aws

sra_local:
	sudo /home/olga/bin/nextflow run czbiohub/nf-kmer-similarity -latest --sra "SRP016501" \
		--outdir s3://kmer-hashing/merkin2012/ \
		-work-dir /mnt/pureScratch/olga/nextflow/ \
                -profile local

move_workdir:
	ls -1 ${D1} | xargs -I {} -P 8 -n 1 sudo rsync -avh ${D1}/{} ${D2}


local:
	sudo /home/olga/bin/nextflow run czbiohub/nf-kmer-similarity -latest \
		--read_pairs /home/olga/data/sra-explorer/merkin2012/*{1,2}.fastq.gz \
		--outdir /home/olga/data/kmer-hashing/merkin2012/ \
                -profile local


sync:
	aws s3 sync \
		/home/olga/data/kmer-hashing/merkin2012 \
		s3://kmer-hashing/merkin2012/
