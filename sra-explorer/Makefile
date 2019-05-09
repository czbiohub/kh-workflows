DIR=/mnt/ibm_lg/olga/sra-explorer
DIR2=/mnt/data/fastq

choanoflagellates:
	cd ${DIR}/choanoflagellates ; parallel --jobs 16 < /home/olga/code/kh-workflows/sra-explorer/choanoflagellates.sh

merkin2012:
	mkdir -p ${DIR}/merkin2012; cd ${DIR}/merkin2012 ; parallel --jobs 16 < /home/olga/code/kh-workflows/sra-explorer/merkin2012.sh


mosquito_blood:
	mkdir -p ${DIR2}/mosquito_blood; cd ${DIR2}/mosquito_blood ; parallel --jobs 16 < mosquito_blood.sh
