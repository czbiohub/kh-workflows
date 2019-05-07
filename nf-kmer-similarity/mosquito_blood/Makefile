OUT_DIR=/home/olga/data/kmer-hashing/multispecies/merkin2012/
S3_DIR=s3://kmer-hashing/multispecies/merkin2012/

all: local sync

local:
	nextflow run czbiohub/nf-kmer-similarity -latest \
		-r master \
		--read_pairs '/home/olga/data/sra-explorer/merkin2012/*{1,2}.fastq.gz' \
		--outdir ${OUT_DIR} \
	  -profile local

# After local is done ,run sync
sync: local
	aws s3 sync ${OUT_DIR} ${S3_DIR}
