aws:
	nextflow run czbiohub/nf-kmer-similarity -latest \
		-r olgabot/fix-fasta \
		--fastas s3://czbiohub-reference/gencode/mouse/vM19/gencode.vM19.pc_transcripts.fa.gz,s3://czbiohub-reference/gencode/human/v29/gencode.v29.pc_transcripts.fa.gz \
		--one_signature_per_record \
		--input_is_protein \
		--molecules dayhoff,protein \
		--log2_sketch_sizes 4,5,6,7 \
		--outdir s3://kmer-hashing/hg38_mm38_protein_coding/ \
		-work-dir s3://kmer-hashing/nextflow-intermediates/ \
		-profile czbiohub_aws
