concat:
	nextflow run czbiohub/fastqcat \
	 	-profile czbiohub_aws \
		--custom_config_base https://raw.githubusercontent.com/czbiohub/configs/olgabot/czb-update  \
		--reads 's3://aaron-data/Botryllus/**.fastq.gz' \
		-resume --outdir s3://kmer-hashing/rawdata/botryllus/


rnaseq:
	nextflow run nf-core/rnaseq \
        -r 1.4.2 \
        -latest \
        --reads `/mnt/data_lg/lekha/kmer-hashing/rawdata/botryllus/concatenated/*{R1,R2}.fastq.gz` \
        -profile docker  \
        --saveReference \
        --saveTrimmed \
        --saveAlignedIntermediates \
        --outdir /mnt/data_lg/lekha/kmer-hashing/botryllus_mouse/nfcore-rnaseq/ \
        -resume \
        -with-tower \
        -work-dir /home/lekha/data_lg/nextflow-intermediates/ \
        --pseudo_aligner salmon \
        --gtf /mnt/data_lg/lekha/kmer-hashing/botryllus_mouse/gff/botznik-chr-all__fix_transcript_attributes_add_semicolon_and_equals.gtf \
        --fasta /mnt/data_lg/lekha/kmer-hashing/botryllus_mouse/fasta/botznik-chr.fa \
                --fc_group_features ID \
                --fc_extra_attributes Name \
                --fc_group_features_type transcript_support \
kmer_aws:
	nextflow run czbiohub/nf-kmer-similarity \
		-r olgabot/dayhoff \
		--read_pairs 's3://kmer-hashing/botryllus/nfcore-rnaseq/trim_galore/*{R1,R2}*.fq.gz' \
		--outdir 's3://kmer-hashing/botryllus/nf-kmer-similarity/' \
		--custom_config_base $$HOME/code/nf-core/configs \
		-profile czbiohub_aws_highpriority \
		--tracedir ./kmer_trace \
		--max_memory 64.GB \
		-resume

kmer_subset:
	nextflow run czbiohub/nf-kmer-similarity \
		-latest -resume \
		-r olgabot/dayhoff \
		--read_pairs 's3://kmer-hashing/botryllus/nfcore-rnaseq/trim_galore/CellPopulation3*{R1,R2}*.fq.gz' \
		--outdir 's3://kmer-hashing/botryllus/nf-kmer-similarity/' \
		--custom_config_base $$HOME/code/nf-core/configs \
		-profile czbiohub_aws
