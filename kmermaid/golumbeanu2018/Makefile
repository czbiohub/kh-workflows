PEPTIDE_DIR=/home/pranathi/code/k2g/data/
NO_K2G_FASTA=${PEPTIDE_DIR}/KS_UniProt_HumanProteomeSPonly_HIV_KtoG_appended_KS20200323correct__non-k2g.fasta
K2G_FASTA=${PEPTIDE_DIR}/KS_UniProt_HumanProteomeSPonly_HIV_KtoG_appended_KS20200323correct__k2g.fasta
OUTDIR_BASE=${BASE}/kmermaid_k2g_lrrr_sep24/
FASTA_DIR=${BASE}rawdata
WORK_DIR=/mnt/ibm_lg/pranathi/nextflow-work-lrrr-k2g/
DATA_DIR=${BASE}/rawdata/fastqs

COMMON_FLAGS=main.nf \
                --molecules dna,protein,dayhoff,hp \
                --ksizes '21,27,33,39,51,63,93' \
                --sketch_scaled 10,50,100,500 \
                --read_singles ${DATA_DIR}/'*.fastq.gz' \
                -w ${WORK_DIR} \
                --save_intermediate_dir /mnt/ibm_lg/pranathi/k2g_intermediate/ \
                --translate_peptide_ksize 15 \
                --max_cpus 2 \
                -resume \
                --max_memory 8.GB \
                --max_time 96.h \
                --tenx_min_umi_per_cell 5001 \
                --track_abundance 


no_k2g_uniprot:
        /home/pranathi/nextflow run \
                ${COMMON_FLAGS} \
                --outdir ${OUTDIR_BASE}/$@ \
                --reference_proteome_fasta ${NO_K2G_FASTA}



with_k2g_uniprot:
        /home/pranathi/nextflow run \
                ${COMMON_FLAGS} \
                --outdir ${OUTDIR_BASE}/$@ \
                --reference_proteome_fasta ${K2G_FASTA}
