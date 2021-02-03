REFERENCE_PROTEIN_FASTA=/home/olga/data_lg/czbiohub-reference/ncbi/refseq/releases/refseq-release98-2020-02-06/vertebrate_mammalian/vertebrate_mammalian_concatenated__np_only.faa.gz


OUTDIR_BASE=${HOME}/data_lg/kmer-hashing/brawand2011/predictorthologs
WORKFLOW=czbiohub/nf-predictorthologs -r olgabot/filter-bam-with-hashes -latest
COMMON_FLAGS=${WORKFLOW} \
                -work-dir ${HOME}/data_sm/nextflow-intermediates-lrrr/ \
                -profile docker \
                --proteome_search_fasta ${REFERENCE_PROTEIN_FASTA} \
                --protein_searcher "sourmash" \
		--sourmash_ksize 27 \
		--sourmash_molecule 'dayhoff' \
		-resume \
                --diff_hash_expression \
		--diff_hash_penalty 'l2' \
		--diff_hash_inverse_regularization_strength 1 \
		-with-tower \
		--csv molecule-dayhoff_ksize-27_log2sketchsize-14.csv \
		--input_is_protein \
		--filter_bam_hashes \

run:
	nextflow run \
		${COMMON_FLAGS} \
		--outdir ${OUTDIR_BASE}/$@/ \
		-dump-channels ch_read_ids_mapped,ch_hash_seqs_and_their_aligned_read_ids,ch_group_to_hashes_for_joining__ch_protein_seq_from_hash2kmer




