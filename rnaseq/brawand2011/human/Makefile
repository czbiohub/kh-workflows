
SPECIES=hsa
GENOME=GRCh38

# Olga's sane naming
SPECIES_OLGA=human

# Parent directory of all outputs
OUTDIR_BASE=/home/olga/ibm_lg/kmer-hashing/brawand2011/nfcore-rnaseq

all: paired_end single_end

paired_end:
	nextflow run nf-core/rnaseq \
		-r dev \
		-resume \
		--reads ${HOME}'/ibm_lg/sra-explorer/brawand2011/paired_end/*'${SPECIES}'*{1,2}.fastq.gz' \
		-profile docker,czbiohub_local \
		--saveTrimmed \
		--outdir ${OUTDIR_BASE}/${SPECIES_OLGA}/$@ \
		-work-dir ${HOME}"/ibm_lg/kmer-hashing/nextflow-intermediates/" \
		--custom_config_base ${HOME}"/code/nf-core/configs" \
		--pseudo_aligner salmon \
		--genome GRCh38 \
		--email olga.botvinnik@czbiohub.org

single_end:
	nextflow run nf-core/rnaseq \
		-r dev \
		-resume \
		--reads ${HOME}'/ibm_lg/sra-explorer/brawand2011/single_end/*'${SPECIES}'*.fastq.gz' \
		-profile docker,czbiohub_local \
		--saveTrimmed \
		--outdir ${OUTDIR_BASE}/${SPECIES_OLGA}/$@ \
		-work-dir ${HOME}"/ibm_lg/kmer-hashing/nextflow-intermediates/" \
		--custom_config_base ${HOME}"/code/nf-core/configs" \
		--pseudo_aligner salmon \
		--genome GRCh38 \
		--email olga.botvinnik@czbiohub.org \
		--singleEnd
