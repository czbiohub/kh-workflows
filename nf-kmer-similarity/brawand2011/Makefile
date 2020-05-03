

RAWDATA=/mnt/ibm_lg/olga/kmer-hashing/brawand2011/rawdata
PAIRED=${RAWDATA}/paired_end
SINGLE=${RAWDATA}/single_end

BRAWAND2011=/home/olga/ibm_lg/kmer-hashing/brawand2011

local:
	nextflow run nf-core/kmermaid \
		-r dev \
		-latest \
		--read_pairs ${BRAWAND2011}/nfcore-rnaseq-paired-end/allspecies/trim_galore/'*{1_val_1,2_val_2}.fq.gz' \
		--read_singles ${BRAWAND2011}/nfcore-rnaseq-single-end/allspecies/trim_galore/'*_trimmed.fq.gz' \
		-profile czbiohub_local \
		--log2_sketch_sizes 12 \
		--ksizes 21,27,33,51 \
		--molecules dna,protein,dayhoff \
		--custom_config_base ${HOME}/code/nf-core/configs/ \
		--outdir ${BRAWAND2011}/kmermaid/ \
		-resume --max-time 8h \
		--max_cpus 32


local_newksizes:
	nextflow run nf-core/kmermaid \
		-r olgabot/increase-max-time \
		-latest \
		--read_pairs ${BRAWAND2011}/nfcore-rnaseq-paired-end/allspecies/trim_galore/'*{1_val_1,2_val_2}.fq.gz' \
		--read_singles ${BRAWAND2011}/nfcore-rnaseq-single-end/allspecies/trim_galore/'*_trimmed.fq.gz' \
		-profile czbiohub_local \
		--log2_sketch_sizes 12 \
		--ksizes 15,18,24,30,36,39,42,45,48,54,57,60,63,66,69,72,75 \
		--molecules dna,protein,dayhoff \
		--custom_config_base ${HOME}/code/nf-core/configs/ \
		--outdir ${BRAWAND2011}/kmermaid/ \
		-resume --max-time 8h

UNIPROT_OPISTHOKONTA=/home/olga/data_lg/czbiohub-reference/uniprot/releases/2019_11/manually_downloaded/uniprot-reviewed_yes+taxonomy_2759.fasta.gz
UNIPROT_UNIREF=/home/olga/data_lg/czbiohub-reference/uniprot/releases/2019_11/uniref/uniref100/uniref100.fasta.gz

KMERMAID_FLAGS=		nf-core/kmermaid \
		-r dev \
		-latest \
		--read_pairs ${PAIRED}/'*{R1,R2}.fastq.gz' \
		--read_singles ${SINGLE}/'*.fastq.gz' \
		-profile czbiohub_local \
                --log2_sketch_sizes 14 \
		--ksizes 21,24,27,30,33,36,39,42,45,48,51,54,57,60,63 \
		--molecules dna,protein,dayhoff \
		--extract_coding_peptide_ksize 9 \
		--extract_coding_jaccard_threshold 0.95 \
		--custom_config_base ${HOME}/code/nf-core/configs/ \
		-resume \
		--max-time 96h \
		--max_cpus 64 \
		-with-tower


uniprot_opisthokonta:
	nextflow run \
		${KMERMAID_FLAGS} \
		--peptide_fasta ${UNIPROT_OPISTHOKONTA} \
		--outdir ${BRAWAND2011}/kmermaid_$@/ \

uniprot_uniref:
	nextflow run \
		${KMERMAID_FLAGS} \
		--peptide_fasta ${UNIPROT_UNIREF} \
		--outdir ${BRAWAND2011}/kmermaid_$@/


existing_peptides_uniprot_opisthokonta:
	nextflow run \
		nf-core/kmermaid \
		-r olgabot/input-protein-fastas \
		-latest \
		--protein_fastas ${BRAWAND2011}/kmermaid_uniprot_opisthokonta/extract_coding/'*__coding_reads_peptides.fasta' \
		-profile czbiohub_local \
                --log2_sketch_sizes 14 \
		--ksizes 21,24,27,30,33,36,39,42,45,48,51,54,57,60,63 \
		--molecules protein,dayhoff \
		--custom_config_base ${HOME}/code/nf-core/configs/ \
		-resume \
		--max-time 96h \
		--max_cpus 64 \
		-with-tower \
		--track_abundance \
		--outdir ${BRAWAND2011}/kmermaid_$@/

