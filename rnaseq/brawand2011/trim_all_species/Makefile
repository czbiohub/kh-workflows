

SPECIES=hsa
GENOME=GRCh38

paired_end:
	nextflow run nf-core/rnaseq \
		-r dev \
		-latest \
		-resume \
		--reads '/home/olga/ibm_lg/sra-explorer/brawand2011/paired_end/*{1,2}.fastq.gz' \
		-profile docker,czbiohub_local \
		--saveTrimmed \
		--outdir "/home/olga/ibm_lg/kmer-hashing/brawand2011/nfcore-rnaseq-paired-end/allspecies/" \
		-work-dir "/home/olga/ibm_lg/kmer-hashing/nextflow-intermediates/" \
		--custom_config_base "/home/olga/code/nf-core/configs" \
		--pseudo_aligner salmon \
		--genome GRCh38 \
		--email olga.botvinnik@czbiohub.org

single_end:
	nextflow run nf-core/rnaseq \
		-r dev \
		-latest \
		-resume \
		--reads '/home/olga/ibm_lg/sra-explorer/brawand2011/single_end/*.fastq.gz' \
		-profile docker,czbiohub_local \
		--saveTrimmed \
		--outdir "/home/olga/ibm_lg/kmer-hashing/brawand2011/nfcore-rnaseq-single-end/allspecies/" \
		-work-dir "/home/olga/ibm_lg/kmer-hashing/nextflow-intermediates/" \
		--custom_config_base "/home/olga/code/nf-core/configs" \
		--pseudo_aligner salmon \
		--genome GRCh38 \
		--email olga.botvinnik@czbiohub.org \
		--singleEnd
