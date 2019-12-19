REPO=~/code/nf-core/extractcoding--olgabot/khtools-extract-coding-long-reads

lrrr:
	nextflow run \
		${REPO} \
		-profile czbiohub_local,docker \
		--reads '/home/olga/data_lg/czbiohub-reference/ensembl/release-97/fasta/**cdna.all.fa.gz' \
		--custom_config_base ~/code/nf-core/configs \
		--peptide_fasta ~/data_lg/czbiohub-reference/ensembl/release-97/fasta/homo_sapiens/pep/Homo_sapiens.GRCh38.pep.all.fa.gz \
		-work-dir ~/data_sm/olga-lrrr/nextflow-intermediates-nosudo/ \
		-resume \
		--singleEnd \
		-with-tower
