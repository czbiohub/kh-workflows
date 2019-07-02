concat:
	nextflow run czbiohub/fastqcat \
	 	-profile czbiohub_aws \
		--custom_config_base https://raw.githubusercontent.com/czbiohub/configs/olgabot/czb-update  \
		--reads 's3://aaron-data/Botryllus/**.fastq.gz' \
		-resume --outdir s3://kmer-hashing/rawdata/botryllus/

aws:
	nextflow run czbiohub/nf-kmer-similarity \
		-r olgabot/dayhoff \
		--read_pairs 's3://kmer-hashing/botryllus/nfcore-rnaseq/trim_galore/*{R1,R2}*.fq.gz' \
		--outdir 's3://kmer-hashing/botryllus/nf-kmer-similarity/' \
		--custom_config_base https://raw.githubusercontent.com/czbiohub/configs/olgabot/czb-update \
		-profile aws

subset:
	nextflow run czbiohub/nf-kmer-similarity \
		-r olgabot/dayhoff \
		--read_pairs 's3://kmer-hashing/botryllus/nfcore-rnaseq/trim_galore/CellPopulation*{R1,R2}*.fq.gz' \
		--outdir 's3://kmer-hashing/botryllus/nf-kmer-similarity/' \
		--custom_config_base https://raw.githubusercontent.com/czbiohub/configs/olgabot/czb-update \
		-profile aws
