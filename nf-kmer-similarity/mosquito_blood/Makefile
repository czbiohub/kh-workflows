OUT_DIR=/mnt/data/kmer-hashing/
READS_DIR= s3://kmer-hashing/rawdata/mosquito_blood/sra/
IN_DIR= /mnt/data/fastq/
S3_DIR=


all: download aws

download:
	mkdir -p ${IN_DIR}
	aws s3 sync ${READS_DIR} ${IN_DIR}

aws:
	mkdir -p ${OUT_DIR}
	/mnt/data/nextflow run czbiohub/nf-kmer-similarity -latest \
		-r master \
		--read_pairs '/mnt/data/fastq/*{1,2}.fastq.gz' \
		--outdir ${OUT_DIR} \
	  -profile aws


sync: local
	aws s3 sync ${OUT_DIR} ${S3_DIR}
