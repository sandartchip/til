

# NGS 데이터
-  현재 NCBI, EBI, DDBJ의 Sequence 데이터 저장 서비스인 SRA(Sequence Read Archieve)에서 공개된 NGS 데이터를 받을 수 있다. 


### Reference Assembly 
- 원본 사진을 보고 퍼즐을 맞추는 것. 말 그대로 reference가 되는 원본 서열에 read들을 mapping 시켜 만들어지는 consensus 서열을 얻는 것. 
- ex) 한우의 유전체를 시퀀싱하여 얻어낸 read 데이터를 NCBI에 공개된 소의 reference 서열에 mapping 시켜서 한우의 유전체와 어떠한 차이가 있는지 비교하는 분석을 수행 가능. 



## 종류
-  Roche 454 장비에서 만들어진 Long read 데이터와 Illumina 장비에서 만들어진 Paired End Read데이터가 있다.



##  Single End Sequencing
- 시퀀싱 기계가 서열의 조각을 오직 한 쪽 끝에서부터 읽어서 염기쌍 서열을 생성한다.


## paired-end squencing
- Paired end Sequencing의 결과로, 두 개의 FASTQ 파일을 얻을 수 있다. (예를 들어, SRS1234_1.fastq와 SRS1234_2.fastq) 각각이 forward와 reverse read를 나타낸다. 
- sequence를 확인해 보면 모두 5' -> 3' 으로 되어 있는 것을 확인할 수 있다. 즉 두 reads를 합칠 때는 reverse reads를 reverse compliment 시킨 후 overlap 되는 부분을 합치면 된다. 또한 각각의 read 앞쪽에 primer가 붙어 있을 수도 있다. 

- 우선 한쪽 끝에서 특정 길이까지 읽고, 그다음 다른 쪽 끝에서 서열을 읽는다. Paired-end sequencing은 유전체 상에서 다양한 read들의 상대적인 위치를 찾는데 더 용이하다.
- 원본 없이 하나하나 맞춰 보면서 연결되는 것 끼리 쭉 잇는다. 이어서 원래의 genome 서열을 알아내야 한다. 따라서 한 종류의 read들만 가지고 assemble을 하기란 쉽지 않다. 그래서, short, long, paired-end, mate-paired-end 등 여러 종류의 read들을 가지고 assembly를 해야 결과가 좋아진다. 
- repetitive한 지역의 assembly를 향상시킬 수 있다. 그러나 Paired end는 Single End보다 더 비싸고, 더 많은 시간이 소요된다. 또한 모든 실험이 높은 수준의 정확도를 필요로 하지 않을 수도 있다. 
- 유전체 재배열, 반복 서열, 유전자 융합, 새로운 전사물 발견에 용이하다. 같은 시간과 노력으로 두 배의 read 수를 생성할 수 있을 뿐만 아니라, read pairs로 정렬된 서열들로 더 정확한 alignment를 할 수 있고, single-end 데이터로는 불가능한 insertion-deletion variant도 찾을 수 있다.
- DNA 또는 RNA를 양쪽 끝에서 시퀀싱(sequencing machine이 양쪽 끝에서부터 읽어 나가게 되고, 두 reads는 5/ 3으로 읽힌다.) 하는 방법을 말한다. paired-end sequencing은 게놈 재배열 및 반복적인 서열, 유전자 융합, 새로운 전사체의 발견에 용이하다. 또한 single-end sequencing으로 불가능한 insertion/deletion 변이도 검출할 수 있다.
- Illumina에서는 약 500bps 길이의 페어드 엔드 리드를 제공하는데, 페어드 엔드 리드의 길이는 달라질 수 있으므로 오차율을 설정해 줄 필요가 있다. 
- 한 페어드 엔드의 오차율을 100bps로 설정하였다면, 한 페어드 엔드의 길이는 400~600bps 정도이다. 전체 염기 서열에서 임의의 영역을 선택한 후 그곳에서부터 연속된 400 ~ 600bps 영역을 추출하고, 추출된 영역에서의 양 끝의 75bps를 잘라내어 페어드 엔드 리드를 생성한다. 이러한 과정으로 생성된 리드 길이의 합이 전체 염기서열의 n배가 될 때까지 반복한다. 이러한 n을 커버리지(coverage)라 하고, 생성된 리드들을 테스트 쿼리라고 한다. 커버리지가 높아질 수록 보다 정확한 정보를 얻을 수 있으나 비용이 많이 소요된다.


## Sequence Read Length 
- Read Length: 시퀀싱을 할 때 read의 염기쌍(base pair, bp) 수를 결정할 수 있다. 
- 예를 들어 하나의 read를 50bp로 할 수 있고, 100bp로 할 수 있고, 그 이상으로도 할 수 있다. 더 긴 read들은 특정 염기쌍의 상대적인 위치에 대한 더 정확한 정보를 제공해준다. 그러나 긴 read를 생선하는 데는 더 많은 비용이 든다. 


## Strand Specific
- Strand-specific은 양 말단의 adapter sequence를 다르게 붙임으로써 reads의 앞뒤를 구분해주는 방식. 

- Single-end, Paired-end와 Stranded, Unstranded는 별개의 개념이라는 것을 알아야 한다. Single-end이더라도 Stranded일 수도 있고 Unstranded일 수도 있으며 Paired-end도 마찬가지이다

## Depth of coverage 
- depth of coverage는 시퀀싱 중 유전체의 특정 위치가 시퀀싱되는 횟수를 나타낸다. 예를 들어 Exome sequencing을 하는데 목표 coverage를 60X라고 한다면, 그 뜻은 목표로 하는 각 염기들이 평균적으로 60번 정도 시퀀싱된다는 것이다. 



#### 참고자료 
https://bgreat.tistory.com/100
https://www.insilicogen.com/blog/106
https://brunch.co.kr/@davidseo97/13
