run_aws:
	nextflow run czbiohub/nf-kmer-similarity -latest -profile aws \
		--read_pairs 's3://czb-maca/Plate_seq/3_month/**{R1,R2}*.fastq.gz' \
		--outdir s3://kmer-hashing/tabula_muris/ \
		-r olgabot/index \
		--index --log2_sketch_sizes 10,11,12,13 \
		--molecules protein --ksizes 21,27 -resume \
		--no_compare
