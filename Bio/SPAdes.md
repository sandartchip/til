
- De novo assembly 툴.

다양한 환경에서 가장 많이 차지하는 박테리아는 실험실에서 복제할 수 없으므로 기존 기술을 사용하여 시퀀싱할 수 없다. 
단일 세포 유전체학의 주요 목표는 미경양 유기체의 전체 게놈 어셈블리로 유전자 중심 메타게놈 데이터를 보완하는 것이다. 
단일 셀 데이터의 조립은 읽기 범위가 매우 균일하지 않고 시퀀싱 오류 및 키메라 읽기 수준이 높기 때문에 어렵습니다. 
우리는 단일 셀 및 표준(다중 셀) 어셈블리 모두를 위한 새로운 어셈블러인 SPAdes를 설명하고 최근 출시된 E+V-SC 어셈블러(단일 셀 데이터에 특화됨)와 인기 있는 어셈블러 Velvet 및 SoapDeNovo( 다중 셀 데이터의 경우). SPAdes는 단일 세포 어셈블리를 생성하여 기존의 메타유전체학 연구를 통해 얻을 수 있는 것보다 훨씬 더 많이 배양할 수 없는 박테리아의 게놈에 대한 정보를 제공합니다. 
SPAdes는 온라인에서 사용할 수 있습니다( http://bioinf.spbau.ru/spades ). 오픈 소스 소프트웨어로 배포됩니다.


## SPAdes output
SPAdes stores all output files in <output_dir> , which is set by the user.

- <output_dir>/corrected/ directory contains reads corrected by BayesHammer in *.fastq.gz files; if compression is disabled, reads are stored in uncompressed *.fastq files
- <output_dir>/scaffolds.fasta contains resulting scaffolds (recommended for use as resulting sequences)
- <output_dir>/contigs.fasta contains resulting contigs
- <output_dir>/assembly_graph_with_scaffolds.gfa contains SPAdes assembly graph and scaffolds paths in GFA 1.0 format
- <output_dir>/assembly_graph.fastg contains SPAdes assembly graph in FASTG format
- <output_dir>/contigs.paths contains paths in the assembly graph corresponding to contigs.fasta (see details below)
- <output_dir>/scaffolds.paths contains paths in the assembly graph corresponding to scaffolds.fasta (see details below)

http://bioip.co.kr/Analysis/56

