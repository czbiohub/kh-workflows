OUTDIR_BASE=~/data_lg/kmer-hashing//brawand2011/kmermaid
PAIRED=/mnt/ibm_lg/olga/kmer-hashing//brawand2011/rnaseq/paired/allspecies/trim_galore
SINGLE=/mnt/ibm_lg/olga/kmer-hashing//brawand2011/rnaseq/paired/allspecies/trim_galore
PEPTIDES=~/data_lg/czbiohub-reference/ensembl/release-97/fasta/homo_sapiens/pep/Homo_sapiens.GRCh38.pep.all.fa.gz

run:
	nextflow run \
		nf-core/kmermaid \
		-r olgabot/khtools-extract-coding \
		-latest \
		-profile czbiohub_local,docker \
		--read_singles ${SINGLE}/'*R1_trimmed.fq.gz' \
		--read_pairs ${PAIRED}/'*{R1,R2}_val*.fq.gz' \
		--custom_config_base ~/code/nf-core/configs \
		--molecules dna,protein,dayhoff \
		--peptide_fasta ${PEPTIDES} \
		--ksizes 21 \
		--log2_sketch_sizes 14 \
		--outdir /home/olga/data_lg/kmer-hashing/brawand2011/kmermaid/results_peptide7/ \
		-work-dir ~/pureScratch/nextflow-intermediates-nosudo/ \
		-with-tower \
		-resume

run_more_ksizes:
	PEPTIDE_KSIZE=12
	nextflow run \
		nf-core/kmermaid \
		-r olgabot/khtools-extract-coding \
		-latest \
		-profile czbiohub_local,docker \
		--read_singles ${SINGLE}/'*.fastq.gz' \
		--read_pairs ${PAIRED}/'*{R1,R2}.fastq.gz' \
		--custom_config_base ~/code/nf-core/configs \
		--molecules dna,protein,dayhoff \
		--peptide_fasta ${PEPTIDES} \
		--ksizes 27,33 \
		--log2_sketch_sizes 12,14 \
		--bloomfilter_tablesize '1e8' \
		--extract_coding_peptide_ksize 11 \
		--extract_coding_peptide_molecule dayhoff \
		--outdir /home/olga/data_lg/kmer-hashing/brawand2011/kmermaid/results_dayhoff11_extract_coding_jaccard_threshold05_more_ksizes \
		--extract_coding_jaccard_threshold 0.5 \
		-work-dir ~/pureScratch/nextflow-intermediates2/ \
		-resume


dayhoff12:
	PEPTIDE_KSIZE=12
	nextflow run \
		nf-core/kmermaid \
		-r olgabot/khtools-extract-coding \
		-latest \
		-profile czbiohub_local,docker \
		--read_singles ${SINGLE}/'*.fastq.gz' \
		--read_pairs ${PAIRED}/'*{R1,R2}.fastq.gz' \
		--custom_config_base ~/code/nf-core/configs \
		--molecules dna,protein,dayhoff \
		--peptide_fasta ${PEPTIDES} \
		--ksizes 21,27,33 \
		--log2_sketch_sizes 12,14 \
		--bloomfilter_tablesize '1e8' \
		--extract_coding_peptide_ksize 12 \
		--extract_coding_peptide_molecule dayhoff \
		--outdir ${OUTDIR_BASE}/results_dayhoff${PEPTIDE_KSIZE}_extract_coding_jaccard_threshold05 \
		--extract_coding_jaccard_threshold 0.5 \
		-work-dir ~/pureScratch/nextflow-intermediates-nosudo/ \
		-resume


# --- No read pairs for now --- #
singles:
	nextflow run \
		/home/olga/code/nf-core/kmermaid--olgabot-khtools-extract-coding/ \
		-r olgabot/khtools-extract-coding \
		-latest \
		-profile czbiohub_local,docker \
		--read_singles ${SINGLE}/'*.fastq.gz' \
		--read_pairs ${PAIRED}/'*{R1,R2}.fastq.gz' \
		--custom_config_base ~/code/nf-core/configs \
		--molecules dna,protein,dayhoff \
		--peptide_fasta ${PEPTIDES} \
		--ksizes 21 \
		--log2_sketch_sizes 10,12,14,16 \
		--bloomfilter_tablesize '1e8' \
		--extract_coding_peptide_ksize 11 \
		--extract_coding_peptide_molecule dayhoff \
		--outdir /home/olga/data_lg/kmer-hashing/brawand2011/kmermaid/results_dayhoff11_extract_coding_jaccard_threshold05 \
		--extract_coding_jaccard_threshold 0.5 \
		-resume
