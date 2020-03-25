DIR=/mnt/ibm_lg/olga/sra-explorer

choanoflagellates:
	cd ${DIR}/choanoflagellates ; parallel --jobs 16 < /home/olga/code/kh-workflows/sra-explorer/choanoflagellates.sh

merkin2012:
	mkdir -p ${DIR}/merkin2012; cd ${DIR}/merkin2012 ; parallel --jobs 16 < /home/olga/code/kh-workflows/sra-explorer/merkin2012.sh


golumbeanu2018:
	mkdir -p ${DIR}/$@; cd ${DIR}/$@ ; parallel --jobs 16 < /home/olga/code/kh-workflows--olgabot/hiv-k2g/sra-explorer/$@.sh
