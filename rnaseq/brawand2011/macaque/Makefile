# brawand2011 naming
SPECIES=mml

# Olga's naming
SPECIES_OLGA=macaque

RAWDATA=/ibm_lg/olga/kmer-hashing/brawand2011/rawdata
PAIRED=${RAWDATA}/paired_end
SINGLE=${RAWDATA}/single_end

OUTDIR_BASE=/data_lg/lekha/kmer-hashing/brawand2011/nfcore-rnaseq

COMMON_FLAGS=-r 1.4 \
                -resume \
                -profile docker,czbiohub_lsf \
                --saveTrimmed \
		--saveAlignedIntermediates \
		--saveUnaligned \
                -work-dir /home/lekha/data_lg/nextflow-intermediates/ \
                --custom_config_base data_sm/home/olga/code/nf-core/configs \
                --pseudo_aligner salmon \
                --compressedReference \
                --fasta data_sm/home/olga_ibm/data_lg/czbiohub-reference/ensembl/release-97/fasta/macaca_mulatta/dna_index/Macaca_mulatta.Mmul_8.0.1.dna.toplevel.fa.gz \
                --gtf data_sm/home/olga_ibm/data_lg/czbiohub-reference/ensembl/release-97/gtf/macaca_mulatta/Macaca_mulatta.Mmul_8.0.1.97.gtf.gz \
                --email olga.botvinnik@czbiohub.org \
                --fc_group_features_type gene_biotype \
                --fc_extra_attributes gene_id \
		-with-tower

all: paired_end single_end

paired_end:
	/apps/Nextflow/bin/nextflow-20.02.0-edge.5276 run nf-core/rnaseq \
		--reads ${PAIRED}'/*'${SPECIES}'*{1,2}.fastq.gz' \
		--outdir ${OUTDIR_BASE}/${SPECIES_OLGA}/$@ \
		${COMMON_FLAGS}

single_end:
	/apps/Nextflow/bin/nextflow-20.02.0-edge.5276 run nf-core/rnaseq \
		--reads ${SINGLE}'/*'${SPECIES}'*.fastq.gz' \
		--outdir ${OUTDIR_BASE}/${SPECIES_OLGA}/$@ \
		--singleEnd \
		${COMMON_FLAGS}
