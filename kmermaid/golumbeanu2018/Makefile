BASE=/mnt/ibm_lg/olga/kmer-hashing/golumbeanu2018
PEPTIDE_DIR=/home/pranathi/code/k2g/
NO_K2G_FASTA=${PEPTIDE_DIR}/KS_UniProt_HumanProteomeSPonly_HIV_KtoG_appended_KS20200323correct__non-k2g.fasta
K2G_FASTA=${PEPTIDE_DIR}/KS_UniProt_HumanProteomeSPonly_HIV_KtoG_appended_KS20200323correct__k2g.fasta
DATA_DIR=${BASE}/rawdata/fastqs
OUTDIR_BASE=mnt/ibm_lg/pranathi/nextflow-out-lrrr-k2g
WORK_DIR=/mnt/ibm_lg/pranathi/nextflow-work-lrrr-k2g

COMMON_FLAGS=nf-core/kmermaid \
		-r pranathi-multiprocessing-translate \
		-latest \
		-profile docker \
		--molecules dna,protein,dayhoff,hp \
		--ksizes '21,27,33,39,51,63,93' \
		--sketch_num_hashes_log2 14 \
		--read_singles ${DATA_DIR}/'*.fastq.gz' \
		-work-dir ${WORK_DIR} \
		--translate_peptide_ksize 15 \
		-resume \
		-with-tower \
		--track_abundance \


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


