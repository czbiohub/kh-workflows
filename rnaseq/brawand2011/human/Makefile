
SPECIES=hsa
GENOME=GRCh38

paired_end:
	nextflow run czbiohub/rnaseq \
		-r olgabot/merged-salmon \
		-latest \
		-resume \
		--reads '/home/olga/ibm_lg/sra-explorer/brawand2011/paired_end/*'$$SPECIES'*{1,2}.fastq.gz' \
		-profile docker,czbiohub_local \
		--saveTrimmed \
		--outdir "/home/olga/ibm_lg/kmer-hashing/lung_adenocarcinoma/nfcore-rnaseq/" \
		-work-dir "/home/olga/ibm_lg/kmer-hashing/nextflow-intermediates/" \
		--custom_config_base "https://raw.githubusercontent.com/nf-core/configs/olgabot/czb-local"
		--pseudo_aligner salmon \
		--genome GRCh38 \
		--email olga.botvinnik@czbiohub.org

single_end:
	nextflow run czbiohub/rnaseq \
		-r olgabot/merged-salmon \
		-latest \
		-resume \
		--reads '/home/olga/ibm_lg/sra-explorer/brawand2011/single_end/*'hsa'*.fastq.gz' \
		-profile docker,czbiohub_local \
		--saveTrimmed \
		--outdir "/home/olga/ibm_lg/kmer-hashing/lung_adenocarcinoma/nfcore-rnaseq/" \
		-work-dir "/home/olga/ibm_lg/kmer-hashing/nextflow-intermediates/" \
		--custom_config_base "https://raw.githubusercontent.com/nf-core/configs/olgabot/czb-local"
		--pseudo_aligner salmon \
		--genome GRCh38 \
		--email olga.botvinnik@czbiohub.org \
		--singleEnd
