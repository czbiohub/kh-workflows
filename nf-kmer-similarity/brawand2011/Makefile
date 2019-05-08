DIR=/mnt/ibm_lg/olga/sra-explorer/brawand2011

aws:
	nextflow run czbiohub/nf-kmer-similarity -latest --sra "SRP016501" \
		-r olgabot/support-csv-directory-or-sra \
		-profile aws

local:
	sudo /home/olga/bin/nextflow run czbiohub/nf-kmer-similarity -latest \
		--samples samples.csv \
		--outdir /home/olga/data/kmer-hashing/brawand2011/ \
		-r master \
		-resume \
		-e.process.executor=local \
                -profile local \
		--ksizes 15,21,27 \
		--log2_sketch_sizes 10,11,12,13,14


sync:
	aws s3 sync \
		/home/olga/data/kmer-hashing/brawand2011 \
		s3://kmer-hashing/brawand2011/
