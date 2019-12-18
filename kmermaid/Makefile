lrrr:
	nextflow run \
                nf-core/kmermaid \
                -r 818a148 \
		-profile czbiohub_local,docker \
		--fastas ~/data_lg/czbiohub-reference/ensembl/release-97/fasta/**cdna.all.fa.gz \
		--custom_config_base ~/code/nf-core/configs \
		--molecules dna,protein,dayhoff \
		--peptide_fasta ~/data_lg/czbiohub-reference/ensembl/release-97/fasta/homo_sapiens/pep/Homo_sapiens.GRCh38.pep.all.fa.gz \
		--ksizes 21 \
		--log2_sketch_sizes 5 \
		--extract_coding_peptide_ksize 7 \
		--extract_coding_peptide_molecule protein \
		--outdir ~/data_sm/kmer-hashing/kmermaid-extract-coding-ensembl97/ \
		--extract_coding_jaccard_threshold 0.5 \
		-work-dir ~/data_sm/olga-lrrr/nextflow-intermediates-nosudo/ \
		--max_cpus 120 \
		--max_time 720.h \
		-resume
