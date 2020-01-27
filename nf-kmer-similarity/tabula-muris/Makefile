run_aws:
	nextflow run czbiohub/nf-kmer-similarity -latest -profile aws \
		--work-dir s3://kmer-hashing/nextflow-intermediates/ \
		--samples samples.csv \
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

samples.csv:
	aws s3 cp s3://czb-maca/Plate_seq/3_month/fastqs.csv - | sed  '0,/R1/ s//read1/' | sed '0,/R2/ s//read2/' > samples.csv
	aws s3 cp samples.csv s3://czb-maca/Plate_seq/3_month/fastqs_read1_read2.csv
