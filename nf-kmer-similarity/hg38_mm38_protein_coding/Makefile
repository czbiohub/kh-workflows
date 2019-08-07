GENCODE=/home/olga/data_lg/czbiohub-reference/gencode

local:
	nextflow run ${HOME}/code/nf-core/kmermaid/main.nf \
		--fastas '${GENCODE}/mouse/vM21/gencode.vM21.pc_translations.fa.gz;${GENCODE}/human/v30/gencode.v30.pc_translations.fa.gz' \
		--one_signature_per_record \
		--input_is_protein \
		--molecules dayhoff,protein \
		--log2_sketch_sizes 4,5,6,7 \
		--outdir ${HOME}/pureScratch/kmer-hashing/hg38_mm38_protein_coding/ \
		-w ${HOME}/pureScratch/kmer-hashing/nextflow-intermediates/ \
		-profile czbiohub_local \
		--custom_config_base ~/code/nf-core/configs \
		-resume

aws:
	nextflow run czbiohub/nf-kmer-similarity -latest \
		-r olgabot/fix-fasta \
		--fastas '${GENCODE}/mouse/vM21/gencode.vM21.pc_translations.fa.gz;${GENCODE}/human/v30/gencode.vM21.pc_translations.fa.gz' \
		--one_signature_per_record \
		--input_is_protein \
		--molecules dayhoff,protein \
		--log2_sketch_sizes 4,5,6,7 \
		--outdir s3://kmer-hashing/hg38_mm38_protein_coding/ \
		-work-dir s3://kmer-hashing/nextflow-intermediates/ \
		-profile czbiohub_aws \
		-resume
