concat:
	nextflow run czbiohub/fastqcat \
	 	-profile czbiohub_aws \
		--custom_config_base https://raw.githubusercontent.com/czbiohub/configs/olgabot/czb-update  \
		--reads 's3://aaron-data/Botryllus/**.fastq.gz' \
		-resume --outdir s3://kmer-hashing/rawdata/botryllus/


sync:
	aws s3 sync --exclude "*" --include "*.fastq.gz" \
		s3://darmanis-group/singlecell_lungadeno/non_immune/nonImmune_fastqs_9.27/  \
		/home/olga/ibm_lg/kmer-hashing/lung_adenocarcinoma/rawdata

rnaseq:
	nextflow run czbiohub/rnaseq \
		-r olgabot/merged-salmon \
		-latest \
		-resume \
		--reads "s3://darmanis-group/singlecell_lungadeno/non_immune/nonImmune_fastqs_9.27/**{R1,R2}*.fastq.gz" \
		-profile czbiohub_aws_highpriority \
		--saveReference \
		--saveTrimmed \
		--saveAlignedIntermediates \
		--outdir "s3://kmer-hashing/lung_adenocarcinoma/nfcore-rnaseq/" \
		-work-dir "s3://kmer-hashing/nextflow-intermediates/" \
		--pseudo_aligner salmon \
		--genome GRCh38 \
		--email olga.botvinnik@czbiohub.org \
		--skipQC

rnaseq_local:
	nextflow run czbiohub/rnaseq \
		-r olgabot/merged-salmon \
		-latest \
		-resume \
		--reads '/home/olga/ibm_lg/kmer-hashing/lung_adenocarcinoma/rawdata/**{R1,R2}*.fastq.gz' \
		-profile docker \
		--saveReference \
		--saveTrimmed \
		--saveAlignedIntermediates \
		--outdir "/home/olga/ibm_lg/kmer-hashing/lung_adenocarcinoma/nfcore-rnaseq/" \
		-work-dir "/home/olga/ibm_sm/nextflow-intermediates/" \
		--pseudo_aligner salmon \
		--genome GRCh38 \
		--email olga.botvinnik@czbiohub.org \
		--skipQC \
		--max_cpus 32 \
		--max_memory 256.GB

kmer_local:
	nextflow run czbiohub/nf-kmer-similarity \
		-r olgabot/dayhoff \
		-latest \
		--read_pairs '/home/olga/pureScratch/kmer-hashing/lung_adenocarcinoma/nfcore-rnaseq/trim_galore/*{R1,R2}*.fq.gz' \
		--outdir /home/olga/pureScratch/kmer-hashing/lung_adenocarcinoma/nf-kmer-similarity/ \
		--custom_config_base ${HOME}/code/nf-core/configs/ \
		-profile czbiohub_local \
		--tracedir ./kmer_local_trace \
		--log2_sketch_sizes 10,12 \
		--ksizes 21,27 \
		-resume



kmer_aws:
	aws s3 rm s3://kmer-hashing/lung_adenocarcinoma/nf-kmer-similarity/pipeline_info/ 
	nextflow run czbiohub/nf-kmer-similarity \
		-r olgabot/dayhoff \
		--read_pairs 's3://kmer-hashing/lung_adenocarcinoma/nfcore-rnaseq/trim_galore/*{R1,R2}*.fq.gz' \
		--outdir 's3://kmer-hashing/lung_adenocarcinoma/nf-kmer-similarity/' \
		--custom_config_base https://raw.githubusercontent.com/czbiohub/configs/olgabot/czb-update \
		-profile czbiohub_aws_highpriority \
		--tracedir ./kmer_aws_trace \
		--log2_sketch_sizes 10,12 \
		-resume

kmer_subset:
	nextflow run czbiohub/nf-kmer-similarity \
		-r olgabot/dayhoff \
		--read_pairs 's3://kmer-hashing/lung_adenocarcinoma/nfcore-rnaseq/trim_galore/A10*{R1,R2}*.fq.gz' \
		--outdir 's3://kmer-hashing/lung_adenocarcinoma/nf-kmer-similarity/' \
		-profile czbiohub_aws_highpriority \
		--tracedir ./kmer_aws_trace \
		--log2_sketch_sizes 10,12
#		--custom_config_base https://raw.githubusercontent.com/czbiohub/configs/olgabot/czb-update \

