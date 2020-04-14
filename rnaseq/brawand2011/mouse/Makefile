# brawand2011 naming
SPECIES=mmu

# Olga's naming
SPECIES_OLGA=mouse

OUTDIR_BASE=/home/olga/data_lg/kmer-hashing/brawand2011/nfcore-rnaseq

COMMON_FLAGS=-r 1.4 \
                -resume \
                -profile docker,czbiohub_local \
                --saveTrimmed \
		--saveAlignedIntermediates \
		--saveUnaligned \
                -work-dir /home/olga/ibm_lg/kmer-hashing/nextflow-intermediates/ \
                --custom_config_base /home/olga/code/nf-core/configs \
                --pseudo_aligner salmon \
                --fasta /home/olga/data_lg/czbiohub-reference/gencode/mouse/vM21/GRCm38.p6.genome.fa \
                --gtf /home/olga/data_lg/czbiohub-reference/gencode/mouse/vM21/gencode.vM21.annotation.gtf \
                --email olga.botvinnik@czbiohub.org \
		--gencode \
                --fc_group_features_type gene_type \
                --fc_extra_attributes gene_id \
		-with-tower

all: single_end

# No paired end data for opossum (only did primate brains with paired-end)
#paired_end:
#	nextflow run nf-core/rnaseq \
#		--reads '/home/olga/ibm_lg/sra-explorer/brawand2011/paired_end/*'${SPECIES}'*{1,2}.fastq.gz' \
#		--outdir ${OUTDIR_BASE}/${SPECIES_OLGA}/$@ \
#		${COMMON_FLAGS}

single_end:
	nextflow run nf-core/rnaseq \
		--reads '/home/olga/ibm_lg/sra-explorer/brawand2011/single_end/*'${SPECIES}'*.fastq.gz' \
		--outdir ${OUTDIR_BASE}/${SPECIES_OLGA}/$@ \
		--singleEnd \
		${COMMON_FLAGS}
