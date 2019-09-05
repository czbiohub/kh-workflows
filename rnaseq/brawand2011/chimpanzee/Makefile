# brawand2011 naming
SPECIES=ptr

# igenomes naming
GENOME=CHIMP2.1.4

# Olga's naming
SPECIES_OLGA=chimpanzee

OUTDIR_BASE=/home/olga/ibm_lg/kmer-hashing/brawand2011/nfcore-rnaseq

all: paired_end single_end

paired_end:
	nextflow run czbiohub/rnaseq \
		-r olgabot/merged-gzip-gffread-transgenes \
		-latest \
		-resume \
		--reads '/home/olga/ibm_lg/sra-explorer/brawand2011/paired_end/*'${SPECIES}'*{1,2}.fastq.gz' \
		-profile docker,czbiohub_local \
		--saveTrimmed \
		--outdir ${OUTDIR_BASE}/${SPECIES_OLGA}/$@ \
		-work-dir "/home/olga/ibm_lg/kmer-hashing/nextflow-intermediates/" \
		--custom_config_base "/home/olga/code/nf-core/configs" \
		--pseudo_aligner salmon \
		--compressedReference \
		--fasta ~/data_lg/czbiohub-reference/ncbi/genomes/refseq/vertebrate_mammalian/Pan_troglodytes/GCA_002880755.3/GCA_002880755.3_Clint_PTRv2_genomic.fna.gz \
		--gtf ~/data_lg/czbiohub-reference/ncbi/genomes/refseq/vertebrate_mammalian/Pan_troglodytes/GCA_002880755.3/GCA_002880755.3_Clint_PTRv2_genomic.gtf.gz \
		--email olga.botvinnik@czbiohub.org \
		--fc_group_features_type gene_biotype

single_end:
	nextflow run czbiohub/rnaseq \
		-r olgabot/merged-gzip-gffread-transgenes \
		-latest \
		-resume \
		--reads '/home/olga/ibm_lg/sra-explorer/brawand2011/single_end/*'${SPECIES}'*.fastq.gz' \
		-profile docker,czbiohub_local \
		--saveTrimmed \
		--outdir ${OUTDIR_BASE}/${SPECIES_OLGA}/$@ \
		-work-dir "/home/olga/ibm_sm/kmer-hashing/nextflow-intermediates/" \
		--custom_config_base "/home/olga/code/nf-core/configs" \
		--pseudo_aligner salmon \
		--genome ${GENOME} \
		--email olga.botvinnik@czbiohub.org \
		--gtf ${HOME}/ibm_lg/czbiohub-reference/igenomes/Pan_troglodytes/Ensembl/CHIMP2.1.4/Annotation/Genes/genes_in_genome.gtf \
		--singleEnd \
		--fc_group_features_type gene_biotype
