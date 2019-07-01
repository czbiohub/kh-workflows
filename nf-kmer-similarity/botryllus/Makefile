aws:
	nextflow run czbiohub/nf-kmer-similarity
    -r olgabot/dayhoff \
		--read_pairs 's3://kmer-hashing/botryllus/nfcore-rnaseq/trim_galore/*{1,2}.fastq.gz' \
		--outdir 's3://kmer-hashing/botryllus/nf-kmer-similarity/' \
		--custom_config_base https://raw.githubusercontent.com/czbiohub/configs/olgabot/czb-update \
		--profile czbiohub_aws
