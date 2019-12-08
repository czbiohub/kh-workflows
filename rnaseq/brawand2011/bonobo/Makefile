# brawand2011 naming
SPECIES=ppa

# Olga's naming
SPECIES_OLGA=bonobo

OUTDIR_BASE=/home/olga/ibm_lg/kmer-hashing/brawand2011/nfcore-rnaseq

COMMON_FLAGS=-r 1.4 \
                -resume \
                -profile docker,czbiohub_local \
                --saveTrimmed \
		--saveAlignedIntermediates \
		--saveUnaligned \
                -work-dir /home/olga/ibm_lg/kmer-hashing/nextflow-intermediates/ \
                --custom_config_base /home/olga/code/nf-core/configs \
                --pseudo_aligner salmon \
                --compressedReference \
                --fasta /home/olga/data_lg/czbiohub-reference/ensembl/release-97/fasta/pan_paniscus/dna_index/Pan_paniscus.panpan1.1.dna.toplevel.fa.gz \
                --gtf /home/olga/data_lg/czbiohub-reference/ensembl/release-97/gtf/pan_paniscus/Pan_paniscus.panpan1.1.97.gtf.gz \
                --email olga.botvinnik@czbiohub.org \
                --fc_group_features_type gene_biotype \
                --fc_extra_attributes gene_id \


all: paired_end single_end

paired_end:
	nextflow run nf-core/rnaseq \
		--reads '/home/olga/ibm_lg/sra-explorer/brawand2011/paired_end/*'${SPECIES}'*{1,2}.fastq.gz' \
		--outdir ${OUTDIR_BASE}/${SPECIES_OLGA}/$@ \
		${COMMON_FLAGS}

single_end:
	nextflow run nf-core/rnaseq \
		--reads '/home/olga/ibm_lg/sra-explorer/brawand2011/single_end/*'${SPECIES}'*.fastq.gz' \
		--outdir ${OUTDIR_BASE}/${SPECIES_OLGA}/$@ \
		--singleEnd \
		${COMMON_FLAGS}
