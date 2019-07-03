concat:
	nextflow run czbiohub/fastqcat \
	 	-profile czbiohub_aws \
		--custom_config_base https://raw.githubusercontent.com/czbiohub/configs/olgabot/czb-update  \
		--reads 's3://aaron-data/Botryllus/**.fastq.gz' \
		-resume --outdir s3://kmer-hashing/rawdata/botryllus/


rnaseq:
	nextflow run czbiohub/rnaseq \
            -r olgabot/merged-salmon \
            -latest \
            --reads "s3://darmanis-group/singlecell_lungadeno/non_immune/nonImmune_fastqs_9.27/**{R1,R2}*.fastq.gz" \
            -profile czbiohub_aws \
            --saveReference \
            --saveTrimmed \
            --saveAlignedIntermediates \
            --outdir "s3://kmer-hashing/lung_adenocarcinoma/nfcore-rnaseq/" \
            -resume \
            -work-dir "s3://kmer-hashing/nextflow-intermediates/" \
            --custom_config_base https://raw.githubusercontent.com/czbiohub/configs/olgabot/czb-update \
            --pseudo_aligner salmon \
						--genome GRCh38

kmer_aws:
	nextflow run czbiohub/nf-kmer-similarity \
		-r olgabot/dayhoff \
		--read_pairs 's3://kmer-hashing/lung_adenocarcinoma/nfcore-rnaseq/trim_galore/*{R1,R2}*.fq.gz' \
		--outdir 's3://kmer-hashing/lung_adenocarcinoma/nf-kmer-similarity/' \
		--custom_config_base https://raw.githubusercontent.com/czbiohub/configs/olgabot/czb-update \
		-profile aws

kmer_subset:
	nextflow run czbiohub/nf-kmer-similarity \
		-r olgabot/dayhoff \
		--read_pairs 's3://kmer-hashing/lung_adenocarcinoma/nfcore-rnaseq/trim_galore/A10*{R1,R2}*.fq.gz' \
		--outdir 's3://kmer-hashing/lung_adenocarcinoma/nf-kmer-similarity/' \
		--custom_config_base https://raw.githubusercontent.com/czbiohub/configs/olgabot/czb-update \
		-profile aws
