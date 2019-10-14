

BRAWAND2011=/home/olga/ibm_lg/kmer-hashing/brawand2011

local:
	nextflow run nf-core/kmermaid \
		-r dev \
		-latest \
		--read_pairs ${BRAWAND2011}/nfcore-rnaseq-paired-end/allspecies/trim_galore/'*{1_val_1,2_val_2}.fq.gz' \
		--read_singles ${BRAWAND2011}/nfcore-rnaseq-single-end/allspecies/trim_galore/'*_trimmed.fq.gz' \
		-profile czbiohub_local \
		--log2_sketch_sizes 12 \
		--ksizes 21,27,33,51 \
		--molecules dna,protein,dayhoff \
		--custom_config_base ${HOME}/code/nf-core/configs/ \
		--outdir ${BRAWAND2011}/kmermaid/ \
		-resume --max-time 8h \
		--max_cpus 32


local_newksizes:
	nextflow run nf-core/kmermaid \
		-r olgabot/increase-max-time \
		-latest \
		--read_pairs ${BRAWAND2011}/nfcore-rnaseq-paired-end/allspecies/trim_galore/'*{1_val_1,2_val_2}.fq.gz' \
		--read_singles ${BRAWAND2011}/nfcore-rnaseq-single-end/allspecies/trim_galore/'*_trimmed.fq.gz' \
		-profile czbiohub_local \
		--log2_sketch_sizes 12 \
		--ksizes 15,18,24,30,36,39,42,45,48,54,57,60,63,66,69,72,75 \
		--molecules dna,protein,dayhoff \
		--custom_config_base ${HOME}/code/nf-core/configs/ \
		--outdir ${BRAWAND2011}/kmermaid/ \
		-resume --max-time 8h
