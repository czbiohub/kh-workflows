# brawand2011 naming
SPECIES=mdo

# Olga's naming
SPECIES_OLGA=opossum

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
                --compressedReference \
                --fasta /home/olga/data_lg/czbiohub-reference/ensembl/release-97/fasta/monodelphis_domestica/dna_index/Monodelphis_domestica.monDom5.dna.toplevel.fa.gz \
                --gtf /home/olga/data_lg/czbiohub-reference/ensembl/release-97/gtf/monodelphis_domestica/Monodelphis_domestica.monDom5.97.gtf.gz \
                --email olga.botvinnik@czbiohub.org \
                --fc_group_features_type gene_biotype \
                --fc_extra_attributes gene_id \
                -with-tower

all: single_end

# No paired end data for opossum (only did primate brains with paired-end)
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
                ${COMMON_FLAGS
