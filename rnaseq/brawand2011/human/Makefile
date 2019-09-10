
SPECIES=hsa
GENOME=GRCh38

# Olga's sane naming
SPECIES_OLGA=human

# Parent directory of all outputs
OUTDIR_BASE=/home/olga/ibm_lg/kmer-hashing/brawand2011/nfcore-rnaseq

COMMON_FLAGS=-r olgabot/merged-gzip-gffread-transgenes \
                -latest \
                -resume \
                -profile docker,czbiohub_local \
								--saveAlignedIntermediates \
                --saveTrimmed \
                -work-dir ~/ibm_lg/kmer-hashing/nextflow-intermediates/ \
                --custom_config_base ~/code/nf-core/configs \
                --pseudo_aligner salmon \
                --email olga.botvinnik@czbiohub.org \
                --fc_extra_attributes gene_id \
								--genome GRCh38 \
								--gencode

all: paired_end single_end

paired_end:
	nextflow run nf-core/rnaseq \
		--reads ${HOME}'/ibm_lg/sra-explorer/brawand2011/paired_end/*'${SPECIES}'*{1,2}.fastq.gz' \
		--outdir ${OUTDIR_BASE}/${SPECIES_OLGA}/$@ \
		${COMMON_FLAGS}

single_end:
	nextflow run nf-core/rnaseq \
		--reads ${HOME}'/ibm_lg/sra-explorer/brawand2011/single_end/*'${SPECIES}'*.fastq.gz' \
		--outdir ${OUTDIR_BASE}/${SPECIES_OLGA}/$@ \
		${COMMON_FLAGS} \
		--singleEnd
