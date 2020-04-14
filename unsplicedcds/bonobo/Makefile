SPECIES=hsa
GENOME=Ensembl-97

# Olga's sane naming
SPECIES_OLGA=bonobo
BASE_DIR=/mnt/data_lg/lekha/kmer-hashing/brawand2011/nfcore-rnaseq/${SPECIES_OLGA}
GTF=/home/olga/data_lg/czbiohub-reference/ensembl/release-97/gtf/pan_paniscus/Pan_paniscus.panpan1.1.97.gtf.gz

run:
        nextflow run czbiohub/nf-unsplicedcds \
                -r snafees/fix_gz_ch -latest \
                --bam ${BASE_DIR}/'*/STAR/*bam' \
                --gtf ${GTF} \
                -profile docker \
                -resume -with-tower \
                --email saba.nafees@czbiohub.org \
