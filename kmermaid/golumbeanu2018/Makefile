BASE=/mnt/data_lg/olga/kmer-hashing/golumbeanu2018
PEPTIDE_DIR=${BASE}/rawdata/peptide-fastas
NO_K2G_FASTA=${PEPTIDE_DIR}/KS_UniProt_HumanProteomeSPonly_HIV_KtoG_appended_KS20200323correct__no_K2G.fasta
K2G_FASTA=${PEPTIDE_DIR}/KS_UniProt_HumanProteomeSPonly_HIV_KtoG_appended_KS20200323correct__bottom197lines.fasta
DATA_DIR=${BASE}/rawdata/fastqs
OUTDIR_BASE=${BASE}/kmermaid
FASTA_DIR=${BASE}rawdata
WORK_DIR=/home/olga/data_sm/nextflow-intermediates-lrrr

COMMON_FLAGS=nf-core/kmermaid \
		-r olgabot/fastp \
		-latest \
		-profile docker,czbiohub_local \
		--molecules dna,protein,dayhoff,hp \
		--ksizes '21,27,33,39,51,63,93' \
		--log2_sketch_sizes 14 \
		--read_singles ${DATA_DIR}/'*.fastq.gz' \
		-work-dir ${WORK_DIR} \
		--extract_coding_peptide_ksize 15 \
		-resume \
		-with-tower \
		--track_abundance \
		--custom_config_base ${HOME}/code/nf-core/configs 


no_k2g_uniprot:
	nextflow run \
		${COMMON_FLAGS} \
		--outdir ${OUTDIR_BASE}/$@ \
		--peptide_fasta ${NO_K2G_FASTA}



with_k2g_uniprot:
	nextflow run \
		${COMMON_FLAGS} \
		--outdir ${OUTDIR_BASE}/$@ \
		--peptide_fasta ${K2G_FASTA}


