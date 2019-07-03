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
            --reads "s3://kmer-hashing/rawdata/botryllus/concatenated/*{R1,R2}*.fastq.gz" \
            -profile czbiohub_aws \
            --saveReference \
            --saveTrimmed \
            --saveAlignedIntermediates \
            --outdir "s3://kmer-hashing/botryllus/nfcore-rnaseq/" \
            -resume \
            -work-dir "s3://kmer-hashing/nextflow-intermediates/" \
            --custom_config_base https://raw.githubusercontent.com/czbiohub/configs/olgabot/czb-update \
            --pseudo_aligner salmon \
            -process.errorStrategy=ignore \
            --seqCenter czbiohub \
            --transcript_fasta s3://czbiohub-reference/botryllus/2019-06-28/botznik-transcripts.fa \
            --fasta s3://czbiohub-reference/botryllus/2019-06-28/botznik-chr.fa \
            --gff s3://czbiohub-reference/botryllus/2019-06-28/botznik-chr-all.gff \
						--fc_group_features ID \
						--fc_extra_attributes Name \
						--fc_group_features_type transcript_support

kmer_aws:
	nextflow run czbiohub/nf-kmer-similarity \
		-r olgabot/dayhoff \
		--read_pairs 's3://kmer-hashing/botryllus/nfcore-rnaseq/trim_galore/*{R1,R2}*.fq.gz' \
		--outdir 's3://kmer-hashing/botryllus/nf-kmer-similarity/' \
		--custom_config_base https://raw.githubusercontent.com/czbiohub/configs/olgabot/czb-update \
		-profile aws

kmer_subset:
	nextflow run czbiohub/nf-kmer-similarity \
		-r olgabot/dayhoff \
		--read_pairs 's3://kmer-hashing/botryllus/nfcore-rnaseq/trim_galore/CellPopulation*{R1,R2}*.fq.gz' \
		--outdir 's3://kmer-hashing/botryllus/nf-kmer-similarity/' \
		--custom_config_base https://raw.githubusercontent.com/czbiohub/configs/olgabot/czb-update \
		-profile aws
