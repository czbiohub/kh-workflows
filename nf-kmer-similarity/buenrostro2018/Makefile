run:
	nextflow run nf-core/kmermaid \
		--read_singles '/home/saba/fastqbams/*.fq' \
		--molecules dna \
		--ksizes 15,21,27,31 \
		--log2_sketch_sizes 10,12 \
		--outdir '/mnt/data_lg/saba/nextflow_kmermaid/' \
		--read_pairs false \
		-profile docker \
		--max_cpus 32 \
		-resume


