# brawand2011 naming
SPECIES=mmu

# Olga's naming
SPECIES_OLGA=mouse

PPC_RAWDATA=/data_lg/olga/kmer-hashing/brawand2011/rawdata
PPC_PAIRED=${PPC_RAWDATA}/paired_end
PPC_SINGLE=${PPC_RAWDATA}/single_end

PPC_OUTDIR_BASE=/data_lg/lekha/kmer-hashing/brawand2011/nfcore-rnaseq

PPC_COMMON_FLAGS=-r 1.4 \
                -resume \
                -profile docker,czbiohub_lsf \
                --saveTrimmed \
                --saveAlignedIntermediates \
                --saveUnaligned \
                -work-dir /data_lg/nextflow-intermediates/ \
                --custom_config_base /data_sm/home/olga_ibm/code/nf-core/configs \
                --pseudo_aligner salmon \
                --compressedReference \
                --fasta /data_sm/home/olga_ibm/data_lg/czbiohub-reference/gencode/mouse/vM21/GRCm38.p6.genome.fa \
                --gtf /data_sm/home/olga_ibm/data_lg/czbiohub-reference/gencode/mouse/vM21/gencode.vM21.annotation.gtf \
                --email olga.botvinnik@czbiohub.org \
                --fc_group_features_type gene_biotype \
                --fc_extra_attributes gene_id \
                -with-tower

PPC_all: PPC_single_end

# No paired end data for mouse (only did primate brains with paired-end)
PPC_paired_end:
	/apps/Nextflow/bin/nextflow-20.02.0-edge.5276 run nf-core/rnaseq \
                --reads ${PPC_PAIRED}'/*'${SPECIES}'*{1,2}.fastq.gz' \
                --outdir ${PPC_OUTDIR_BASE}/${SPECIES_OLGA}/$@ \
                ${PPC_COMMON_FLAGS}

PPC_single_end:
	/apps/Nextflow/bin/nextflow-20.02.0-edge.5276 run nf-core/rnaseq \
                --reads ${PPC_SINGLE}'/*'${SPECIES}'*.fastq.gz' \
                --outdir ${PPC_OUTDIR_BASE}/${SPECIES_OLGA}/$@ \
                --singleEnd \
                ${PPC_COMMON_FLAGS}

RAWDATA=/mnt/data_lg/olga/kmer-hashing/brawand2011/rawdata
PAIRED=${RAWDATA}/paired_end
SINGLE=${RAWDATA}/single_end

# Parent directory of all outputs
OUTDIR_BASE=/mnt/data_lg/lekha/kmer-hashing/brawand2011/nfcore-rnaseq


COMMON_FLAGS=-r 1.4 \
                -resume \
                -profile docker,czbiohub_local \
                --saveTrimmed \
                --saveAlignedIntermediates \
                --saveUnaligned \
                -work-dir /home/lekha/data_lg/nextflow-intermediates/ \
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

# No paired end data for mouse (only did primate brains with paired-end)
#paired_end:
#       nextflow run nf-core/rnaseq \
#               --reads '/home/olga/ibm_lg/sra-explorer/brawand2011/paired_end/*'${SPECIES}'*{1,2}.fastq.gz' \
#               --outdir ${OUTDIR_BASE}/${SPECIES_OLGA}/$@ \
#               ${COMMON_FLAGS}

single_end:
	nextflow run nf-core/rnaseq \
                --reads ${SINGLE}'/*'${SPECIES}'*.fastq.gz' \
                --outdir ${OUTDIR_BASE}/${SPECIES_OLGA}/$@ \
                --singleEnd \ 
		${COMMON_FLAGS}

