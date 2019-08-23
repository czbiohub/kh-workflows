

BRAWAND2011=/home/olga/ibm_lg/kmer-hashing/brawand2011

local:
	nextflow run nf-core/kmermaid \
		-latest \
		--read_pairs '/home/olga/ibm_lg/kmer-hashing/brawand2011/nfcore-rnaseq-paired-end/allspecies/trim_galore/*{val_1,val_2}.fq.gz' \
		--read_singles '/home/olga/ibm_lg/kmer-hashing/brawand2011/nfcore-rnaseq-single-end/allspecies/trim_galore/*_trimmed.fq.gz' \
		-profile czbiohub_local \
		--log2_sketch_sizes 12 \
		--ksizes 21,27,33,51 \
		--molecules DNA,protein,dayhoff \
		--custom_config_base ${HOME}/code/nf-core/configs/ \
		--outdir ${BRAWAND2011}/kmermaid/ \
		-resume --max-time 8h
