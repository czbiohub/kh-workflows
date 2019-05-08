run_aws:
	nextflow run czbiohub/nf-kmer-similarity -latest -profile aws \
		--work-dir s3://kmer-hashing/nextflow-intermediates/ \
		--read_pairs 's3://czb-maca/Plate_seq/3_month/**{R1,R2}*.fastq.gz' \
		--outdir s3://kmer-hashing/tabula_muris/ \
		-r olgabot/index \
		--create_sbt_index --log2_sketch_sizes 12 \
		--molecules protein --ksizes 21 -resume \
		--no_compare


local:
	nextflow run czbiohub/nf-kmer-similarity -latest -profile local \
		--read_pairs 's3://czb-maca/Plate_seq/3_month/**{R1,R2}*.fastq.gz' \
		--outdir s3://kmer-hashing/tabula_muris/ \
		-r olgabot/index \
		--create_sbt_index --log2_sketch_sizes 12 \
		--molecules protein --ksizes 21 -resume \
		--no_compare
