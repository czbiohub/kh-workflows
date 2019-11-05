


run:
	nextflow run \
		nf-core/kmermaid \
		-r olgabot/khtools-extract-coding \
		-latest \
		-profile czbiohub_local,docker \
		--read_singles '/home/olga/data_lg/kmer-hashing/brawand2011/nfcore-rnaseq-single-end/allspecies/trim_galore/*.fq.gz' \
		--read_pairs   '/home/olga/data_lg/kmer-hashing/brawand2011/nfcore-rnaseq-paired-end/allspecies/trim_galore/*{1_val_1,2_val_2}.fq.gz' \
		--custom_config_base ~/code/nf-core/configs \
		--molecules dna,protein,dayhoff \
		--peptide_fasta ~/data_lg/czbiohub-reference/ensembl/release-97/fasta/homo_sapiens/pep/Homo_sapiens.GRCh38.pep.all.fa.gz \
		--ksizes 21 \
		--log2_sketch_sizes 10,12,14,16 \
		--bloomfilter_tablesize '1e8' \
		--extract_coding_peptide_ksize 11 \
		--extract_coding_peptide_molecule dayhoff \
		--outdir /home/olga/data_lg/kmer-hashing/brawand2011/kmermaid/results_dayhoff11_extract_coding_jaccard_threshold05 \
		--extract_coding_jaccard_threshold 0.5 \
		-work-dir ~/pureScratch/nextflow-intermediates2/ \
		-resume

run_more_ksizes:
	nextflow run \
		nf-core/kmermaid \
		-r olgabot/khtools-extract-coding \
		-latest \
		-profile czbiohub_local,docker \
		--read_singles '/home/olga/data_lg/kmer-hashing/brawand2011/nfcore-rnaseq-single-end/allspecies/trim_galore/*.fq.gz' \
		--read_pairs   '/home/olga/data_lg/kmer-hashing/brawand2011/nfcore-rnaseq-paired-end/allspecies/trim_galore/*{1_val_1,2_val_2}.fq.gz' \
		--custom_config_base ~/code/nf-core/configs \
		--molecules dna,protein,dayhoff \
		--peptide_fasta ~/data_lg/czbiohub-reference/ensembl/release-97/fasta/homo_sapiens/pep/Homo_sapiens.GRCh38.pep.all.fa.gz \
		--ksizes 27,33 \
		--log2_sketch_sizes 12,14 \
		--bloomfilter_tablesize '1e8' \
		--extract_coding_peptide_ksize 11 \
		--extract_coding_peptide_molecule dayhoff \
		--outdir /home/olga/data_lg/kmer-hashing/brawand2011/kmermaid/results_dayhoff11_extract_coding_jaccard_threshold05 \
		--extract_coding_jaccard_threshold 0.5 \
		-work-dir ~/pureScratch/nextflow-intermediates2/ \
		-resume


# --- No read pairs for now --- #
singles:
	nextflow run \
		/home/olga/code/nf-core/kmermaid--olgabot-khtools-extract-coding/ \
		-r olgabot/khtools-extract-coding \
		-latest \
		-profile czbiohub_local,docker \
		--read_singles '/home/olga/data_lg/kmer-hashing/brawand2011/nfcore-rnaseq-single-end/allspecies/trim_galore/*.fq.gz' \
		--custom_config_base ~/code/nf-core/configs \
		--molecules dna,protein,dayhoff \
		--peptide_fasta ~/data_lg/czbiohub-reference/ensembl/release-97/fasta/homo_sapiens/pep/Homo_sapiens.GRCh38.pep.all.fa.gz \
		--ksizes 21 \
		--log2_sketch_sizes 10,12,14,16 \
		--bloomfilter_tablesize '1e8' \
		--extract_coding_peptide_ksize 11 \
		--extract_coding_peptide_molecule dayhoff \
		--outdir /home/olga/data_lg/kmer-hashing/brawand2011/kmermaid/results_dayhoff11_extract_coding_jaccard_threshold05 \
		--extract_coding_jaccard_threshold 0.5 \
		-resume