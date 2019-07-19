aws:
	nextflow run czbiohub/nf-kmer-similarity -latest \
		-r olgabot/fix-fasta \
		--fastas s3://czbiohub-reference/gencode/mouse/vM19/gencode.vM19.pc_transcripts.fa.gz,s3://czbiohub-reference/gencode/human/v29/gencode.v29.pc_transcripts.fa.gz \
		--one_signature_per_record \
		--outdir s3://kmer-hashing/hg38_mm38_protein_coding/ \
		-work-dir s3://kmer-hashing/nextflow-intermediates/ \
		-profile czbiohub_aws
