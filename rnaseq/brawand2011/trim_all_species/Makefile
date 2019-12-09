

OUTDIR_BASE=~/data_lg/kmer-hashing//brawand2011/rnaseq/
PAIRED=/mnt/ibm_lg/olga/kmer-hashing/brawand2011/rawdata/paired_end
SINGLE=/mnt/ibm_lg/olga/kmer-hashing/brawand2011/rawdata/single_end

SPECIES=hsa
GENOME=GRCh38

all: paired_end single_end

paired_end:
	nextflow run nf-core/rnaseq \
		-r 1.4.2 \
		-latest \
		-resume \
		-profile docker,czbiohub_local \
		--saveTrimmed \
		--reads ${PAIRED}/'*{R1,R2}.fastq.gz' \
		--outdir ${OUTDIR_BASE}/paired/allspecies \
		-work-dir "/home/olga/pureScratch//nextflow-intermediates-nosudo/" \
		--custom_config_base "/home/olga/code/nf-core/configs" \
		--pseudo_aligner salmon \
		--genome GRCh38 \
		--skipQC \
		--email olga.botvinnik@czbiohub.org

single_end:
	nextflow run nf-core/rnaseq \
		-r 1.4.2 \
		-latest \
		-resume \
		-profile docker,czbiohub_local \
		--saveTrimmed \
		--reads ${SINGLE}/'*R1.fastq.gz' \
		--outdir ${OUTDIR_BASE}/paired/allspecies \
		-work-dir "/home/olga/pureScratch//nextflow-intermediates-nosudo/" \
		--custom_config_base "/home/olga/code/nf-core/configs" \
		--pseudo_aligner salmon \
		--genome GRCh38 \
		--email olga.botvinnik@czbiohub.org \
		--skipQC \
		--singleEnd
