DIR=/mnt/ibm_lg/olga/sra-explorer

choanoflagellates:
	cd ${DIR}/choanoflagellates ; parallel --jobs 16 < /home/olga/code/kh-workflows/sra-explorer/choanoflagellates.sh

merkin2012:
	mkdir -p ${DIR}/merkin2012; cd ${DIR}/merkin2012 ; parallel --jobs 16 < /home/olga/code/kh-workflows/sra-explorer/merkin2012.sh


brawand2011:
	mkdir -p ${DIR}/brawand2011; cd ${DIR}/brawand2011 ; parallel --jobs 16 < /home/olga/code/kmer-hashing/kh-workflows/sra-explorer/brawand2011.sh
