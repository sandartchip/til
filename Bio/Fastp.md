

We developed fastp as an ultra-fast FASTQ preprocessor with useful quality control and data-filtering features. \
It can perform quality control, adapter trimming, quality filtering, per-read quality pruning and many other operations with a single scan of the FASTQ data. 
This tool is developed in C++ and has multi-threading support. 
Based on our evaluation, fastp is 2–5 times faster than other FASTQ preprocessing tools such as Trimmomatic or Cutadapt despite performing far more operations than similar tools.

# Motivation 
- FASTQ 파일의 품질 관리 및 전처리는 다운스트림 분석을 위한 깨끗한 데이터를 제공하는 데 필수적입니다. 
- 전통적으로 품질 관리, 어댑터 트리밍 및 품질 필터링과 같은 각 작업에 서로 다른 도구가 사용되었습니다. 
- 이러한 도구는 대부분이 고급 프로그래밍 언어(예: Python 및 Java)를 사용하여 개발되고 제한된 다중 스레딩 지원을 제공하기 때문에 충분하지 않은 경우가 많습니다. 
- 데이터를 여러 번 읽고 로드하면 전처리 속도가 느려지고 I/O가 비효율적입니다.

# RESULT 
- 우리는 유용한 품질 관리 및 데이터 필터링 기능을 갖춘 초고속 FASTQ 전처리기로 fastp를 개발했습니다. 
- FASTQ 데이터를 한 번 스캔하여 품질 관리, 어댑터 트리밍, 품질 필터링, 읽기별 품질 정리 및 기타 여러 작업을 수행할 수 있습니다. 
- 이 도구는 C++로 개발되었으며 다중 스레딩을 지원합니다. 
- 우리의 평가에 따르면 fastp는 유사한 도구보다 훨씬 더 많은 작업을 수행함에도 불구하고 Trimmomatic 또는 Cutadapt와 같은 다른 FASTQ 전처리 도구보다 2-5배 빠릅니다.


