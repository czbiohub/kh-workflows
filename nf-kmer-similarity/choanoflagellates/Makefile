D1=work
D2=/mnt/pureScratch/olga/nextflow


aws:
	nextflow run czbiohub/nf-kmer-similarity \
		-r olgabot/support-csv-directory-or-sra -latest --sra "PRJNA419411" \
		-profile aws


local:
	sudo /home/olga/bin/nextflow run czbiohub/nf-kmer-similarity \
		--outdir ~/data/kmer-hashing/choanoflagellates/richter2018/rawreads/ \
	 	-r olgabot/support-csv-directory-or-sra \
		-latest --sra "PRJNA419411" \
		-work-dir /mnt/pureScratch/olga/nextflow/ \
		-profile local

sra_local:
	sudo /home/olga/bin/nextflow run czbiohub/nf-kmer-similarity \
		--outdir ~/data/kmer-hashing/choanoflagellates/richter2018/rawreads/ \
	 	-r olgabot/support-csv-directory-or-sra \
		-latest \
		-resume \
		--read_pairs '/home/olga/data/sra-explorer/choanoflagellates/*{1,2}.fastq.gz' \
		-profile local


move_workdir:
	ls -1 ${D1} | xargs -I {} -P 8 -n 1 sudo rsync -avh ${D1}/{} ${D2}

transcriptomes:
	sudo /home/olga/bin/nextflow run czbiohub/nf-kmer-similarity \
                --outdir ~/data/kmer-hashing/choanoflagellates/richter2018/assembled_transcriptomes/ \
                -r olgabot/support-csv-directory-or-sra \
		--molecules dna,protein \
                -latest --fastas '/home/olga/data/figshare/choanoflagellates_richter2018/1_choanoflagellate_transcriptomes/*.fasta' \
		-resume \
                -profile local


sync_transcriptomes:
	aws s3 sync \
		~/data/kmer-hashing/choanoflagellates/richter2018/assembled_transcriptomes/ \
		s3://kmer-hashing/choanoflagellates/richter2018/assembled_transcriptomes/
