

BRAWAND2011=/home/olga/ibm_lg/kmer-hashing/brawand2011

local:
	nextflow run nf-core/kmermaid \
		--read_pairs ${BRAWAND2011}/nfcore-rnaseq-single-end/allspecies/trim_galore \
		--read_singles ${BRAWAND2011}/nfcore-rnaseq-paired-end/allspecies/trim_galore \
		-profile czbiohub_local \
		--log2_sketch_sizes 10 \
		--ksizes 21,27,33,51 \
		--molecules DNA,protein,dayhoff \
		--custom_config_base ${HOME}/code/nf-core/configs/ \
		-resume --max-time 8h
